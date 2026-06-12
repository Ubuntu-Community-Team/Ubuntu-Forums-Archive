---
title: "can I use vobcopy to transcode into something other than .mpg?"
date: 2007-02-23
forum: General Help
---

### Post by billdotson on 2007-02-23
I installed vobcopy, transcode, and the other applications needed to copy the video off of a DVD so I can get the TV shows I recorded using my dvd recorder into a video format I can edit and cut out commercials.

The only way I have transcoded is:
tcextract -i movie1-1.vob.partial -t vob -x mpeg2 > movie.m2v
tcextract -i movie1-1.vob.partial -t vob -x ac3 -a 0 > movie.ac3

can I the audio and video into different formats and put them back together lie I can do with mpeg2 and ac3?   Like convert the video to avi and the sound to mp3 or the video to xvid and the sound to ogg?

---

### Post by watermark on 2007-02-23
Look into acidrip and/or dvdrip.  There are packages in the universe repositories I think.

---

### Post by billdotson on 2007-02-23
acidrip always messes the audio up in the output files vobcopy and transcode does not.

---

### Post by billdotson on 2007-02-23
well actually right now I cannot even get acidrip to find the DVD.  the default for acidrip is /dev/dvd and it says "no DVD found.. is there a DVD in the drive?" My fstab looks like this

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

I have tried /dev/hda and it says that that is not a valid DVD drive.

---

