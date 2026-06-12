---
title: "No sound"
date: 2007-10-29
forum: General Help
---

### Post by MikeMLP on 2007-10-29
Greetings,

Periodically, I have sound problems using Ubuntu (on the past several releases).  

Just a few weeks ago, sound was working perfectly in my current install of Gutsy.  I believe there were a few updates, and I uninstalled some unneeded things (like some old kernels from the beta process).  I wish I could say exactly when / after what changes sound stopped working, but I can't.

Right now, the situation is that there are no sounds at all - no startup sounds, no sounds in apps, no system beeps... nothing.  I know my hardware is ok, because sound works fine in my windows partition.

I would really appreciate it if someone could walk me through a troubleshooting process.

According to device manager, I have an Intel 82801DB-ICH4 Audio Controller.  I'm using an IBM Thinkpad T42.

---

### Post by Crafty Kisses on 2007-10-29
> **MikeMLP said:**
> Greetings,

Periodically, I have sound problems using Ubuntu (on the past several releases).  

Just a few weeks ago, sound was working perfectly in my current install of Gutsy.  I believe there were a few updates, and I uninstalled some unneeded things (like some old kernels from the beta process).  I wish I could say exactly when / after what changes sound stopped working, but I can't.

Right now, the situation is that there are no sounds at all - no startup sounds, no sounds in apps, no system beeps... nothing.  I know my hardware is ok, because sound works fine in my windows partition.

I would really appreciate it if someone could walk me through a troubleshooting process.

According to device manager, I have an Intel 82801DB-ICH4 Audio Controller.  I'm using an IBM Thinkpad T42.
You should try giving us the following output:
```
lspci
```

---

### Post by MikeMLP on 2007-10-29
```
:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

```

---

### Post by MikeMLP on 2007-11-03
Well, I really need sound, and since no one seems able to help, I'd like to achieve it by means of a reinstall.  The Gutsy livecd's sound works fine.  The only problem is that I have a lot of settings in /home that I need to keep.  Due to HDD space constraints, I keep /home on the same partition as my os install.

I've tried copying /home to a partition that will not get destroyed so I can restore all my settings after the fresh install, but it keeps erroring out.  I'll get error messages throughout the copy, and then it'll just stop copying about 3/4 of the way through.  This happens as root, and as root using the livecd (I assumed that maybe some of the errors not allowing me to copy files might have been related to the idea that they were in use.)  I'm confused... when is a root user not able to do basic file manipulations?

My exact method is as follows:

```
~$ gksudo nautilus
```

I then copy /home, and past into /fat (my fat32 partition).  It will start copying and then I'll get an error window:
> Error "Operation not permitted" while copying "/home/mike...en-GB.soe". Skip, Cancel, Retry

the terminal will display the following message:
```
** Message: Hit unexpected error "Operation not permitted" while doing a file operation.
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS

```


What can I do to reliably back up /home (a separate partition is not an option)  Is there a backup utility that will get around these errors, do I have to turn it into a .tar?  If so, how do I do this?

---

### Post by Pumalite on 2007-11-03
You might want to try one of these two:
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by MikeMLP on 2007-11-03
Partimage wont work for me because my / is on the same partition as my /home.  I'm trying to replace my / with a fresh install to fix the sound problem mentioned above.

I tried using the backup method mentioned in your other link, however I get errors anytime I try to transfer certain files to another disk or partition (see above)  I tried archiving the data and then transferring it to another disk / partition.  That worked, however the archive fails to extract (I want to make sure it extracts on another disk before reinstalling because my data consists of the files within the archive.  An archive alone that refuses to extract is useless):

```
tar: Backup110307/.gtkrc-1.2-gnome2: Cannot utime: Operation not permitted
tar: Backup110307/.Xauthority: Cannot utime: Operation not permitted
tar: Backup110307/.tomboy.log: Cannot utime: Operation not permitted
tar: Backup110307/.profile: Cannot utime: Operation not permitted
tar: Backup110307/.gksu.lock: Cannot utime: Operation not permitted
tar: Backup110307/.bash_logout: Cannot utime: Operation not permitted
tar: Backup110307/nautilus-debug-log.txt: Cannot utime: Operation not permitted
tar: Backup110307/bookmarks_100307.html: Cannot utime: Operation not permitted
tar: Backup110307/.ICEauthority: Cannot utime: Operation not permitted
tar: Backup110307/.dmrc: Cannot utime: Operation not permitted
tar: Backup110307/.gpilotd.pid: Cannot utime: Operation not permitted
tar: Backup110307/.xsession-errors: Cannot utime: Operation not permitted
tar: Backup110307/config.log: Cannot utime: Operation not permitted
tar: Backup110307/.sudo_as_admin_successful: Cannot utime: Operation not permitted
tar: Backup110307/.mcoprc: Cannot utime: Operation not permitted
tar: Backup110307/.bash_history: Cannot utime: Operation not permitted
tar: Backup110307/intltool-update: Cannot utime: Operation not permitted
tar: Backup110307/intltool-extract: Cannot utime: Operation not permitted
tar: Backup110307/.glade2: Cannot utime: Operation not permitted
tar: Backup110307/.esd_auth: Cannot utime: Operation not permitted
tar: Backup110307/.gtk-bookmarks: Cannot utime: Operation not permitted
tar: Backup110307/.recently-used.xbel: Cannot utime: Operation not permitted
tar: Backup110307/drawing.gif.svg: Cannot utime: Operation not permitted
tar: Backup110307/config.status: Cannot utime: Operation not permitted
tar: Backup110307/intltool-merge: Cannot utime: Operation not permitted
tar: Backup110307/.bashrc: Cannot utime: Operation not permitted
tar: Backup110307/.recently-used: Cannot utime: Operation not permitted
tar: Backup110307/Makefile: Cannot utime: Operation not permitted
tar: Backup110307/.thumbnails: Cannot utime: Operation not permitted
tar: Backup110307/.thumbnails: Cannot change mode to rwx------: Operation not permitted
tar: Backup110307/.wapi: Cannot utime: Operation not permitted
tar: Backup110307/.wapi: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: Backup110307/.gimp-2.4: Cannot utime: Operation not permitted
tar: Backup110307/.gimp-2.4: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: Backup110307/.beagle: Cannot utime: Operation not permitted
tar: Backup110307/.beagle: Cannot change mode to rwx------: Operation not permitted
tar: Backup110307/.gnome2_private: Cannot utime: Operation not permitted
tar: Backup110307/.gnome2_private: Cannot change mode to rwx------: Operation not permitted
tar: Backup110307/.nautilus: Cannot utime: Operation not permitted
tar: Backup110307/.nautilus: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: Backup110307/.tomboy: Cannot utime: Operation not permitted
tar: Backup110307/.tomboy: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: Backup110307/.local: Cannot utime: Operation not permitted
tar: Backup110307/.local: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: Backup110307/.gstreamer-0.10: Cannot utime: Operation not permitted
tar: Backup110307/.gstreamer-0.10: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: Backup110307/.java: Cannot utime: Operation not permitted
tar: Backup110307/.java: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: Backup110307/.evolution: Cannot utime: Operation not permitted
tar: Backup110307/.evolution: Cannot change mode to rwxr-xr-x: Operation not permitted

...

tar: Backup110307/.openoffice.org2/user: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: Backup110307: Cannot utime: Operation not permitted
tar: Backup110307: Cannot change mode to rwxr-xr-x: Operation not permitted
tar: Error exit delayed from previous errors
```

---

### Post by Pumalite on 2007-11-03
Sorry my links didn't work.
Regarding your 'No Sound'; have you tried:

sudo apt-get install linux-backports-modules-generic

---

### Post by MikeMLP on 2007-11-04
I installed the package mentioned above and restarted (to be sure), but still no sound.  A correction to what I said before:  System beeps appear to work (and did work before the installation of this package).  No audio files of any sort play, however, including the usual Ubuntu startup and shutdown sounds.

I can't figure out why I'm unable to get a clean copy of my /home.  I do remember this being an issue in previous (cleanly installed) versions of Ubuntu, so this is not just a problem with this particular install.  As I said before, when is root not root?

---

