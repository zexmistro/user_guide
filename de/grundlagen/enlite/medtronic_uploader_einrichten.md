# Medtronic Uploader einrichten

Bevor die Medtronic Uploader App auf dem Android Smartphone konfiguriert werden kann, muss man die Schritte des Kapitels [Nightscout einrichten](../../nightscout/nightscout_einrichten.md), außer denen des Unterkapitels "Care Portal", vollzogen haben.

Nun installiert man die Datei "NightScout.apk" auf dem Smartphone. Eventuell muss man dazu unter Einstellungen - Sicherheit - Unbekannte Herkunft die Installation von Apps aus unbekannten Quellen zulassen, da diese App nicht aus dem Google Play Store stammt. Dort gibt es nur den für den Dexcom Empfänger gedachten "Nightscout Uploader".

Die Account-Informationen, die man auf dem Arbeitsblatt aus Kapitel dem "Account-Information". eingetragen hat, werden nun zum Konfigurieren der Medtronic Uploader App benötigt.

Zuerst muss die Medtronic Uploader App geschlossen werden, falls diese bereits läuft. Nun den MMCommander über das USB OTG Kabel an das Smartphone anschließen. Es sollte sich automatisch ein Fenster öffnen, welches fragt, was getan werden soll. Dort die Nightscout App auswählen und diese sollte danach automatisch starten.

Wenn jetzt der Uploader läuft, klickt man rechts oben auf die drei Punkte oder, abhängig vom jeweiligen Android Smartphone, man benutzt die Einstellungstaste des Gerätes. Es öffnet sich ein Menü, und dort wählt man den Punkt "Preferences". Hier werden folgende Einstellungen vorgenommen:

![Einstellungen](../../images/enlite/settings.jpg)
* 
mmol/L -> hier kann man wählen, ob man lieber mit mmol/l oder mg/dl arbeitet.
* 
Type -> "Medtronic CGM" auswählen.
* 
Pump ID -> die ID von der Pumpenrückseite eintragen. Dies sind die sechs Ziffern, die auf dem folgenden Bild im Bereich des roten Rechteckes liegen.

![Pumpe](../../images/enlite/pumpe.jpg)
* 
Glucometer ID -> die ID des Blutzuckermessgerätes eintragen (rotes Rechteck).

![Messgerät](../../images/enlite/messgeraet.jpg)
* 
Sensor ID -> die ID von der Rückseite des Minimed Transmitters eintragen (rotes Rechteck).

![Transmitter](../../images/enlite/transmitter.jpg)
* 
Calibration Type -> "Manual" auswählen.
* 
Glucose Value Source -> "Medtronic Sensor" auswählen.
* 
API Upload (REST) -> aktivieren
* 
API Base URL -> ```APISECRET```@https:// ```WEBSEITENNAME```.azurewebsites.net/api/v1 eintragen. Sowohl das "APISECRET", als auch den "Webseitennamen" findet man auf der letzten Seite des Arbeitsblattes aus Kapitel 2.1. - vorausgesetzt man hat das Arbeitsblatt ausgefüllt. Mit den Beispielen aus Kapitel 2.5. [Azure](../../nightscout/azure.md) ergäbe sich dann: Y3KmrdFA12jmk@https://nscgm01.azurewebsites.net/api/v1.
* 
MongoDB Upload -> deaktivieren
* 
MongoDB REST Upload -> deaktivieren
* 
Wifi Hack -> deaktivieren
* 
2 Days at Startup -> aktivieren
* 
I UNDERSTAND -> Hier steht ganz klar, dass Nightscout nicht genutzt werden darf, um medizinische Entscheidungen zu fällen. Es gibt weder Unterstützung noch irgendwelche Garantien. Die Qualität und Leistung dieses Projektes hängt einzig von Dir ab. Dieses Projekt wurde von Freiwilligen erstellt und weiterentwickelt. Dies muss man akzeptieren. -> aktivieren
* 
Logging Level -> Error

Nun geht man raus aus den Einstellungen. Man sollte Striche sehen, einen grünen Text "CGM Service Started" und einen weiteren Text "Uncalibrated".

Jedes Mal, wenn der Uploader Daten vom Sensor empfängt, erscheint folgender Text im unteren Teil des Bildschirms: "Medtronic CGM Message: sensor data value received". Sobald man den ersten Wert empfangen hat, klickt man wieder rechts oben auf die drei Punkte. Diesmal wählt man "Instant Calibration" und gibt den Wert ein, den man gerade auf der Pumpe abliest. Anschließend sollte der Uploader alle 5 Minuten einen Wert empfangen und diesen in die Mongo Datenbank hochladen.

![Upload](../../images/enlite/upload.jpg)

Damit wäre der Medtronic Uploader eingerichtet. Es dauert nun noch etwa eine Viertelstunde, bis die ersten Werte über die persönliche Internetseite im Netz abrufbar sind. Ansonsten empfiehlt sich ein Blick in das Unterkapitel [Fehlerbehebung](fehlerbehebung.md).

Man sollte die Kalibrierung mittels "Instant Calibration" jedes Mal durchführen, wenn der MMCommander erneut mit dem Smartphone verbunden wird.




