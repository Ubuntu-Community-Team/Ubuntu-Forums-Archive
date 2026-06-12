---
title: "Create a raid0 software install"
date: 2018-04-28
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2018-04-28
I have a old core 2 duo system with a pair of HDDs in it
figured would do a quick test install *2 hours later; well that was a failure...*
on a live usb i installed mdadm *dpkg exits with status code 1*
ran
```
sudo mdadm --create --verbose /dev/md0 --level=0 --raid-devices=2 /dev/sda /dev/sdb
```
this system has a DG965OT motherboard, i tried the bios raid0 and got errors trying to make a install, so i figured i would give software a try
when i got this thing it had XP on it with raid1 via bios

my understanding is when you raid0 the hdds are treated as one, but i do not see how the bios can see how to boot it since it only has 2 hdds and not a 3ed to have /boot; the fdd is not working... (i got 3 free system 2 dells and a low end custom build and every fdd is not working...)

*first time trying to use raid

---

### Post by TheFu on 2018-04-28
Which release?   18.04 has issues with LVM and RAID according to the release notes.  Always read the release notes.

---

### Post by pqwoerituytrueiwoq on 2018-04-28
using the xubuntu amd64 18.04 iso via usb boot (multi boot)

using bios raid i was getting a partition out of disk error

i do not see it saying there are issues just to use the alt installer
```
submenu 'Ubuntu 18.04' --class submenu --id bionic {
    menuentry "Xubuntu 18.04 Desktop 64bit" --class xubuntu --class gnu-linux --id bionic {
        set isofile="/iso/Bionic/xubuntu-18.04-desktop-amd64.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
    }
    menuentry "Ubuntu Mate 18.04 Desktop 64bit" --class ubuntumate --class gnu-linux --id bionic {
        set isofile="/iso/Bionic/ubuntu-mate-18.04-desktop-amd64.iso"
        loopback loop $isofile
        linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noeject noprompt splash --
        initrd (loop)/casper/initrd.lz
    }
}
```
is there a way to launch the alt installer

on the note of the gui installer is there a way to make it not wait on a timeout to ask if i want to try to unmout a disk that can not be unmounted as that is the install media, in the past it would take maybe 10 seconds, but on this old system it seems like one or 2 minutes (long enough to type this paragraph with one and and fix the typos and still wait)

---

### Post by TheFu on 2018-04-28
I didn't see the alternate installer at the link provided in the release notes.  Perhaps next week.

---

