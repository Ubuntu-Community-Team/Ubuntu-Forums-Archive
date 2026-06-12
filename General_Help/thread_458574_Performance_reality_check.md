---
title: "Performance reality check"
date: 2007-05-29
forum: General Help
---

### Post by Freymish on 2007-05-29
](*,)I just installed 7.04 on an HP Omnibook XE3.  This machine has a 40GB drive, 512 MB RAM and a 1.0 GHz PIII M processor.  This is the first time I've used UBUNTU so I am unsure of what to expect in terms of performance.
There is a pretty noticable lag time when I click on buttons, open applications, and generally do anything.  This thing ran much faster using WinXP.  Are there any basic things I can do to troubleshoot this or is this to be expected given the hardware?

](*,)

Thanks,

Freymish

---

### Post by kilroy423 on 2007-05-29
Make sure and update all your drivers... I have a Hp DV 8300 2.16 Core Duo, 2GBs RAM, 100GB Hdd and ubuntu runs so much faster then xp and if that doesnt work then try 6.06

dan

---

### Post by scrooge_74 on 2007-05-29
probably some driver problem, did you leave enough space for the swap file?

---

### Post by Freymish on 2007-05-30
Good pointers both, thanks.  How might I go about finding out which driver/device is causing the problem?  I am totally new to this OS so I need a little hand holding I'm afraid.

---

### Post by eggdeng on 2007-05-30
I set up Edgy (6.10) on a PIII 666MHz 512MB. Everything works but it *is* sluggish. Firefox takes about 4-5 secs to open, openOffice about 12. With Beryl running, it's like wading through butter. You might just make sure DMA is enabled on the hard drive```
sudo hdparm -d /dev/hda1
``` (assuming your hard drive is hda1).

---

### Post by Freymish on 2007-05-30
There is a swap partition that's 256MB, but it doesn't seem to be getting used:  The System Monitor shows used swap as 0 bytes of 0 bytes and 205 MB of 495 MB of user memory.  

As for the DMA: --
sudo hdparm /dev/hda1

/dev/hda1:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 76694247, start = 63

---

### Post by dagrump on 2007-05-30
I could be all wet, but 0 of 0 means there is no swap. That would account for slug like speeds.

---

### Post by Freymish on 2007-05-30
That's why I put that in the post.  I ran the install again just to get a look at the partition table, since I don't know how to do it otherwise, and it showed that there was a swap partition.  But, as I said, it doesn't look as if it's being used.  Odd..

---

### Post by dagrump on 2007-05-30
I would try to manually partition the drive with about a gig for swap, but this means sitting thru a reinstall. Or if I remember correctly you can let it set up the partitions automagically, but I think it gives you excessive swap space. I'm sorry if I'm not much help.

---

### Post by merlinus on 2007-05-30
> 
There is a swap partition that's 256MB, but it doesn't seem to be getting used: The System Monitor shows used swap as 0 bytes of 0 bytes and 205 MB of 495 MB of user memory.


Maybe the UUID for it changed, for some reason.  

Entering blkid in a terminal and comparing the UUID for /swap with that in /etc/fstab might be helpful.

-merlin

---

### Post by kerry_s on 2007-05-31
i had the xe2, you should try xubuntu or the pure debian xfce4.

[http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso)

---

### Post by wirelessmonkey on 2007-05-31
This sluggishness often occurs when the video card driver is set to 'vesa', as opposed to its specific driver... i.e. nvidia, fglrx, etc.

---

