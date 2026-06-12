---
title: "Stinkin' RhythmBox"
date: 2007-09-28
forum: General Help
---

### Post by blithen on 2007-09-28
I don't use RhythmBox, and I don't want to. But that's not the point. The update is saying it needs to update Rhythmbox, Okay? I don't have it installed but it says it does. Anyway to fix this? I can't do a re-installation. I've been having this problem for the longest time... here is the error code

```
blithen@Sparky:~$ sudo apt-get install rhythmbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libtotem-plparser1
Use 'apt-get autoremove' to remove them.
Recommended packages:
  python-louie
The following packages will be upgraded:
  rhythmbox
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/3322kB of archives.
After unpacking 483kB of additional disk space will be used.
(Reading database ... 164925 files and directories currently installed.)
Preparing to replace rhythmbox 0.10.0-0ubuntu2 (using .../rhythmbox_0.11.2-0ubuntu3_i386.deb) ...
Warning: /usr/share/gconf/schemas/rhythmbox.schemas could not be found.
Usage: gconf-schemas --[un]register file1.schemas [file2.schemas [...]]

gconf-schemas: error: You need to give at least a file to (un)register.
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
WARNING: /usr/share/python-support/rhythmbox.dirs does not exist.
         Some bytecompiled files may be left behind.
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 227, in <module>
    args.remove(arg)
ValueError: list.remove(x): x not in list
dpkg: error processing /var/cache/apt/archives/rhythmbox_0.11.2-0ubuntu3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/rhythmbox_0.11.2-0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
blithen@Sparky:~$ 

```

---

### Post by blithen on 2007-09-29
Bumpage!

---

### Post by FuturePilot on 2007-09-29
If it wants to upgrade it, it's got to be installed. If you're using Gnome it's part of the Gnome desktop. Unless you uninstalled it yourself.

---

### Post by blithen on 2007-09-29
> **FuturePilot said:**
> If it wants to upgrade it, it's got to be installed. If you're using Gnome it's part of the Gnome desktop. Unless you uninstalled it yourself.

Yeah but it's not installed. But it says it is.
Like if I go to Application>Sound & video, then it shows rhythm box.
But If I try to install it, it comes up with the above errors.

---

### Post by FuturePilot on 2007-09-29
It looks like it can't find the schema file. Maybe if you try to register it, it might find it.
```
cd /usr/share/gconf/schemas
sudo gconf-schemas --register *.schemas
```

---

### Post by blithen on 2007-09-29
> **FuturePilot said:**
> It looks like it can't find the schema file. Maybe if you try to register it, it might find it.
```
cd /usr/share/gconf/schemas
sudo gconf-schemas --register *.schemas
```

Dang, nope it gave me this

```
blithen@Sparky:~$ cd /usr/share/gconf/schemas
blithen@Sparky:/usr/share/gconf/schemas$ sudo gconf-schemas --register *.schemas
You must have at least one <locale> entry in a <schema>
You must have at least one <locale> entry in a <schema>
```
Then still had the same error as before when trying to install

---

### Post by FuturePilot on 2007-09-29
I wonder if deleting the deb from /var/cache/apt/archives then try reinstalling it again would do anything.

---

### Post by blithen on 2007-09-29
Did. Twice actually xD
I have no idea.
It's not hindering me of anything, just kind of annoying. So it's not the OMFG BIG DEAL if it doesn't get fixed. Just was wondering if there is way.

---

### Post by FuturePilot on 2007-09-29
Lol, yeah I know how that is. Maybe it's just Gutsy being gutsy? lol

---

### Post by blithen on 2007-09-30
> **FuturePilot said:**
> Lol, yeah I know how that is. Maybe it's just Gutsy being gutsy? lol
Nah that can't be actually. I've had this problem since fiesty. : P
But meh. $#!@ happens.

---

### Post by Golyadkin on 2007-09-30
How about purging it with sudo apt-get remove --purge rhythmbox?

---

### Post by proog on 2007-10-02
I had the same problem after the upgrade to gutsy beta and not just for rhythmbox, but for the dia-common package too.
```
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Reading state information... Fertig
Empfohlene Pakete:
  dia dia-gnome dia-libs
Die folgenden Pakete werden aktualisiert:
  dia-common
1 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
Es müssen noch 0B von 2392kB Archiven geholt werden.
Nach dem Auspacken werden 32,8kB Plattenplatz zusätzlich benutzt.
(Lese Datenbank ... 204202 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereiten zum Ersetzen von dia-common 0.96.1-0ubuntu1 (durch .../dia-common_0.96.1-3_all.deb) ...
Ignoring nonregistered document dia-manual
WARNING: /usr/share/python-support/dia-common.dirs does not exist.
         Some bytecompiled files may be left behind.
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 227, in <module>
    args.remove(arg)
ValueError: list.remove(x): x not in list
dpkg: Warnung - altes pre-removal-Skript wurde mit Fehler-Status 1 beendet
dpkg - probiere stattdessen Skript aus dem neuen Paket ...
WARNING: /usr/share/python-support/dia-common.dirs does not exist.
         Some bytecompiled files may be left behind.
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 227, in <module>
    args.remove(arg)
ValueError: list.remove(x): x not in list
dpkg: Fehler beim Bearbeiten von /var/cache/apt/archives/dia-common_0.96.1-3_all.deb (--unpack):
 Unterprozess neues pre-removal-Skript gab den Fehlerwert 1 zurück
Fehler traten auf beim Bearbeiten von:
 /var/cache/apt/archives/dia-common_0.96.1-3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I solved the problem by simply downloading the packages manually from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
unpacking them with file roller and copying the missing files in the directories missing them:
>sudo cp rhythmbox.schemas /usr/share/gconf/schemas/
>sudo cp rhythmbox.dirs /usr/share/python-support/

---

