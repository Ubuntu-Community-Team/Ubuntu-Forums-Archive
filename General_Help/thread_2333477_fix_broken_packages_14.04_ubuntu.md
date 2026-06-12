---
title: "fix broken packages 14.04 ubuntu"
date: 2016-08-10
forum: General Help
---

### Post by t-ani on 2016-08-10
[COLOR=#111111][FONT=Ubuntu]I tried to reinstall Pulse Audio (crashed always) but after uninstall I can't reinstall. I tried to fix broken packages with these steps:[/FONT][/COLOR]
sudo apt-get update
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get check
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo rm -i /var/lib/dpkg/lock
sudo rm -i /var/cache/apt/archives/lock
[COLOR=#111111][FONT=Ubuntu]Nothing works. After sudo apt-get -f install I got the message[/FONT][/COLOR]
    dpkg: error processing packages: pulseaudio-module-bluetooth (--remove):
    can't remove safely: „/usr/lib/pulse-4.0/modules/libbluetooth-util.so”: No directory
    Error processing pulseaudio-module-bluetooth
    E: Sub-process /usr/bin/dpkg returned an error code (1)
[COLOR=#111111][FONT=Ubuntu]Any idea?[/FONT][/COLOR]

---

### Post by t-ani on 2016-08-11
[COLOR=#111111][FONT=Ubuntu]Solved. I deleted manually the file /usr/lib/pulse-4.0/modules/libbluetooth-util.so, and all of the previous commands work.[/FONT][/COLOR]

---

### Post by mörgæs on 2016-08-11
Good, please mark the thread 'solved' using Thread Tools.

---

