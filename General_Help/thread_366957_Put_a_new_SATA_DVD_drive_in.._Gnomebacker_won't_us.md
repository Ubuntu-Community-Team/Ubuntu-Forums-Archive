---
title: "Put a new SATA DVD drive in.. Gnomebacker won't use it now"
date: 2007-02-21
forum: General Help
---

### Post by billdotson on 2007-02-21
I put a DVD+RW in the drive and hit format DVD+-RW in Gnomebaker and I got the following error:

* DVDÂ±RW/-RAM format utility by <appro@fy.chalmers.se>, version 6.1.
* 4.7GB DVD+RW media detected.
umount: /media/dvdrecorder is not in the fstab (and you are not root)
:-( unable to proceed with format: Device or resource busy

here is the contents of my /etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=c51e7206-7183-4cee-b79f-142eb72cbc1b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb2
UUID=1e0d2ef5-41dc-4288-8518-4814ecc5c585 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

So I went to /etc/fstab and added the following:

/dev/hdc        /media/dvdrecorder   udf,iso9660 user,noauto     0       0 

and I also tried /dev/sd0 (zero)

Then I tried to format again and I got this error

* DVDÂ±RW/-RAM format utility by <appro@fy.chalmers.se>, version 6.1.
* 4.7GB DVD+RW media detected.
umount: /media/dvdrecorder mount disagrees with the fstab
:-( unable to proceed with format: Device or resource busy

I am also having issues telling vobcopy where to go and it is very hard because I have to open the contents of the DVD and then tell vobcopy to look and it only works half the time.  

 I also have another DVD drive but it seems to be working because I think I installed Ubuntu with it in where as the SATA DVD drive I added afterwards.  

Thanks.

---

### Post by billdotson on 2007-02-21
I think I fixed it I set the DVD drives as 

/dev/hda /media/dvd0 udf,iso9660 user,noauto 0 0
/dev/hdb /media/dvd1 udf,iso9660 user,noauto 0 0

and it seems to work

---

### Post by dannyboy79 on 2007-02-22
could you maybe clarify as to why you think you got it solved, all sata drives use the scsi emulation I am pretty sure so they will always be sdx instead of hdx. also, mount points are really not important, you can mount a device in any folder you want! so by simply changing a fstab entry from /media/cdrom0 to /media/dvd0, all you really did was instead of the dvd's contents being shown in the folder /media/cdrom0, they'll now show up in /media/dvd0. Plus, you're making it look as though you have 3 optical drives. 1 on hda, 1 on hdb, and now this new sata interface optical drive. why don't you do this code
```
dmesg | grep DVD
```
and see what it says, this is what mine says:

daniel@UBUNTU:~$ dmesg | grep DVD
[17179581.920000] hda: Optiarc DVD RW AD-7170A, ATAPI CD/DVD-ROM drive
[17179582.988000] hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)

so it should tell you what your drives are being referred to by /dev

good luck.

---

### Post by billdotson on 2007-02-22
well now it is not working

while in ther terminal typing "vobcopy -l" this happens:

sgtmattbaker@sgtmattbaker:/$ vobcopy -l
Vobcopy 0.5.14 - GPL Copyright (c) 2001 - 2004 [email]robos@muon.de[/email]
[Hint] All lines starting with "libdvdread:" are not from vobcopy but from the libdvdread-library

path to dvd: /dev/scd0

[Error] Path thingy didn't work '(null)'
[Error] Try someting like -i /cdrom, /dvd  or /mnt/dvd 
sgtmattbaker@sgtmattbaker:/$ 

I then set my /etc/fstab to the default (plus the automount for the Windows drive) here is my new /etc/fstab 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=c51e7206-7183-4cee-b79f-142eb72cbc1b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb2
UUID=1e0d2ef5-41dc-4288-8518-4814ecc5c585 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1    /home/sgtmattbaker/Windows_NTFS ntfs  nls=utf8,umask=0222 0    0

After that I put the DVD in my SATA DVD drive and got this message after typing vobcopy:

sgtmattbaker@sgtmattbaker:~$ vobcopy 
Vobcopy 0.5.14 - GPL Copyright (c) 2001 - 2004 [email]robos@muon.de[/email]
[Hint] All lines starting with "libdvdread:" are not from vobcopy but from the libdvdread-library

path to dvd: /dev/scd0
name of dvd: SONY_DVD_RECORDER_VOLUME
[Error] Can't open VMG info.
sgtmattbaker@sgtmattbaker:~$ vobcopy -l
Vobcopy 0.5.14 - GPL Copyright (c) 2001 - 2004 [email]robos@muon.de[/email]
[Hint] All lines starting with "libdvdread:" are not from vobcopy but from the libdvdread-library

path to dvd: /dev/scd0

[Error] Path thingy didn't work '(null)'
[Error] Try someting like -i /cdrom, /dvd  or /mnt/dvd 

and then again   

sgtmattbaker@sgtmattbaker:~$ vobcopy 
Vobcopy 0.5.14 - GPL Copyright (c) 2001 - 2004 [email]robos@muon.de[/email]
[Hint] All lines starting with "libdvdread:" are not from vobcopy but from the libdvdread-library

path to dvd: /dev/scd0

[Error] Path thingy didn't work '(null)'
[Error] Try someting like -i /cdrom, /dvd  or /mnt/dvd 
sgtmattbaker@sgtmattbaker:~$ 

Then I tried it by putting the DVD in the IDE drive and typed vobcopy and this happened:
 sgtmattbaker@sgtmattbaker:~$ vobcopy 
Vobcopy 0.5.14 - GPL Copyright (c) 2001 - 2004 [email]robos@muon.de[/email]
[Hint] All lines starting with "libdvdread:" are not from vobcopy but from the libdvdread-library

path to dvd: /dev/hda
name of dvd: SONY_DVD_RECORDER_VOLUME
[Error] Can't open VMG info.
sgtmattbaker@sgtmattbaker:~$

---

### Post by dannyboy79 on 2007-02-22
apparently you're not reading what I am posting. I can't help you unless you help me help you. and this goes for any time you want help in the future from others as well. when some1 asks for output in order to help you, you should provide it if you want that persons help. so again, please post the output from 
```
dmesg | grep DVD
```
maybe I didn't ask for it, but I did suggest looking at this and if you did than you should've posted what it said so I can see what it says so that I can help you further. also, I am starting to beleive that since this disc was created by a sony dvd recorder, that it won't be able to be read by vobcopy because of it's dvd structure isn't the same as a normal dvd structure of having a video_ts and a audio_ts. I thought I already said this once but you posted in that other thread that you got it figured out??? have you tried acidrip and the others that I suggested in your other thread? I just can't believe that ubuntu is labeling a sata drive as /dev/hda, I thought it would be /dev/scd0. post back if ytou want any more input from me and please stop pm'ing me when you post back, I am notified as it is via email when the thread is updated.

---

