---
title: "kjournald constantly accessing disk"
date: 2007-02-24
forum: General Help
---

### Post by billionmonkeys on 2007-02-24
I've got a myth box running edgy and a 2.6.19 kernel, and kjournald seems to access the disk constantly (the hd light flashes roughly 3 times per second when the system is idle)

here is an example: i did this:

echo 1 >/proc/sys/vm/block_dump
wait 12 seconds
echo 0 >/proc/sys/vm/block_dump

[ 6691.516770] kjournald(1813): WRITE block 710949504 on sda1
[ 6691.516781] kjournald(1813): WRITE block 709925704 on sda1
[ 6691.516786] kjournald(1813): WRITE block 709925632 on sda1
[ 6691.516790] kjournald(1813): WRITE block 709925712 on sda1
[ 6691.516988] kjournald(1813): WRITE block 197976 on sda1
[ 6691.516993] kjournald(1813): WRITE block 197984 on sda1
[ 6691.516996] kjournald(1813): WRITE block 197992 on sda1
[ 6691.516999] kjournald(1813): WRITE block 198000 on sda1
[ 6691.517003] kjournald(1813): WRITE block 198008 on sda1
[ 6691.517006] kjournald(1813): WRITE block 198016 on sda1
[ 6691.517009] kjournald(1813): WRITE block 198024 on sda1
[ 6691.517120] kjournald(1813): WRITE block 198032 on sda1
[ 6693.789685] kjournald(1813): WRITE block 710949504 on sda1
[ 6693.789698] kjournald(1813): WRITE block 709925712 on sda1
[ 6693.789704] kjournald(1813): WRITE block 709925632 on sda1
[ 6693.789891] kjournald(1813): WRITE block 198040 on sda1
[ 6693.789895] kjournald(1813): WRITE block 198048 on sda1
[ 6693.789899] kjournald(1813): WRITE block 198056 on sda1
[ 6693.789902] kjournald(1813): WRITE block 198064 on sda1
[ 6693.789977] kjournald(1813): WRITE block 198072 on sda1
[ 6696.037396] bash(7073): dirtied inode 4026531947 (block_dump) on proc

so you can see that kjournald is doing most of the disk activity.  Whats strange to me is that it seems to be writing the same blocks over and over, I've seen some of those blocks written multiple times in multiple instances of the above test.

So my questions:
- why does kjournald do this?  what is it doing?
- how do I make it stop?


many thanks for any help

---

### Post by chrisstankevitz on 2007-07-31
Me too,

---

### Post by hossa1c on 2007-12-05
hi,
I had the same problem. There is another thread that is very helpful

[http://ubuntuforums.org/showthread.php?t=613715](http://ubuntuforums.org/showthread.php?t=613715)

I found that I needed to add noatime to my /etc/fstab file, eg

UUID=409....b28 /  ext3   defaults,**noatime**,errors=remount-ro 0  1

This prevents the HDD being updated every time a file is read, which is what was happen before hand when you see kjournald constantly accessing the disk.

This helped a lot but didn't solve it completely. My HDD led was still flashing. Using ps -aux I tracked it down to (I've kept on stopping processes until the led stopped blinking)

 hald-addon-storage: polling /dev/scd0 (every 2 sec)

In the above thread is appears that the HDD led is also turned on when the IDE is used (eg accessing the cd rom). It doesn't seem to be accessing the HDD when this happens, so it wont affect HDD idle time. They suggested using the following line to stop this polling which turns on the LED  (Note: it also stops auto mounting of the CD ROM as well)

hal-disable-polling --device /dev/scd0

This stopped the blinking... mostly. There are still some processes that are writing to the HDD every 8-ish seconds, which does stop the HDD from entering sleep, but these are my required apps... I think.

All of this is explained much better in the above thread, you just need to read both pages.

hope this helps

Chris

---

### Post by atlfalcons866 on 2007-12-05
kjournaled is the journal driver for ext3. it is normal for it to write to the disk every 5 seconds.

---

