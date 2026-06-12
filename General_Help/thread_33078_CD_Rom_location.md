---
title: "CD Rom location"
date: 2005-05-09
forum: General Help
---

### Post by DutchLau on 2005-05-09
Wow, I don't mean to completely sound noobie, but how do I find the location of my CD rom drive?

I have one DVD drive in my computer, that's all, but I don't know for sure if its cdrom, cdrom0, dvd, dvd0

What is a simple command/way to find this out,

Cheers,

DutchLau

---

### Post by RadioImp on 2005-05-09
Open a terminal and do:
ls /media

This will list the media directory. There will be two entries, one is probably 'cdrom' and the other is 'cdrom0'

cdrom is the mount point, cdrom0 is the device.

If you wish to get access files on the cd, the it is /media/cdrom
If you wish to mount the device, or access it directly, it would be /media/cdrom0

---

### Post by DutchLau on 2005-05-09
To be a little clearer, I'm trying to enable DMA on my DVD drive, which is taking AGES to read any audio CD that I want to rip. The Ubuntuguide ([http://ubuntuguide.org/#speedupcddvdrom](http://ubuntuguide.org/#speedupcddvdrom)) tells me to mount my DVD as /dev/cdrom , but will this also work if I just put /media/cdrom0 ?

Thanks,

DutchLau

EDIT: I'm trying to do it now, but I keep getting error messages:

> /dev/cdrom:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off) 

> /media/cdrom0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
discom@Discom:~$ sudo hdparm -d1 /media/cdrom 

What should I do, please help, it takes 20 minutes to rip an audio CD, although my computer is FAR FROM slow..  :-|

EDIT EDIT: I'm using sudo btw

---

### Post by RadioImp on 2005-05-09
Sorry, after doing a little bit of poking, looks like I was wrong, I got confused with my system having two DVD drives.

/media is where the cdrom is mounted.

/dev/cdrom should be the physical device, so in that command, /dev/cdrom should work.

---

### Post by RadioImp on 2005-05-09
Ah, just read your edit.

In that case try:
sudo umount /media/cdrom

and then run the hdparm command, once that is done, eject and reinsert the cd.

---

### Post by DutchLau on 2005-05-09
This is the error message I keep getting:

> discom@Discom:~$ sudo hdparm -d1 /dev/cdrom

/dev/cdrom:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off) 

I don't understand what's going on. What did you use to get DMA enabled?  :|

EDIT: I just read your 3rd reply, I'm trying it now  :razz:

EDIT EDIT: Now I'm getting a new error message  :-?  

> discom@Discom:~$ sudo hdparm -d1 /media/cdrom

/media/cdrom:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
discom@Discom:~$

EDIT EDIT EDIT: This is driving me nuts!  :roll:

---

### Post by RadioImp on 2005-05-09
Hmmm

Last idea:

Try taking the any CD's that might be in the drive out, this should sort the unmounting problem etc.

Then do
sudo hdparm -d1 /dev/cdrom

That exact command definitly worked on my system, other than that, I can't help.

---

### Post by DutchLau on 2005-05-09
Nope, that isn't working either. I'm thinking my DVD burner might not support DMA. I'm going to play around with the Bios to see if I can find anything interesting there. Other than that I'm dumbfounded.. :(

Now I can't really use the CD drive  ](*,) 

If anyone else could help, please do, and thanks RadioImp, I'm going to try over and over again. 

Cheers,

DutchLau

EDIT: I went into the BIOS and put the DMA mode to UDMA2 which is supported by the DVD drive, I'm still having the same problem though.

---

### Post by DutchLau on 2005-05-09
Here are some extra outputs that I have:

Output of hdparm -d /dev/hdc (My DVD location):

> 
root@Discom:/home/discom # hdparm -d /dev/hdc 

/dev/hdc:
using_dma = 0 (off)


So I tried doing this:

> 
root@Discom:/home/discom # hdparm -d1 /dev/hdc

/dev/hdc:
setting using_dma to 1 (on)
HDIO_SET_DMA failed: Operation not permitted
using_dma = 0 (off) 


What must I do to enable DMA? The output of hdparm -i /dev/hdc is as follows:

> 
root@Discom:/home/discom # hdparm -i /dev/hdc

/dev/hdc:

Model=HL-DT-ST DVDRAM GSA-4163B, FwRev=A102, SerialNo=K7351SB5729
Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
BuffType=unknown, BuffSize=0kB, MaxMultSect=0
(maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
PIO modes: pio0 pio3 pio4
DMA modes: mdma0 mdma1 mdma2
UDMA modes: udma0 udma1 *udma2
AdvancedPM=no
Drive conforms to: device does not report version:

* signifies the current active mode 

---

