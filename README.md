# HV-Trainer Update (Generic)

OTA-Update-Quelle für die **Generic-Variante** des HV-Trainers
(`applicationId` = `com.csm.hvtrainer`, Branch `generic` in `hv-trainer-layout`).

Das Repo muss **öffentlich** bleiben: Die App ruft `latest.json` über
`raw.githubusercontent.com` ohne Authentifizierung ab.

> Nicht mit `phexerus/hv-trainer-update` verwechseln — das ist die BMW-Variante
> (`com.example.hv_trainer_layout`, Branch `bmw`). Die beiden Varianten dürfen
> sich nie gegenseitig aktualisieren.

## Neue Version veröffentlichen

1. Auf Branch `generic` `versionCode` und `versionName` in `app/build.gradle.kts` erhöhen.
2. `./gradlew assembleRelease`
3. `app/build/outputs/apk/release/app-release.apk` hierher als `hvtrainer-latest.apk` kopieren.
4. `versionCode` und `versionName` in `latest.json` auf die neuen Werte setzen.
5. Beide Dateien im selben Commit pushen.

Schritt 4 und 5 gehören zusammen: Zeigt `latest.json` auf eine Version, die das
APK nicht hat, laufen die Tablets in eine Update-Schleife.
