---
title: "NeroLinux Help Request"
date: 2007-04-13
forum: General Help
---

### Post by elephant007 on 2007-04-13
I've downloaded and installing [NeroLinux]("http://www.nero.com/eng/NeroLINUX.html") which I like so far...
the problem I have is that I have to either run NeroLinux with sudo or in a terminal do this code
```
chmod o+r+w /dev/sg*
```
then run NeroLinux
this is done so I can write to the CD-R

Every time I log off or reboot my computer, I have to re-run the command or use sudo.
My question is this, how can I change so I have access to the write permissions to the CD-R so I can use NeroLinux without having to run the command or use sudo?
Nero said it is possible to setup a nero group with permissions, I attempted that and it failed to work....

Thank you in advance.

---

### Post by elephant007 on 2007-04-13
okay, I figured it out myself.  

```
sudo addgroup nero
sudo adduser <username> nero
sudo chgrp nero /dev/sg0
```

of course you can name your group anything you'd like to name it
and /dev/ to where ever your device is located

---

### Post by elephant007 on 2007-04-14
This change does not stay between log off, shutdowns or reboots.  How can I make the change permanent?**

---

### Post by noynac on 2007-04-14
elephant007,

I don't have a direct answer to your question. I installed NeroLinux 2 and did not encounter any problems.

I thought I might mention that a NeroLinux forum moderator has reported that a beta of NeroLinux 3 will be available next Thursday. So, rather than spend a great deal of time with version 2, you may want to wait to see if the new version solves the issue.

BTW, the new features in NeroLinux 3.0 include:

* Exact same GUI as Nero Burning ROM (except some adaptions for Linux)

* Lots of new features & options (basically all features from Burning ROM)

* Supports all type of devices (IDE, S-ATA, SCSI, USB and FireWire)

* Support HD media burning (HD DVD and Blu-ray) even if you do not have a physical device (using the Image Recorder)

* Translated in the 26 Nero official languages (but some strings are still missing)

I've seen a screenshot of the beta, and it looks much better than the existing verison.

noynac

---

### Post by elephant007 on 2007-04-19
I'll try that, thank you

---

### Post by yabbadabbadont on 2007-04-19
> **elephant007 said:**
> This change does not stay between log off, shutdowns or reboots.  How can I make the change permanent?**

I added a udev rule to change the group and mode of the /dev/sg* devices to correct this issue.

```
/home/daffy $ tail -1 /etc/udev/rules.d/40-permissions.rules 
KERNEL=="sg[0-9]*",                     GROUP="cdrom", MODE="0660"

```

---

