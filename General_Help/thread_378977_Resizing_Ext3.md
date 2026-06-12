---
title: "Resizing Ext3"
date: 2007-03-07
forum: General Help
---

### Post by KonoKanji on 2007-03-07
Well, I've been having a little bit of trouble.
I recently removed my Windows XP partition which was a 77.84 GB section of my 
Hard Drive, and only had about 27 GBs of space set up for Ubuntu; just expecting
 to experiment with it.
However, I've taken quite a shine to Linux in general.  So, after deleting the Windows 
partition, I went to expand the Ext3 partition I had Ubuntu running on (using the 
gParted on the Ubuntu LiveCD) but I could only make it smaller.

I know I have 77 GBs of unallocated space that is just waiting to be used.
So far I haven't found anything to help me by searching through the forums and
it's giving me a headache.

Is there any way I can expand it?

---

### Post by Kateikyoushi on 2007-03-07
This ext3 resize guide was written on edgy. [LINK]("http://www.howtoforge.com/linux_resizing_ext3_partitions")

---

### Post by Belyel on 2007-03-08
The ABSOLUTE easiest way to resize you partitions is to use the gParted live CD.  I just resized my Vista partition to allow Ubuntu more room to play using the gParted live cd, and it was effortless.  Don't believe people who say that you can't resize ext3.  It's simple: burn the image [found HERE ](http://gparted.sourceforge.net/livecd.php) to a CD, burn it slowly.  Then boot from the CD and use the graphical interface to find your drive and resize the partition.  Click "apply," wait and then boot back into linux.

---

### Post by KonoKanji on 2007-03-08
> **Belyel said:**
> The ABSOLUTE easiest way to resize you partitions is to use the gParted live CD.  I just resized my Vista partition to allow Ubuntu more room to play using the gParted live cd, and it was effortless.  Don't believe people who say that you can't resize ext3.  It's simple: burn the image [found HERE ](http://gparted.sourceforge.net/livecd.php) to a CD, burn it slowly.  Then boot from the CD and use the graphical interface to find your drive and resize the partition.  Click "apply," wait and then boot back into linux.

I actually have a burnt copy of that.
But when I gave it a try, and typed in 'startx', it gave me an error about
not being able to use xorg.conf properly.

Maybe if someone knew a way to get around that, I might be able to get it working.


But, just in case I can't get around that, I'm printing off Kateikyoushi's link to
resize it the hard way.

Thank you.

---

### Post by Kateikyoushi on 2007-03-08
What is your video card ?

---

### Post by KonoKanji on 2007-03-08
ATI Mobility x1400.

---

### Post by Kateikyoushi on 2007-03-08
It was tested on ubuntu live disc but worth a shot to try on gparted as well if works you can get to the gui. [LINK]("http://www.ubuntuforums.org/showpost.php?p=2193083&postcount=3")

---

### Post by KonoKanji on 2007-03-08
Well, I followed the 'How-to' completely and I got the space.  Only problem
is that I lost all my data along the way.  It's going to take a while to get
all of that back, but that's alright.  Everyone needs a new beginning, right?

Anyway, my personal experience with expanding the Ext3 system manually
didn't go as it should have, but I wish luck to anyone else who tries it.

Thanks for your help.

---

### Post by Kateikyoushi on 2007-03-08
Sorry about the lost data, in this light I won't recommend that route to anyone in the future.

I have to try it as well when feisty goes large, gparted cd works on my pc so have a better chance to succeed.

---

