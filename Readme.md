AvNav More NMEA plugin
======================

*** diese plugin ist nicht aktuell ***
Aktuelle Version im [repo des Autors](https://github.com/kdschmidt1/avnav-more-nmea-plugin).


Ein plugin für [AvNav](https://www.wellenvogel.net/software/avnav/docs/beschreibung.html), das zusätzliche NMEA Daten dekodiert und berechnet.

Autor: [kdschmidt1](https://github.com/kdschmidt1)

Das Plugin berechnet
--------------------

AWD (Scheinbare Windrichtung) -> "gps.AWD"
TWD (Wahre Windrichtung) -> "gps.TWD"
TWS (Wahre Windgeschwindigkeit in m/s) -> "gps.TWS"
TWA (Wahren Windwinkel) -> "gps.TWA"

falls avnav relative Winddaten ("gps.windReference"=="R", Windrichtung "gps.windAngle" und Windgeschwindigkeit "gps.WindSpeed") bereitstellt.
Bei wahren Winddaten ("gps.windReference"=="T") erfolgt keine Berechnung der Winddaten !

Zusätzlich erfolgt die Ausgabe von:

HDGm (Magnetischer Kurs) -> "gps.HDGm"
HDGt (Rechtweisender Kurs) -> "gps.HDGt"
HDGt (Geschwindigkeit durch das Wasser) -> "gps.STW"
MagVar (Missweisung basierend auf dem World Magnetic Model 2020 der NOAA (https://www.ngdc.noaa.gov/geomag/WMM/soft.shtml#downloads)

Anmerkungen:
STW (Speed through Water) wird $VHW entnommen.
Achtung bei NMEA200 Quellen:

Das Signalk-Plugin "sk-to-nmea0183" sendet diese Message nur, wenn gleichzeitig Heading und magnetic-Variation Daten in Signalk verfügbar sind.
canboat dagegen sendet $VHW auch ohne Heading!
HDGt (Heading True) wird aus HDGm (Heading magnetic aus $HDM oder $HDG oder $VHW) unter Berücksichtigung der Missweisung berechnet falls keine True Heading Signale empfangen werden.
Empfangene True-Heading Signale überschreiben die berechneten Werte!
Wird eine Missweisung von den Sensoren empfangen ($VHW oder $HDG) so überschreibt diese die berechnete Missweisung!