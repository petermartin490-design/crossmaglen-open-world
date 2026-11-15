# Crossmaglen: Open World — prototype v0.1

A playable, mobile-friendly top-down driving/action prototype inspired by the classic 1990s overhead open-world games. It currently uses a hand-built fictionalised Crossmaglen-inspired layout (town centre, radial roads and countryside lanes), not a surveyed 1:1 street map. The supplied Google Maps link identifies Crossmaglen, but Google Maps imagery/data is not bundled or copied.

## Play immediately

Open `www/index.html` in a modern browser, or run:

```bash
npm install
npm start
```

Then open the local address shown by `serve` on your phone or computer.

## Android APK packaging

Requirements: Node.js 20+, Android Studio, Android SDK and a JDK supported by your installed Android Gradle Plugin.

```bash
npm install
npx cap add android
npx cap sync android
npx cap open android
```

In Android Studio, wait for Gradle sync, then choose **Build > Build Bundle(s) / APK(s) > Build APK(s)**. The debug APK is normally created under `android/app/build/outputs/apk/debug/`. For a distributable release, configure a signing key and build a signed APK/AAB in Android Studio.

## Controls

- Touch: left virtual stick to walk / steer; RUN to accelerate; ENTER/EXIT to use nearby cars.
- Keyboard (desktop): WASD or arrow keys; Shift to run / accelerate; E is not currently mapped (use the on-screen ENTER button).
- Reach the yellow marker at each named landmark to complete a delivery-style objective and earn £100.

## Prototype systems

- Walking player and camera follow
- Enterable cars, steering, acceleration and exit
- Ambient traffic and pedestrians
- Police pursuit, wanted stars and fines
- Cash and repeatable location missions
- On-screen mobile controls and minimap

## Known prototype limitations

- The road layout is an approximation for gameplay, not exact cartography. For a faithful map, add licensed OpenStreetMap vector data for the desired town/countryside boundary and convert it into game roads/buildings. Do not scrape or redistribute Google Maps tiles.
- No save system, sound, mission dialogue, collision/pathfinding, traffic lights, or final art/audio yet.
- Police and NPC behaviour is deliberately simple placeholder AI.

## One-click cloud APK build (GitHub Actions)

This project includes `.github/workflows/android-apk.yml`. To build an APK without installing Android Studio on your own computer:

1. Create a GitHub repository and upload the contents of this project folder.
2. Open the repository's **Actions** tab and select **Build Crossmaglen Android APK**.
3. Choose **Run workflow** (or let the workflow run after pushing to `main`).
4. When the run finishes successfully, open it and download the `crossmaglen-open-world-debug-apk` artifact.
5. Extract the artifact ZIP and install `app-debug.apk` on your Android phone. You may need to allow installation from that source.

This produces a debug APK for testing, not a Play Store-signed release. A release build needs a signing key and secure signing configuration.
