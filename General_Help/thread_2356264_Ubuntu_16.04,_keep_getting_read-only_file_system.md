---
title: "Ubuntu 16.04, keep getting read-only file system"
date: 2017-03-21
forum: General Help
---

### Post by digital-larry on 2017-03-21
Now that this has happened a few times I now recognize the symptoms.  First symptom is browsers not working, or unable to save anything.  Then I see Package Update manager icon at upper right, red circle with grey horizontal bar suggesting that I should do some things with the package manager.  These steps fail.  Eventually I get a message that I am using a read-only file system.

Recourse which seems to work is to reboot and drop into the maintenance shell or whatever it's called, and run:

fsck /dev/sda7

/dev/sda7 is the Ubuntu partition on my dual-boot laptop with Windows 10 also installed.

After cleaning up all the disk errors, I can once again boot and the system seems OK for awhile.  I don't recall this happening on 14.04 on the same laptop.  I am not having any known issues with the hard drive when I run Windows 10 (there is only one physical drive).

This happens once a week?  Once every two weeks?  Not all the time but often enough to be getting pretty annoying.

Any clues about how to prevent this from happening?  Or seeing if there's really something wrong with the hard drive itself?

Thanks,

DL
==============================
$ cat /etc/os-release 
NAME="Ubuntu"
VERSION="16.04.1 LTS (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04.1 LTS"
VERSION_ID="16.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
VERSION_CODENAME=xenial
UBUNTU_CODENAME=xenial

---

### Post by SeijiSensei on 2017-03-21
Never turn off the power to shut down.  You must shut down the system from the menus or with the "shutdown" or  "reboot" commands in the terminal.  Only those methods can ensure that the file systems will be unmounted before the machine turns off.  If you have unreliable power, get a UPS.

---

### Post by efflandt on 2017-03-22
That is usually a sign of a failing drive. If Linux gets too many drive errors, it remounts the file system read-only to avoid further damaging anything.

Check /var/log/syslog for any drive errors, but that will not log anything once it goes read-only. So if that happens again, see what **dmesg** in a terminal says. If you want to copy any text from that, save it to USB memory stick, external drive, or SD card.

---

### Post by digital-larry on 2017-03-22
Thanks for the replies.  It is conceivable that I power cycled the laptop because it seems to lock up from time to time, no particular pattern other than it doesn't like to come out of a suspend sometimes.  I will try to get the syslog and dmesg next time around.

Cheers,

DL

---

