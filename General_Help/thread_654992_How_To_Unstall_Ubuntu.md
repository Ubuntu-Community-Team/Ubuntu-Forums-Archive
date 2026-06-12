---
title: "How To Unstall Ubuntu?"
date: 2007-12-31
forum: General Help
---

### Post by Xero117 on 2007-12-31
How do I unstall Ubuntu? I just want Windows XP until I get a bigger HD

---

### Post by -grubby on 2007-12-31
download [this]("http://gparted-livecd.tuxfamily.org/") and burn it to a CD (as an iso). Then,(after booting the CD up) using gparted (the hard drive partitioner) delete your ubuntu partition (which should be listed as ext3) and then resize your ntfs (XP) partition to be the full size of your hard drive. If these instructions are too vague for you, I'm sure another member will elaborate on it

---

### Post by forestpixie on 2007-12-31
sounds fine to me - same info I'd give

once you've done that use your windows disc to restore the mbr - although of course there are opensource alternatives to do that

---

### Post by tanman on 2007-12-31
Do you mean you want to keep XP and install Ubuntu. You would then have to create a dual boot system. I have done a couple of episodes on my podcast about this. Check out these episodes of the [MSC Giz Cast]("http://www.mscgizcast.com/")
Here is a right up I did Located[ [COLOR="Red"]here[/COLOR]]("http://www.msccompcasts.com/2006/07/installing-ubuntu.html").
Here is a video episode of installing Ubuntu [[COLOR="Red"]Video episode[/COLOR] #3]("http://www.mscgizcast.com/2007/11/msc-giz-cast-video-3-ubuntu-install.html")
I also have a video right on my site at [COLOR="Red"][MSC Comp Casts]("http://www.msccompcasts.com")[/COLOR]

---

### Post by tanman on 2007-12-31
Sorry disregard my post I miss read what you asked.

---

### Post by Canuckelhead on 2007-12-31
You'll need to use the recovery console on the win XP disk once you have removed Ubuntu.  From the console type FIXMBR

---

### Post by rsambuca on 2007-12-31
> **Canuckelhead said:**
> You'll need to use the recovery console on the win XP disk once you have removed Ubuntu.  From the console type FIXMBR

As an alternative, you can just install ms-sys run it prior to deleting your Ubuntu partition.  This will restore the MBR to the XP loader.  You can then use any utility to either delete the Ubuntu partition, or just reformat it to ntfs and use it as a separate media drive for XP.

```
sudo apt-get install ms-sys
```

---

### Post by forestpixie on 2007-12-31
#-o - ms-sys read about that yesterday and promptly forgot to write in on my pad of stuff to remember - thanks rsambuca

---

### Post by Xero117 on 2008-01-05
thanks guys :D

---

