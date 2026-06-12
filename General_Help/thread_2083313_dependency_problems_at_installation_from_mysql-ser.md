---
title: "dependency problems at installation from mysql-server-5.5"
date: 2012-11-12
forum: General Help
---

### Post by PrinzLangweilig on 2012-11-12
[PHP]
qcons@014-QCONS:/var/lib$ sudo apt-get install -f mysql-server
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Statusinformationen werden eingelesen... Fertig
mysql-server ist schon die neueste Version.
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
2 nicht vollständig installiert oder entfernt.
Nach dieser Operation werden 0 B Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren [J/n]? j
mysql-server-5.5 (5.5.28-0ubuntu0.12.04.2) wird eingerichtet ...
121112 11:16:52 [Note] Plugin 'FEDERATED' is disabled.
121112 11:16:52 InnoDB: The InnoDB memory heap is disabled
121112 11:16:52 InnoDB: Mutexes and rw_locks use GCC atomic builtins
121112 11:16:52 InnoDB: Compressed tables use zlib 1.2.3.4
121112 11:16:52 InnoDB: Initializing buffer pool, size = 128.0M
121112 11:16:52 InnoDB: Completed initialization of buffer pool
121112 11:16:52 InnoDB: highest supported file format is Barracuda.
121112 11:16:53  InnoDB: Waiting for the background threads to start
121112 11:16:54 InnoDB: 1.1.8 started; log sequence number 1595675
121112 11:16:54  InnoDB: Starting shutdown...
121112 11:16:54  InnoDB: Shutdown completed; log sequence number 1595675
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: Fehler beim Bearbeiten von mysql-server-5.5 (--configure):
 Unterprozess installiertes post-installation-Skript gab den Fehlerwert 1 zurück
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von mysql-server:
 mysql-server hängt ab von mysql-server-5.5; aber:
  Paket mysql-server-5.5 ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von mysql-server (--configure):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert
Es wurde kein Apport-Bericht verfasst, da die Fehlermeldung darauf hindeutet, dass dies lediglich ein Folgefehler eines vorherigen Problems ist.
                                                                Fehler traten auf beim Bearbeiten von:
 mysql-server-5.5
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/PHP]

---

