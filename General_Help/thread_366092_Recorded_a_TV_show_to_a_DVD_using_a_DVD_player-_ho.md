---
title: "Recorded a TV show to a DVD using a DVD player- how to I import it as an mpeg??"
date: 2007-02-20
forum: General Help
---

### Post by billdotson on 2007-02-20
the contents of the DVD are the following.. there are two folders VIDEO_RM which contains VIDEO_RM.BUP;1  VIDEO_RM.DAT;1   VIDEO_RM.IFO;    and the other folder is VIDEO_TS which contains VIDEO_TS.BUP;1    VIDEO_TS.IFO;1   VIDEO_TS.VOB;1    VTS_01_0.IFO;1  and VTS_01_1.VOB;1

Is there anyway just to copy the video file off of the DVD as an mpeg?  

I am using a Sony DVD Player/Recorder that's hooked up to the TV.

---

### Post by annda on 2007-02-20
if it's not encrypted it might be enough to copy the VIDEO_TS folder.

otherwise you might need to rip the dvd.

---

### Post by dannyboy79 on 2007-02-20
> **billdotson said:**
> the contents of the DVD are the following.. there are two folders VIDEO_RM which contains VIDEO_RM.BUP;1  VIDEO_RM.DAT;1   VIDEO_RM.IFO;    and the other folder is VIDEO_TS which contains VIDEO_TS.BUP;1    VIDEO_TS.IFO;1   VIDEO_TS.VOB;1    VTS_01_0.IFO;1  and VTS_01_1.VOB;1

Is there anyway just to copy the video file off of the DVD as an mpeg?  

I am using a Sony DVD Player/Recorder that's hooked up to the TV.

I am guessing that you are not familar with dvd compliant format. Well, any dvd player needs this format in order to be able to play it. Actually most dvd's have AUDIO_TS and a VIDEO_TS folders. There is normally nothing within the audio folder.. You have .bup's, .vob's, and .ifo's.  Explained here:

VIDEO_TS.IFO, VTS_01_0.IFO - are configuration files with information about how to play exactly all video and audio content of DVD (including menus, subtitles, aspect ratio, languages etc.). 

VIDEO_TS.BUP, VTS_01_0.BUP - backup of configuration files. 

VTS_01_1.VOB, VTS_01_2.VOB, VTS_01_3.V0B, ... - files with video and audio data. 

You could just take the .vobs and click on them, I know my xbox (which has mplayer on it) can play them, but then when 1 vob ends you'll have to click on the next one so that wouldn't be the answer. You'll have to either rip it onto your hard drive using a couple different software or encode it into something else like mpeg files or avi files. Here are a few threads relating to this topic.

[https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs](https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs)

or  follow this to backup your dvd and then once on your computer do what you will

[http://kavlon.org/index.php/dvdbackup](http://kavlon.org/index.php/dvdbackup)

---

### Post by billdotson on 2007-02-20
I don't need a backup disc of it, I am using the recorder until I get my replacement WinTV-PVR-150 tuner.  I need to get the movie files into mpeg format.

---

### Post by dannyboy79 on 2007-02-20
ok wait, did you read it or just make some comment based on simply the title of the link??? If you had read it you would have seen that you can use this process to backup your dvd disc which will then turn into a .mpg file.

---

### Post by billdotson on 2007-02-20
I didn't see that in the link, I will check again though

---

### Post by billdotson on 2007-02-20
I tried the following things.. no help

sgtmattbaker@sgtmattbaker:~$ vobcopy -l
Vobcopy 0.5.14 - GPL Copyright (c) 2001 - 2004 [email]robos@muon.de[/email]
[Hint] All lines starting with "libdvdread:" are not from vobcopy but from the libdvdread-library

path to dvd: /dev/scd0

[Error] Path thingy didn't work '(null)'
[Error] Try someting like -i /cdrom, /dvd  or /mnt/dvd 
[Hint] By the way, you have 2 cdroms|dvds mounted, that probably caused the problem
sgtmattbaker@sgtmattbaker:~$ vobcopy -l
Vobcopy 0.5.14 - GPL Copyright (c) 2001 - 2004 [email]robos@muon.de[/email]
[Hint] All lines starting with "libdvdread:" are not from vobcopy but from the libdvdread-library

path to dvd: /dev/scd0

[Error] Path thingy didn't work '(null)'
[Error] Try someting like -i /cdrom, /dvd  or /mnt/dvd 
sgtmattbaker@sgtmattbaker:~$ vobcopy -l -n 2
Vobcopy 0.5.14 - GPL Copyright (c) 2001 - 2004 [email]robos@muon.de[/email]
[Hint] All lines starting with "libdvdread:" are not from vobcopy but from the libdvdread-library

path to dvd: /dev/scd0

[Error] Path thingy didn't work '(null)'
[Error] Try someting like -i /cdrom, /dvd  or /mnt/dvd 
sgtmattbaker@sgtmattbaker:~$ /mnt/dvd
bash: /mnt/dvd: No such file or directory
sgtmattbaker@sgtmattbaker:~$ vobcopy -l
Vobcopy 0.5.14 - GPL Copyright (c) 2001 - 2004 [email]robos@muon.de[/email]
[Hint] All lines starting with "libdvdread:" are not from vobcopy but from the libdvdread-library

path to dvd: /dev/scd0

[Error] Path thingy didn't work '(null)'
[Error] Try someting like -i /cdrom, /dvd  or /mnt/dvd 
sgtmattbaker@sgtmattbaker:~$ vobcopy -i
vobcopy: option requires an argument -- i
[Error] Wrong option.
Vobcopy 0.5.14 - GPL Copyright (c) 2001 - 2004 [email]robos@muon.de[/email]

Usage: vobcopy [-i /path/to/the/mounted/dvd/]
[-n title-number] 
[-o /path/to/output-dir/ (can be "stdout" or "-")] 
[-f (force output)]
[-V (version)]
[-v (verbose)]
[-v -v (create log-file)]
[-h (this here ;-)] 
[-I (infos about title, chapters and angles on the dvd)]
[-1/path/to/second/output/dir/] [-2/.../third/..] [-3/../] [-4 /../]
[-b <skip-size-at-beginning[bkmg]>] 
[-e <skip-size-at-end[bkmg]>]
[-O <single_file_name1,single_file_name2, ...>] 
[-q (quiet)]
[-t <your name for the dvd>] 
[-m (mirror)] 
[-F <fast-factor:1..64>]
[-l (large-file support for files > 2GB)] 
sgtmattbaker@sgtmattbaker:~$ vobcopy 
Vobcopy 0.5.14 - GPL Copyright (c) 2001 - 2004 [email]robos@muon.de[/email]
[Hint] All lines starting with "libdvdread:" are not from vobcopy but from the libdvdread-library

path to dvd: /dev/scd0

[Error] Path thingy didn't work '(null)'
[Error] Try someting like -i /cdrom, /dvd  or /mnt/dvd 
sgtmattbaker@sgtmattbaker:~$ vobcopy -i /media/SONY_DVD_RECORDER_VOLUME
[Hint] You use -i. Normally this is not necessary, vobcopy finds the input dir by itself. This option is only there if vobcopy makes trouble.
[Hint] If vobcopy makes trouble, please mail me so that I can fix this (robos@muon.de). Thanks
Vobcopy 0.5.14 - GPL Copyright (c) 2001 - 2004 [email]robos@muon.de[/email]
[Hint] All lines starting with "libdvdread:" are not from vobcopy but from the libdvdread-library
[Error] Could not find the provided path (/media/SONY_DVD_RECORDER_VOLUME), typo?

path to dvd: 

[Error] Path thingy didn't work '(null)'
[Error] Try someting like -i /cdrom, /dvd  or /mnt/dvd 
sgtmattbaker@sgtmattbaker:~$ vobcopy -i /media/scd0
[Hint] You use -i. Normally this is not necessary, vobcopy finds the input dir by itself. This option is only there if vobcopy makes trouble.
[Hint] If vobcopy makes trouble, please mail me so that I can fix this (robos@muon.de). Thanks
Vobcopy 0.5.14 - GPL Copyright (c) 2001 - 2004 [email]robos@muon.de[/email]
[Hint] All lines starting with "libdvdread:" are not from vobcopy but from the libdvdread-library
[Error] Could not find the provided path (/media/scd0), typo?

path to dvd: 

[Error] Path thingy didn't work '(null)'
[Error] Try someting like -i /cdrom, /dvd  or /mnt/dvd 
sgtmattbaker@sgtmattbaker:~$ vobcopy /media/scd0
Vobcopy 0.5.14 - GPL Copyright (c) 2001 - 2004 [email]robos@muon.de[/email]
[Hint] All lines starting with "libdvdread:" are not from vobcopy but from the libdvdread-library
[Error] Could not find the provided path (/media/scd0), typo?

path to dvd: 

[Error] Path thingy didn't work '/media/scd0'
[Error] Try someting like -i /cdrom, /dvd  or /mnt/dvd 
sgtmattbaker@sgtmattbaker:~$ vobcopy -l /media/scd0
Vobcopy 0.5.14 - GPL Copyright (c) 2001 - 2004 [email]robos@muon.de[/email]
[Hint] All lines starting with "libdvdread:" are not from vobcopy but from the libdvdread-library
[Error] Could not find the provided path (/media/scd0), typo?

path to dvd: 

[Error] Path thingy didn't work '/media/scd0'
[Error] Try someting like -i /cdrom, /dvd  or /mnt/dvd

---

### Post by dannyboy79 on 2007-02-20
ok, please let me see the output from ```
cat /etc/fstab
``` 
and ```
mount
``` Also please look in both the Device Manager and the Disks Manager and let me know what they report your dvd drive as being when you insert the dvd into it. make sure you look at them AFTER you insert the dvd and wait a sec until it is recognized and automounted. I am guessing it is /dev/scd0 but for some reason vobcopy isn't seeing a valid dvd structure which it ISN'T. you have a custom dvd structure which is probably why it's not working. well jsut post that output and we can go from there.
thanks

---

### Post by billdotson on 2007-02-20
sgtmattbaker@sgtmattbaker:~$ cat /etc/fstab
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


and now mount>

sgtmattbaker@sgtmattbaker:~$ mount
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-11-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb3 on /media/NTFS type ntfs (rw,nosuid,nodev,uid=1000,gid=1000,umask=077,iocharset=utf8)
/dev/sdb4 on /media/FAT32 type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)

---

### Post by dannyboy79 on 2007-02-20
well, did you try using /media/cdrom0? because that's were your dvd is being mounted. when I look at the mount command I don't see /media/cdrom0 there, did you insert the dvd first before doing mount?

---

### Post by artships on 2007-02-21
I use mplayer, or rather, the commandline ripper:

mencoder dvd://1 -dvd-device /dev/dvd  -oac copy -ovc copy -o '/media/video/movie.mpg'

Also of use might be the comand lsdvd

---

### Post by dannyboy79 on 2007-02-21
you know I was going to say that before. as corney as that sounds. but I figured that somehow the dvd could be played and then could be captured into a .mpg file. I thought this based on another technique using ffmpeg. glad you got it.

---

### Post by billdotson on 2007-02-21
I got vobcopy to work my doing vobcopy -i /dev/dvd but now I am going to try to actually convert it

---

### Post by dannyboy79 on 2007-02-22
you told us you didn't want to convert it??? you didn't need to use vobcopy then. you could have used several different guides. what do you want it to be in the end? .avi or what? are the files just vob files now what? you could have used use thoggen to rip the dvd into an avi file. or mencoder but that's used from the cli. or acidrip can rip a dvd as an avi file. I didn't bring any of this up because you specifically said you didn't want to convert it, I thought that's what you said or maybe I misread something. or I believe avidemux would work.

---

### Post by dannyboy79 on 2007-02-22
> **billdotson said:**
> I got vobcopy to work my doing vobcopy -i /dev/dvd but now I am going to try to actually convert it

I wonder why /dev/dvd worked?  did you do this when the dvd was NOT mounted? you know the vobcopy website specifically stated that it's not a good idea to use the /dev/ location  but I suppose if you got it to work than you're ok. you were suppose to use the mount location instead.


straight from the website ([http://lpn.rnbhq.org/projects/c/c.shtml):](http://lpn.rnbhq.org/projects/c/c.shtml):)
But using /dev/dvd with umounted dvd also works (but has some drawbacks and is NOT recommended!).

---

