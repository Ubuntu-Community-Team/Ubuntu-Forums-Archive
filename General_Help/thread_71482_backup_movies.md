---
title: "backup movies"
date: 2005-10-03
forum: General Help
---

### Post by Ubuntu_User on 2005-10-03
Do you know any program so i can make backup of my original movies? :confused:

---

### Post by yage on 2005-10-03
[http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/)

---

### Post by Ubuntu_User on 2005-10-05
Please someone help me with that. I installed DvdShrink and Dvd decrypter but they dont see my devices!

---

### Post by Xumbi on 2005-10-05
This sounds like a permissions issue.
Can you post the output of these commands?

mount
ls -l /dev/hd*

---

### Post by Ubuntu_User on 2005-10-05
**mount**:
/dev/sda5 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev/sda1 on /media/windows type ntfs (rw,iocharset=utf8,umask=000)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

**ls -l /dev/hd***
brw-rw----  1 root cdrom 3,  0 2005-10-05 07:34 /dev/hda
brw-rw----  1 root cdrom 3, 64 2005-10-05 07:34 /dev/hdb


What's the problem? :confused:

---

### Post by Ubuntu_User on 2005-10-06
Nobody? :confused: 

Help

---

### Post by professor_chaos on 2005-10-06
Have you made sure your links are correct.
goto your ~/.wine/dosdevices directory and check the paths with ls -l

do you have something like this? d: -> /media/cdrom1
if not, make it so.

---

### Post by Emerzen on 2005-10-06
Check this program out.  It is Linux native, so no emulation.  Only draw back is the movie is copied as one long chapter.  There's also acidrip and dvdrip, which are capable but increasingly complicated in that order.

[http://dvdshrink.sourceforge.net/index.html](http://dvdshrink.sourceforge.net/index.html)

---

### Post by Ubuntu_User on 2005-10-07
where i can find **transcode**? and how i must install it?

---

### Post by foxy123 on 2005-10-07
[QUOTE=Ubuntu_User]where i can find **transcode**? and how i must install it?[/QUOTE]
try this [http://archive.ubuntu.com/ubuntu/pool/multiverse/t/transcode/](http://archive.ubuntu.com/ubuntu/pool/multiverse/t/transcode/)

---

### Post by KLineD on 2005-10-07
if you installed a newer wine that the one in mrbass tutorial just type winecfg in a console. There, you can configure your devices for Wine. That's what I did to get it to work

---

### Post by Ubuntu_User on 2005-10-07
[QUOTE=Emerzen]Check this program out.  It is Linux native, so no emulation.  Only draw back is the movie is copied as one long chapter.  There's also acidrip and dvdrip, which are capable but increasingly complicated in that order.

[http://dvdshrink.sourceforge.net/index.html](http://dvdshrink.sourceforge.net/index.html)[/QUOTE]

This worked perfect! Thank you folks!
Thank you **foxy123**, i installed transcode perfect!
Thanx.

Just a last question... THis xdvdshrink has gui? or its only that script? 
But it's ok without it, i like it, i just backed up my first movie in Ubuntu!
Just asking about gui...:)

---

### Post by Emerzen on 2005-10-07
Do you have all the repositories added (universe and multiverse) as well as Hoary-Backports?  I believe I found my version in Backports.

---

### Post by Emerzen on 2005-10-07
UbuntuUser,
xdvdshrink does have a GUI.  By default it runs as a terminal program.  If you want the GUI:  The folder you extracted from the download...  Browse inside this folder->usr->bin->xdvdshrink.pl

Double click on the file xdvdshrink.pl and a GUI window should open (you have to select to run this in a terminal I believe).  If you want to add this to your application menu, use the application menu editor under system tools and add the command

sudo xdvdshrink.pl

I believe that should do it.  If you have any problems let me know, as it's been awhile since I installed it.  Also, I found using the GUI, I was able to configure it properly, the terminal version never worked quite right as I wasn't good w/ all the settings.

---

### Post by foxy123 on 2005-10-08
[QUOTE=Emerzen]UbuntuUser,
xdvdshrink does have a GUI.  By default it runs as a terminal program.  If you want the GUI:  The folder you extracted from the download...  Browse inside this folder->usr->bin->xdvdshrink.pl

Double click on the file xdvdshrink.pl and a GUI window should open (you have to select to run this in a terminal I believe).  If you want to add this to your application menu, use the application menu editor under system tools and add the command

sudo xdvdshrink.pl

I believe that should do it.  If you have any problems let me know, as it's been awhile since I installed it.  Also, I found using the GUI, I was able to configure it properly, the terminal version never worked quite right as I wasn't good w/ all the settings.[/QUOTE]
I suspect it should be 

```
gksudo xdvdshrink.pl
```

---

### Post by jeremy on 2005-11-07
Can't it just be xdvdshrink.pl (without sudo)?

---

