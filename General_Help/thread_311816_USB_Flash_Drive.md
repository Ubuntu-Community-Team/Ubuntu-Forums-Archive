---
title: "USB Flash Drive"
date: 2006-12-03
forum: General Help
---

### Post by aiduciukas on 2006-12-03
Hi! I have Ubuntu Edgy Eft 6.10, and obe problem, when I plug usb flash in usb port nothung happens, i tried to restart with pluged flash and nothing happens too, my USB printer, webcam and wheel works fine. Any help?

[COLOR="Red"][SIZE="3"]Resloving problem:
Just type this comand in terminal:
**sudo update-initramfs -u -k `uname -r`**[/SIZE][/COLOR]

---

### Post by bapoumba on 2006-12-03
Hi,
please post the output to **lsusb** when your flash is plugged in. Do CDs (or other storage devices) show up on the desktop ?

---

### Post by aiduciukas on 2006-12-03
i tried lsusb when flash pluged in and when not plugged, it's the same. no any CDs and other devices doesn't show up on desktop, I just tried to connect my phone (motorola e398) and it shown up on desktop, but any other devices doesn't show up, what to do?

---

### Post by bapoumba on 2006-12-03
Two things :

1- assuming you have the GNOME environment, run gconf-editor form a terminal (> Accessories > Terminal).
> apps > nautilus > desktop > volumes_visible should be checked (so that's for storage devices to show up on the desktop).

2- is your flash usb device working on another computer ?

---

### Post by strabes on 2006-12-03
bapoumba: volumes_visible is checked for me and my mounted ext3 partition shows up on my desktop, but my ipod (mounted to /media/ipod) doesn't show up on the desktop, even when it's mounted. It *does* show up in the places menu. Any ideas?

---

### Post by aiduciukas on 2006-12-03
1. volume visible already chcked, because I can see mine windows drive
2. yes it works, I tried on notebook HP and on this computer but with win xp

---

### Post by bapoumba on 2006-12-03
@ strabes : in gconf-editor > desktop > gnome > volume_manager, is autoipod checked ? (I had seen your other thread ;))

@ aiduciukas : this is quite strange.
> System > Prefs > Removable drives > Storage. Mount removable drives when hot-plugged checked ?
Can you get to your flash drive from the Places menu ? It should be mounted in /media. Please also check /var/run/drive if not in media (it should NOT be there, but I have seen that once.
What is the output of cat /etc/mtab when your drive is plugged in.

---

### Post by aiduciukas on 2006-12-03
I checked in removables drives... in places menu and /media it isn't ;( ok tomorrow I'll try to see cat /etc/mtab output

---

### Post by strabes on 2006-12-03
bapoumba: it was not checked, however after I checked it, the icon still did not show up on my desktop after plugging it in again. Thanks for your help.

---

### Post by bapoumba on 2006-12-03
@ strabes : this may take effect after your next login (just a wild guess ;))

@ aiduciukas : OK. I am also checking for bug reports on this. I'll edit this post if I find something.

---

### Post by strabes on 2006-12-03
bapoumba: didn't take effect after restart :(

---

### Post by bapoumba on 2006-12-03
@ strabes : well, I do not own a ipod to check. I have done some searches, but did not find anything interesting ... Sorry :/

---

### Post by aiduciukas on 2006-12-04
/dev/hdc7 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-10-generic/volatile tmpfs rw 0 0
/dev/hdc5 /home ext3 rw 0 0
/dev/disk/by-uuid/3E0C244D0C23FF11 /media/windows fuse rw,nosuid,nodev,noatime,allow_other 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

ok it's cat /etc/mtab output

---

### Post by bapoumba on 2006-12-04
```
/dev/sda1 /media/usbdisk vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
```
This is what I get in mtab upon pluggin a usb flash drive.

Could you run gconf-editor > desktop > gnome > volume_manager > and check automount_drives ?

```
 $ apt-cache policy pmount
pmount:
  Installed: 0.9.13-1build1
  Candidate: 0.9.13-1build1

$ apt-cache policy hal
hal:
  Installed: 0.5.7.1-0ubuntu17
  Candidate: 0.5.7.1-0ubuntu17

```
Could you check you have the same versions of pmount and hal (both in main repository) ?

What is the output of **cat /etc/fstab** ?

I am not sure I quite understand this, and there is a [bug report]("https://launchpad.net/distros/ubuntu/+source/gnome-volume-manager/+bug/67307").

---

### Post by aiduciukas on 2006-12-04
Here's fstab output:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc7
UUID=72376a7e-bf28-48d9-93e1-003c9d1122f4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc5
UUID=81beae5c-4415-44e5-91c5-d9173f7cef79 /home           ext3    defaults        0       2
# /dev/hdc1
UUID=3E0C244D0C23FF11 /media/windows    ntfs-3g    defaults,locale=en_US.utf8    0    0
# /dev/hdc6
UUID=eff8b76b-a180-495a-850d-d9ae7b88f02d none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

and pmount's and hal's is same versions as yours ](*,) Any ideas?

---

### Post by bapoumba on 2006-12-04
Well, fstab looks okay, and when you plug in your flash drive, it does not show up neither in mtab nor in lsusb, am I right ?
There is another bug :
[https://launchpad.net/distros/ubuntu/+source/pmount/+bug/68851]("https://launchpad.net/distros/ubuntu/+source/pmount/+bug/68851")
with a procedure you might want to follow to add your comments to that bug :
[https://wiki.ubuntu.com/DebuggingRemovableDevices]("https://wiki.ubuntu.com/DebuggingRemovableDevices")

---

### Post by aiduciukas on 2006-12-05
When I plug flash into USB 2.0 port, light is blinking and when I plug into USB 1.1 Port light just lights but not blinks, these bug reports doesn't helped ;( any ideas? hmmmm and I found this on end of dmesg:
[17181589.668000] usb 4-2: new high speed USB device using ehci_hcd and address 73
[17181605.544000] usb 4-2: new high speed USB device using ehci_hcd and address 10
[17181608.568000] usb 4-2: new high speed USB device using ehci_hcd and address 21
[17181632.508000] usb 4-2: new high speed USB device using ehci_hcd and address 115
[17181638.556000] usb 4-2: new high speed USB device using ehci_hcd and address 13
[17181694.500000] usb 4-2: new high speed USB device using ehci_hcd and address 89

---

### Post by bapoumba on 2006-12-05
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/54419]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/54419")
One more bug you might want to check out. You could try the irqpoll option at boot time.
If on a desktop, have you tried the usb from your mother board (the ones at the rear of the computer) or a powered usb hub ?

---

### Post by aiduciukas on 2006-12-05
YESSS!!!! IT WORKS! Last link is da best ;D type this **sudo update-initramfs -u -k `uname -r`** and all will work! I LOVE YOU BAPUOMBA! :DD thanks!

---

### Post by bapoumba on 2006-12-05
Cool !!
Congratulations. Hope this might help other people ;)

---

### Post by aiduciukas on 2006-12-05
I edited first post with that command and one more thing, after beryl installation and uninstallation, when I want to switch windows I need to press the titlebar, I remember that I could press anywhere in window zone. any ideas? ;)

---

### Post by bapoumba on 2006-12-05
Well, I do not know much about beryl and stuff, not using it. Are you back with metacity ?
In gconf-editor :
apps > metacity > general > raise_on_clic checked ? You could still use alt-left-click anywhere on the window according to this key description.

---

### Post by aiduciukas on 2006-12-05
Yes it's checked but I want like in windows, I can click anywhere in window, on your avatar, on text o smth. and window will be activated, but now I can click just on titlebar(where close, minimize, maximize is) to activate the window, btw I'm using metacity now, because beryl was too slow

---

### Post by mtaggart on 2007-12-16
attn:  bapoumba

I am in full agreement regarding your very thorough & systematic troubleshooting.  I ran into a similar problem this week, when my machine suddenly started ignoring all my USB memory devices.  I'd been driven to 2 re-installs, and the problem continued to exist.  

Today I came across your directions in this post, and followed them line by line.  I discovered a very odd thing:  from a brand-new install & update, hal was loaded, but pmount was NOT.  Installed pmount using Synaptic, and now everything works perfectly again. 

So indeed, this thread DOES help others!  :)  Thanks for your efforts-- folks like you make troubleshooting Ubuntu a hell of a lot easier.

---

