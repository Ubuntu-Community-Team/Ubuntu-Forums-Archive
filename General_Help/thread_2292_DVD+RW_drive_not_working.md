---
title: "DVD+RW drive not working"
date: 2004-10-26
forum: General Help
---

### Post by SFN on 2004-10-26
I installed Warty today on a box containing a NU DVDRW DDW-081. Everything works except this drive. It shows correctly in dmesg, like so:

hdc: NU DVDRW DDW-081, ATAPI CD/DVD-ROM drive

It also got added to fstab automatically:

/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0

I went through the Multimedia HOWTO (which worked perfectly on laptop I might add - kudos!) but when I try to play a DVD in MPlayer, I get:

Couldn't open DVD device: /dev/dvd

If I throw a data disc in there it doesn't automount. When I try to mount by hand, I get:

mount: No medium found

If I try to write to a DVD using Nautilus CD creator I get:

Reload rewritable or blank media
Please replace the in-drive media by a rewritable or blank media.

Since this drive worked just an hour before I did the Ubuntu install (in SuSE 9.1) I have to assume it's not the drive.

I did a number of googles on DDW-081 and Linux as well as DVD writer searches here. Found a number of problems but they all seem to be about someone being able to write but not watch DVDs or read discs but not write. Nobody seems to have no functionality at all.

I'm guessing it has to do with SCSI emulation. I did a search on that here as well but didn't come up with anything.

Has anybody else come across this problem?

Thanks.

---

### Post by mark on 2004-10-27
I can't get DVDs (movies) to play yet, but I think that's a config issue - just a mtter of time until I get motivated enough to really dig into it.  Everything else seem to be working fine.  I have a LITE-ON SOHW-812S DVD+R/W drive; the */etc/fstab* entry is: ```
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
``` and *dmesg* returns: ```
hdd: LITE-ON DVDRW SOHW-812S, ATAPI CD/DVD-ROM drive
``` I've burned several CDs and DVDs with *Nautilus*, all okay - but I haven't done anything with music files yet - just data.  Music CDs play just fine, auto-launching *Gnome-CD* on insertion.

Let me know if there are any specifics you would like & I'll be glad to post them.

Regards,

Mark

---

### Post by SFN on 2004-10-27
So it looks like the only problem you have is viewing DVDs, is that right?

I ran into a similar problem when I first installed SuSE. This same situation was coming up with both my CDROM and my DVDRW drives. Turns out the DMA settings were set to Off (which, WTF?). Through YaST hardware configuration for IDE devices, I was able to change those settings to On.

I guess I got spoiled using YaST but I'm not seeing any app for manipulating the settings on the drive in Ubuntu. Does one exist? I found Device Manager but that doesn't really seem to allow me to change settings.

---

### Post by mark on 2004-10-27
[QUOTE=SFN]So it looks like the only problem you have is viewing DVDs, is that right?

I ran into a similar problem when I first installed SuSE. This same situation was coming up with both my CDROM and my DVDRW drives. Turns out the DMA settings were set to Off (which, WTF?). Through YaST hardware configuration for IDE devices, I was able to change those settings to On.

I guess I got spoiled using YaST but I'm not seeing any app for manipulating the settings on the drive in Ubuntu. Does one exist? I found Device Manager but that doesn't really seem to allow me to change settings.[/QUOTE]Dunno...it might be another **.conf* that needs to be edited.  Which I don't particularly mind, I just wish there was some kind of reference work somewhere - maybe a listing of common configuration files, with suggested hacks?

---

### Post by SFN on 2004-10-27
[QUOTE=mark]Dunno...it might be another **.conf* that needs to be edited.  Which I don't particularly mind, I just wish there was some kind of reference work somewhere - maybe a listing of common configuration files, with suggested hacks?[/QUOTE]
Hmm. I was just saying to somebody that if it came down to editing files I would probably go back to SuSE as I didn't really want to deal with that but the notion of a reference does make it attractive.

---

### Post by jdong on 2004-10-27
People trying to play dvds: **Do you have libdvdcss2 installed?**

---

### Post by mark on 2004-10-27
[QUOTE=jdong]People trying to play dvds: **Do you have libdvdcss2 installed?**[/QUOTE]Apparently not.  A search from Synaptic doesn't return anything, either (and I have universe/multiverse repos enabled).  Where would I find this lib?

Thanks,

Mark

---

### Post by calvinpriest on 2004-10-27
Add the following to your sources:
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

Then:
sudo apt-get update
sudo apt-get install libdvdcss2
sudo ln -s /media/cdrom0 /dev/dvd

There is a great multimedia how-to:
[http://www.ubuntuforums.org/showthread.php?t=94](http://www.ubuntuforums.org/showthread.php?t=94)

Calvin

---

