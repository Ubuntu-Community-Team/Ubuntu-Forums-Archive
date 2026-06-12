---
title: "I can't use my DVD Writer to burn DVDs or CDs anymore"
date: 2015-01-25
forum: General Help
---

### Post by dandyloon on 2015-01-25
Hello
since yesterday my DVD-Writer is not found by K3b and Brasero anymore
When I open K3b I get a messege:  [COLOR=#bf0303]No optical drive found.[/COLOR]
K3b did not find any optical device in your system.

In Brasero I can only choose to crate an Image

when I open devices in the Dash I se my Harddrive and a Block device where once my dvd-writer was shown.

When I enter a DVD or a CD I can access it via Nautilus and copy files to my Harddrive for exaple, because it shows up like a partition or usb-stick does.
Somehow my Ubuntu doesn't know it is a DVD-writer device anymore. I use Ubuntu 14.04.1.

I'm very thankfull for any Help

---

### Post by Sef on 2015-01-25
Have you changed anything, e.g., upgrade, added/deleted a program, changed hardware, etc.?

---

### Post by dandyloon on 2015-01-25
I only updated Pinta 1.3 to 1.5 a few days ago, because 1.3 didn't work on my System, but Pinta 1.5 now does well.
There also were some security updates during the last days, but I never read the details, just install them when shown.

are there links missing in my system?


mithos@mithos-desktop:~$ ls -ali /dev | grep sr0
8158 lrwxrwxrwx   1 root root           3 Jan 25 13:50 cdrom -> sr0
7833 brw-rw----+  1 root cdrom    11,   0 Jan 25 13:50 sr0
mithos@mithos-desktop:~$


And file 70-persistent-cd.rules opened in Nautilus has this:

 # This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-cd-aliases-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# HL-DT-ST_DVDRAM_GH22NS90 (pci-0000:00:08.0-scsi-0:0:0:0)
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:08.0-scsi-0:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:08.0-scsi-0:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:08.0-scsi-0:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:08.0-scsi-0:0:0:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"

---

### Post by dandyloon on 2015-01-28
Oh it seems like nobody can help me to solve my Problem :(

Is there really no way to make K3b and Brasero find my DVD writer again?

---

### Post by scottbomb on 2015-11-26
I'm having this same problem. Using Kubuntu 14.04.3 on a Lenovo T510. I can access CDs and DVDs with Dolphin, no problem. But when I put a blank disc in and fire up K3b or Brasero, they both complain that there's no optical drive. It shows up just fine in lshw:

```

*-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: DVD ROM DDU7700H
             vendor: Optiarc
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1RF0
             capabilities: removable audio dvd
             configuration: ansiversion=5 status=nodisc

```

My other system (full-size PC running same OS/version) handles blank discs just fine. They show up in K3b as "Empty DVD-R medium".

Any ideas on what to check next?

---

