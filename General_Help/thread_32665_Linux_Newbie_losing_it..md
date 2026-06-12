---
title: "Linux Newbie losing it."
date: 2005-05-08
forum: General Help
---

### Post by momo66 on 2005-05-08
Ok Im about to give up and go back to Windows.  I cant believe Im saying that but I have been troubleshooting this issue all weekend and I cant get dvd::rip to work.

Finally was able to get installed but did get errors when installing transcode, but kept plugging.  Now.... 

In the rip process usind dvd::rip  libdvdread gives the error 

Couldn't find device name

My settings for Preferences are

DVD device  /dev/dvd

DVD mount point /media/cdrom0

my /etc/fstab file reads

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb1	/mnt		ext3	rw		0	0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

thanks for any help.

---

### Post by defkewl on 2005-05-08
I think your settings for preferences for DVD device should be /dev/hdd  

CMIIW

---

### Post by tkiesel on 2005-05-09
or /dev/hdc perhaps.

---

### Post by momo66 on 2005-05-09
[QUOTE=tkiesel]or /dev/hdc perhaps.[/QUOTE]
 Its able to read the DVD drive initially.  It picks out the vob files and but when I go to rip - thats when libdvdread gives the error that it cant find the device.

I did change it to dev/hdc and it couldnt read the disc at all.  I will try hdd this evening.

I wish it would be that simple to fix but it doesnt make sense that it read the DVD initially and then it cant find it during the rip process.

---

### Post by momo66 on 2005-05-09
Ok i found the answer at the dvdrip documentation site.  

> 6.4 Why complains transcode about a missing VIDEO_TS.IFO file?

That's Ok. The corresponding messages are printed by libdvdread if you transcode files on harddisk (what's the default case with dvd::rip). You see something like this:

  libdvdread: Couldn't find device name.
  libdvdread: Can't open file VIDEO_TS.IFO.

but these are only (very confusing) warning messages of libdvdread, which naturally can't find any DVD device or VIDEO_TS.IFO file if started from a directory with only VOB files in it. Just ignore these messages, and please don't report this as a bug.

So i knew where my DVD device was afterall.  It turns out that I was getting that error when using divx for transcode.  When I switched to ffmpegx it worked fine.

---

