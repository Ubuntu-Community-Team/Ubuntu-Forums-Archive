---
title: "HELP !  Keyboard not responding after &quot;dpkg-reconfigure xkb-data&quot;"
date: 2017-01-30
forum: General Help
---

### Post by jf-moniquelevi on 2017-01-30
Lenovo laptop just upgraded to 16.04 LTS.

Tried to change the keyboard layout per ubuntu help.

Edited the /usr/share/X11/xkb/us file to suit my need.

Then I did what it says in Help:

```
There is a change in Ubuntu version (13.10) and later versions which causes the keyboard settings cache to not refresh after files in "/usr/share/X11/xkb/symbols" directory are modified. It looks like changes just don't get applied. To force the cache refreshing a one should delete *.xkm files from "/var/lib/xkb", or enter into the console: 

sudo dpkg-reconfigure xkb-data
```After this command I lost the keyboard. I cannot even go in command line, Ctl-Alt-F1 does nothing.
Invoking the soft keyboard (on-screen) it pops up with question marks on each key.
However, going to GRUB command line it works perfectly, so the hardware is not the problem.

I get a message about missing files, but I didn´t copy them, and I cannot get in my system since I cannot type the password !

I tried: sudo dpkg-reconfigure keyboard-configuration, didn do anything.

I have been working on this all week-end, utterly aggravated !!!

I would really try to avoid re-install considering the time spent to download and install all the apps, setting, passwd, etc.

Your help would be greatly appreciated !!!!!!!!!

The error messages:

```
Error starting interface
Keyboard monitoring will
be disabled.
Check your system/configuration.
<class 'xlib.error. BadAlloc' code 11, resource id
0
sequence number
1, ajor opcode or opcode 0
OK


Error activating XKB configuration.
t can happen under various circumstances:
a bug in libxklavier library
a bug in X server (xkbcomp, xmodmap utilities)
X server with incompatible libxkbfile implementation
X server version data:
The X.Org Foundation
11804000
If you report this situation as a bug, please include
The result of xprop -root l grep XKB
The result of gsettings list-keys org.mate.peripherals-
keyboard-xkb.kbd
```

---

### Post by DuckHook on 2017-01-30
It sounds like you have a corrupted xkb subsystem.

Try the following:

[LIST=1]
[*]You will need a LiveUSB of 16.04
[*]Boot into the LiveUSB.
[*]Find the device designation assigned to the HDD/partition of your broken install using:```
sudo blkid
```
[*]You will need to chroot into your borked system and repair the xkb-data pkg beginning with:
```
sudo mkdir /mnt/foo
```
[*]If device is, say, /dev/sda2, then:
```
sudo mount /dev/sda2 /mnt/foo
```
[*]Make sure this shows a typical installed root directory with:```
ls -laF /mnt/foo
```
[*]If everything looks proper, then the next series of steps:
```
sudo mount --bind /dev /mnt/foo/dev
``` 
```
sudo mount --bind /dev/pts /mnt/foo/dev/pts
```
```
sudo mount --bind /proc /mnt/foo/proc
```
```
sudo mount --bind /sys /mnt/foo/sys
```
[*]Now, to chroot into this directory:
```
sudo chroot /mnt/foo
```
[*]And finally:
```
apt install --reinstall xkb-data
```
[/LIST]
The above procedure "borrows" the functionality of the LiveUSB session to go in and reinstall the xkb-data pkg on your broken system. If it works, don't change xkb-data the way that you did. I assume that you just want a non-English keyboard. There are better ways to achieve that.

---

### Post by jf-moniquelevi on 2017-01-31
Thanks a lot !!!
Actually, thinking about it, it was pretty stupid of me.
I wanted to add a couple of accented letters to the US kbd, just editing the US file does it.  I followed blindly the "HELP" description. I should know better, been on Ubuntu since Dapper Drake; things were not as easy then ;)

I will try your suggestion and report here.

Have a great day !!!

---

