---
title: "Cannot install File-Roller"
date: 2004-11-23
forum: General Help
---

### Post by novaburst on 2004-11-23
I am having trouble installing File-Roller. It seems to be the only thing giving me any trouble.
I tried it from Synaptic and the command line using Sudo. Any help would be appreciated. It gives me the following error:


(Reading database ... 61678 files and directories currently installed.)
Unpacking file-roller (from .../file-roller_2.8.2-0ubuntu1_i386.deb) ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/file-roller_2.8.2-0ubuntu1_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/gnome/help/file-roller/sv/file-roller.xml')
Errors were encountered while processing:
 /var/cache/apt/archives/file-roller_2.8.2-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by novaburst on 2004-11-24
Does anyone have any ideas on how I could start troubleshooting this?

---

### Post by p!=f on 2004-11-24
You could try:
1) sudo apt-get -f install
2) purging the file-roller package and then install it again (sudo apt-get --purge remove file-roller && sudo apt-get install file-roller gnome-desktop-environment)
3) check if you have a free space on the HDD
4) check if you don't have a bad RAM using memtest86+

---

### Post by novaburst on 2004-11-24
Thanks for the reply. I tried all but the last one. Heck, it might just be easier to reinstall, since I really haven't tweaked anything yet.

---

