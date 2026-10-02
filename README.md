# DoorGuard — Phase 1 (GitHub / Mobile Friendly)

DoorGuard is an Android Smart Door Video Intercom project. Phase 1 contains the base Android/Compose project and a GitHub Actions workflow so the project can be built in the cloud without Android Studio.

## Current Phase

Phase 1 only verifies the Android project setup. Door/Home roles, pairing, WebRTC, signaling, notifications, and other features will be added in later phases.

## Technology

- Kotlin 2.0.21
- Android Gradle Plugin 8.7.2
- Jetpack Compose + Material 3
- Compile SDK 35
- Minimum Android SDK 26
- JDK 17
- Gradle 8.9

## Build without Android Studio

This repository includes `.github/workflows/android-build.yml`.

After uploading the project to GitHub:

1. Open the repository on GitHub.
2. Go to **Actions**.
3. Select **Android Build**.
4. Press **Run workflow** (or push a commit to `main`/`master`).
5. Wait for the build to finish.
6. Open the successful workflow run.
7. Under **Artifacts**, download `DoorGuard-debug-apk`.
8. Extract the downloaded artifact and install the APK on an Android phone.

No Android Studio is required for this build path.

## GitHub mobile upload

Upload the contents of this project to a GitHub repository. Keep the folder structure exactly as provided, especially:

```text
.github/workflows/android-build.yml
app/
gradle/
build.gradle.kts
settings.gradle.kts
gradle.properties
```

If GitHub's mobile interface makes uploading many files inconvenient, create the repository first and upload the ZIP contents from a browser/desktop GitHub interface when available. Do not upload the ZIP as the only repository file: GitHub Actions needs the project files extracted in the repository.

## Phase 1 test

Expected result after installation:

- The app launches.
- `DoorGuard` is displayed.
- The project builds successfully in GitHub Actions.

## Security notes

- `app/google-services.json` is ignored and is not included.
- No Firebase configuration is required in Phase 1.
- No TURN credentials are included.
- No API keys or passwords are hardcoded.
- `android:allowBackup="false"` is enabled.

## Planned architecture

```text
presentation/
domain/
data/
network/
webrtc/
pairing/
security/
settings/
notifications/
ui/theme/
```

The Phase 1 project keeps the dependency surface small. Later phases will add only the components that are actually needed.

## Planned development order

1. Phase 1 — Project setup ✅
2. Phase 2 — Door/Home role selection
3. Phase 3 — Local pairing / QR / 6-digit code
4. Phase 4 — Signaling
5. Phase 5 — WebRTC video
6. Phase 6 — Two-way audio
7. Phase 7 — Notifications
8. Phase 8 — Reconnect and background operation
9. Phase 9 — Security hardening
10. Phase 10 — Testing and release build

## Important product goal

The first usable version should prioritize a free/local-network workflow. Paid cloud services are not required for Phase 1. Before introducing Firebase, TURN, or another paid service, we will evaluate free or low-cost alternatives.
