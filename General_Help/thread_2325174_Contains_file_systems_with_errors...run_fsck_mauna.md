---
title: "Contains file systems with errors...run fsck maunally (16.04)"
date: 2016-05-19
forum: General Help
---

### Post by anthony58 on 2016-05-19
Out of nowhere the app launcher and icons disappeared and rendered Ubuntu useless.  After rebooting , this error shows up...
[IMG]https://goo.gl/photos/eJ9cuD4Dx6xsnSReA[/IMG]
I have tried using the fsck -a /dev/sdb1 as root but it did not fix the problem, yielding...
[IMG]https://goo.gl/photos/4B8i7XwjXRYNrNu96[/IMG]
Using the same command not using root access (which I got into by using sudo -i) says that it is unmounted and continuing can be fatal to the drive.  This is currently running off of a flash drive which is currently where I have Ubuntu installed on(not a live usb, though I amusing one to access the terminal).

Any help on how I can fix the filesystem and make Ubuntu usable again would be greatly appreciated.

---

### Post by anthony58 on 2016-05-19
Title should say run fsck manually, my bad.

---

### Post by cariboo on 2016-05-20
I fixed the title for you

---

### Post by vanadium on 2016-05-20
You will need to do the file system check while sda1 is not mounted. This can be done either from a root prompt in recovery mode or from a session booted from a live USB or CD. You can reach the root prompt in recovery mode from the grub menu. The latter, in turn, may be shortly visible if you dual boot with Windows. If it is not visible, then press Shift while grub is loading to display it.

---

