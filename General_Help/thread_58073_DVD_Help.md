---
title: "DVD Help"
date: 2005-08-18
forum: General Help
---

### Post by Rogue21121987 on 2005-08-18
I've seen a thread on DVD problems before but I can't find it so I'll just post here.

I'm getting this problem: The DVD recognises and plays except it is jumpy.  When I try to set dma to 1 this happens (When I try this with /dev/dvd or with /dev/cdrom I get the same result):

-------------------------------------------------------
rogue@DC1:~$ sudo hdparm -d1 /dev/hdd

/dev/hdd:
 setting using_dma to 1 (on)
 
HDIO_SET_DMA failed: Operation not permitted
 
using_dma    =  0 (off)

-------------------------------------------------------

When I edit hdparm.conf like this:

-------------------------------------------------------
command_line {
	hdparm -d1 /dev/hdd
}
-------------------------------------------------------

I get a "/dev/hdd: File or Folder not found"  on the next reboot.

System:
AMD 2000+
512MB RAM
Primary Master HDD = Windows XP
Secondary Master HDD = Ubuntu
Seconday Slave = LILITE-ON DVD SOHD-16P6P9S (DVD-Drive)

Note: 	-DVD Drive is definantly at /dev/hdd.
	-Using xine to play DVD. (Totem gets the first frame of the first menu and   then does nothing.

Any suggestions?  If I'm being stupid and missing something obvious please let me know...

---

### Post by buldir on 2005-08-18
Do a Google search using "HDIO_SET_DMA failed: Operation not permitted DVD" and you will find that it is likely that your chipset is not compiled into the kernel.

---

### Post by Rogue21121987 on 2005-08-18
](*,) 
Thanks

So how do I fix it?  Is it possible?  Or do I have to wait until the next kernal release?
Will buying a new DVD drive help?

<edit>Never mind, now that I actually read the posts I understand. 
[Good link](http://ubuntuforums.org/showthread.php?t=52842)

Thanks for not flaming me.

---

### Post by buldir on 2005-08-19
No flames here...there's already enough forest fires up here in Alaska.  OK, so it doesn't look promising without recompiling the kernel.  Folks who posted in the thread below mentioned this problem is resolved in the 2.6.12 kernel.  The last poster (emperor) got it to work after they recompiled the 2.6.11.11 from kernel.org.  Personally, I can live with only 4x (instead of 8x) burning speed for my external USB DVD burner until Breezy (next Ubuntu version) comes out.  If you feel brave, give it a whirl. 

[DVD DMA issue](http://www.ubuntuforums.org/showthread.php?t=35738&highlight=external+DVD+DMA)

---

