# Online R mit Binder [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/reschreiter/rbinder/HEAD?urlpath=rstudio)

Zum Beispiel: <https://github.com/ModelOriented/shapper/> is launched via [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/ModelOriented/shapper/master?filepath=binder%2Fshapper.ipynb)


Um ein **R** Umgebung mit [Binder](https://mybinder.org) zu erstellen ist eine `DESCRIPTION` Datei im `root/` Verzeichnis der einfachste Weg. 

`DESCRIPTION`
```
Package: MeinProjektName
Title: Analyse fuer Binder
Version: 0.0.1
Depends:
    R (>= 4.0)
Imports:
    quanteda,
    ggplot2,
    dplyr
```

Die wichtigsten Punkte dabei:

   1. `Imports`: Alle R-Pakete auf (kommagetrennt), die Binder automatisch vorinstallieren soll (z. B. `quanteda`).
   2. Formatierung: Die Zeilen unter `Imports`: müssen eingerückt sein.
   3. Zusatz-Tipp (`runtime.txt`): Damit die Installation stabil läuft, empfiehlt es sich, zusätzlich eine Datei namens `runtime.txt`
      mit nur einer Zeile zu erstellen, z. B.: `r-2023-12-01`. Das sagt Binder: "Nutze den Software-Stand vom 1. Dezember 2023".

Verwende <https://mybinder.org> zum Aufbau des Links: <https://mybinder.org/v2/gh/reschreiter/RBinder/HEAD?urlpath=rstudio> and its  
Badge is: [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/reschreiter/rbinder/HEAD?urlpath=rstudio)

## Eine bestimmten R-Version

Da **R** Version 4.6.0 ("Because it was There") am 24. April 2026 veröffentlicht wurde, 
musst für die `runtime.txt` ein Datum wählen, das an oder kurz nach diesem Veröffentlichungsdatum liegt.

Datei `runtime.txt` im Hauptverzeichnis deines Repositories mit Inhalt:
```
r-4.6-2026-04-24
```
Das Schema lautet r-<Version>-<Datum>. Das Datum 2026-04-24 fungiert als Snapshot-Datum für den Paketmanager (Posit Package Manager).
Binder nutzt diesen Snapshot, um sicherzustellen, dass die installierten R-Pakete mit der gewählten R-Version kompatibel sind.
Durch diese Zeile installiert MyBinder automatisch R 4.6.0 und konfiguriert die Umgebung so, dass RStudio über den URL-Pfad gestartet werden kann. 

Stelle sicher, dass deine `DESCRIPTION`-Datei (falls vorhanden) mindestens R (>= 4.6) unter Depends voraussetzt, um Konflikte zu vermeiden.


## Online Binder Umgebungen

Damit MyBinder eine R-Umgebung mit RStudio erstellt, werden normalerweise folgende Dateien benötigt (die typischerweise im Folder `binder/` liegen):

* `binder/runtime.txt`: Diese Datei ist zwingend erforderlich, um MyBinder mitzuteilen, dass R verwendet werden soll. Sie muss eine Zeile im Format `r-YYYY-MM-DD` enthalten (z. B. `r-2023-10-01`), die auf einen Snapshot des CRAN-Archivs verweist.
* `binder/install.R`: In dieser Datei listen Sie alle zusätzlichen R-Pakete auf, die vorinstalliert werden sollen (z. B. `install.packages("quanteda")`).
* `binder/apt.txt (Optional): Falls bestimmte R-Pakete Systembibliotheken von Linux benötigen, müssen diese hier aufgelistet werden.

Alternativ können diese Dateien auch im Root Folger liegen anstelle von `binder/`. Diese Dateien haben Vorrang gegenüber der `DESCRIPTION` Datei.
