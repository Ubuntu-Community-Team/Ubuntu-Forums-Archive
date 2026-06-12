---
title: "questions on Grip and mounted partitions"
date: 2005-04-12
forum: General Help
---

### Post by george29 on 2005-04-12
Hello all,

I've just upgraded to Hoary, (from warty) and have been setting my new system up, getting everything working the way i want. I have a couple of questions.

1, when i use Grip to rip MP3 files from a CD - how do i get a track number assigned to the file? 

2. I've mounted my Windows NTFS (i know i'm still dual booting  [-X  but i've not managed to work out how to play COD using cedegaCVS yet) and a FAT32 partition using the [http://ubuntuguide.org/](http://ubuntuguide.org/) guide which has proved very useful. However in Warty when i mounted the partition in my /etc/fstab file they would show up with icons in 'computer' (just like the filesystem icon) - does anyone know how to get this to happen in hoary? I can access via /media/windows....etc... but would like to have individual icons.

thank you to any one who can help. 
and to all those of you who've written how to's and posted them - they've been invaluble in helping me (almost) make the switch from windows to linux. now if i could just sort out the gaming....

George

---

### Post by astoltz on 2005-04-12
in Grip, go to the config tab, then the Encode tab.  Look for the entry in Encode file format - it should have something like ~/mp3/%A/%d/%n.%x.  All those % things are switches for different parts of the file name.  %n is the name of the track for example.  for the track number, you want %t.  It's all in the help file - have a look.

---

### Post by george29 on 2005-04-13
thanks astolz, hadn't read far enough in the manal, sorry.

by the way do you have any idea how to increase the ripping speed?

I've tried disable paranoia, setting DMA on for my dvd drives, using scsi emulation, for one cd i managed to get grip to rip at about 10X, but now it only seems to rip at about 2X?

thanks 
George

---

