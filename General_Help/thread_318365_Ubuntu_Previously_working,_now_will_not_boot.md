---
title: "Ubuntu Previously working, now will not boot"
date: 2006-12-13
forum: General Help
---

### Post by jrichardson on 2006-12-13
Fairly new to linux. I have successfully installed MEPIS, Knoppix, and CENTOS Desktop and Server but they were pretty straightforward installations so I did not learn much about the nuts and bolts.

Recently after my desktop Windows machine got hammered by the worst Worm I have ever seen I decided to flatten my machine (since it was going to need it anyway) and install Kubuntu.

I successfully installed Ubuntu Edgy and had used it for several days. I was very happy with it, loved the stability and performance. I was able to add programs and updates with no problems and successfully archived several dvd's as well as install firefox 2.0, and even had a Windows Emulator running with working programs.

So that's the good part. Now the bad part.

I shut down the machine on Sunday morning and left town for a couple of days. When I returned I started the machine only to get internal speaker beeps during booting, and then the boot stops at the point where I would expect to see the login screen

I used the ESC during GRUB and then edited the boot to remove the quiet and splash screens. After rebooting I saw that the beeps occurred during

[B]jr-desktop lofin: *starting Common Unix Printing System System: cupsd
 * Starting HP Linux Printing and Imaging System
 * Starting apt index watcher apt-index-watcher
 * Starting system message bus dbus
 * Starting Hardware abstraction layer hald
 * Starting powernowd...
 * Starting Bluetooth services                                                              [OK][/B]

Then the beeps stop, and the following loads

[B]* Starting anac(h)ronistic cron: anacron
 * Starting deferred execution scheduler atd
 * Starting periodic command scheduler...
 * Checking battery state...                                                                 [OK][/B]

then the boot hangs at

*** Running local boot scripts (/etc/rc.local)                                          _  **  

with the cursor blinking in the right corner

If I hit the enter key I get:

[B]Login incorrect
jr-desktop login:[/B]

When I use my username and password I get some text followed by a prompt.
[B]The programs included.........to the extent permitted by law.
jr@jr-desktop:~$[/B]

If I look at the dir, I see that the my home folders and files are there.

Obviously something got hosed during one of the updates, or program installations. I have tried stripping the hardware down to the basics; monitor, keyboard, mouse, SATA drive but it did not change anything so I suspect it's not related to the CD ROM, IDE drives, or USB devices.

I'd like to get this running again rather than starting over, it took alot of hours to get the programs I wanted installed and working.

any ideas????

build info:
Ubuntu 6.10 Kernel 2.6.17-10-386
Pentium 4
1G ram
160G SATA
80G IDE
DVD/CDRW
CD/RW


Jerry Richardson

---

### Post by wpshooter on 2006-12-13
Is it possible that your machine got hit by lightning or a massive power surge while you were gone or is it possible that you are having hard drive or other hardware problems ?

Are you sure that what you had to start with was really a virus problem and not the signs of developing hardware problems ?

---

### Post by d3v1ant_0n3 on 2006-12-13
What happens if you put ```
startx
``` in at the prompt?

---

### Post by jrichardson on 2006-12-13
That was quick...Thanks!

No possibility of lightning, no power failures.

No, I am not sure about the HW vs/virus although it was definately a worm - every time I got it corralled it popped up somewhere else.

Can you suggest, or do you know of a small distro that can run a diagnostic on a machine?

Thanks again

---

### Post by jrichardson on 2006-12-13
/usr/bin/startx: line 132: cannot create temp file for here document: Read-only file system
xauth: error in locking authority file /home/jr/.Xauthority
/usr/bin/startx: line 144: cannot create temp file for here document: Read-only file system
xauth: error in locking authority file /home/jr/.Xauthority
/usr/bin/startx: line 144: cannot create temp file for here document: Read-only file system

Fatal server error
Could not create lock file in /tmp.tX0-lock

giving up.
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): Server error
xauth: error in locking authority file /home/jr/.Xauthoruty
jr@jr-desktop:~$

I can only get to the login if I boot with splash and quiet removed from the boot.

Thanks in advance!

---

### Post by d3v1ant_0n3 on 2006-12-13
Ok...I have no idea about those errors:-? 

Sorry, I've had a vaguely similar problem that wa the result of a screwed up xorg...I managed to diagnose with startx's errors.

Have you tried booting into recovery mode and trying the same from there? It will log you into a prompt as root

---

### Post by jrichardson on 2006-12-13
Tried recovery mode - same error

For some reason the /root/.Xauthority file appears to have been changed to read only. any ideas how to change the rights?

---

### Post by Dave54 on 2006-12-13
Is there any chance this could be related to the Nvidia driver / kernel update breakage today?

---

### Post by Rodneyck on 2006-12-13
> **Dave54 said:**
> Is there any chance this could be related to the Nvidia driver / kernel update breakage today?

That would be my bet... 

[http://ubuntuforums.org/showthread.php?t=318206](http://ubuntuforums.org/showthread.php?t=318206)

---

### Post by jrichardson on 2006-12-13
Don't think so.

Booted in recovery mode. 

Tried apt-get install linux-386 and got

[B]W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.[/B]

It appears that the files are all read only. Not sure how that happened or how to change them back...

this is a drag - i thought this was going to make my life easier...

---

