---
title: "format a memory card"
date: 2008-03-22
forum: General Help
---

### Post by skydiver|goose on 2008-03-22
I have a 2GB mirco SD card that I use with my mobile to store all my pictures, videos, and other fun stuff. I plugged the chip into my friend's phone to transfer him a ringtone, and his phone locked the memory card up and corrupted and destroyed all my files so that they all have strange filenames/format extensions and I can't write to the card, only read it.

How can I format the card so that I can use it again?

---

### Post by ibuclaw on 2008-03-22
Hi, give me a minute to find my phone (so I can try this out).
But the program you'll want would be "gparted" and (I'll have to check with my card) the file format the card should be partitioned to a normal fat partition. (not fat32)

Regards
Iain

---

### Post by Sef on 2008-03-22
> But the program you'll want would be "gparted" and (I'll have to check with my card) the file format the card should be partitioned to a normal fat partition.

A link to [GParted]("http://gparted-livecd.tuxfamily.org/").

---

### Post by skydiver|goose on 2008-03-22
do I apt-get gparted?

---

### Post by ibuclaw on 2008-03-22
Yes, you can "apt-get install gparted"
And the format would be "FAT16".

[EDIT]
Though perhaps using gparted on a live CD is safer?
Confirmation needed, though I have used it happily on ubuntu.
[/EDIT]

And you should have no trouble finding the disk in gparted, it should be at the bottom of the list of partitions and,  the only one with a 2GB space. (or in my case, the 950ish MB)
[[IMG]http://img229.imageshack.us/img229/7135/screenshotdevsdagpartedcv8.th.png[/IMG]](http://img229.imageshack.us/my.php?image=screenshotdevsdagpartedcv8.png)

---

### Post by skydiver|goose on 2008-03-22
when I can get my apt-get to work, I'll try it. thanks man!

---

### Post by ibuclaw on 2008-03-22
Cool! Now that is sorted, hows the program going?

If you have any questions, or are scared to do something that you'll regret, just ask or post a screenshot to show me what you are attempting to do!

Regards
Iain

---

### Post by skydiver|goose on 2008-03-22
yeah.. what do I do from here?

Screenshot attached:

---

### Post by ibuclaw on 2008-03-22
Okay, from left to right, try to spot this:
> 
| New  Delete | Resize/Move | Copy  Paste | Undo  Apply | /dev/hda (74.53GB) |

Click on the "/dev/hda" button, and a tab will drop down.

Your card should be the "/dev/hdb" partition if you have 1 hard-drive in your computer. "/dev/hdc" if you have two. Either way it should be the one at the bottom.

If you are confused still, look at my previous image again, as I'm doing it there.

---

### Post by skydiver|goose on 2008-03-22
okay, so this is what I need to format, correct?

---

### Post by ibuclaw on 2008-03-22
I don't have a card reader, so I'm currently plugged in through the phone, hence why my partition is "unallocated". But yours shouldn't be.
[[IMG]http://img369.imageshack.us/img369/4910/screenshotuo1.th.png[/IMG]](http://img369.imageshack.us/my.php?image=screenshotuo1.png)

So, simulating it on my phone disk drive, first thing to do when you find it, is to unmount it. Notice the mountpoint of the partition. Take care into looking that that mountpoint is correct to the SD disk you have inserted.
[[IMG]http://img526.imageshack.us/img526/2827/screenshot1rd0.th.png[/IMG]](http://img526.imageshack.us/my.php?image=screenshot1rd0.png)

Once the drive has unmounted, you can now reformat it.
[[IMG]http://img99.imageshack.us/img99/8459/screenshot2cp7.th.png[/IMG]](http://img99.imageshack.us/my.php?image=screenshot2cp7.png)

Now you have selected the partition format you want, click Apply.
[[IMG]http://img176.imageshack.us/img176/2602/screenshot3dm5.th.png[/IMG]](http://img176.imageshack.us/my.php?image=screenshot3dm5.png)

If your phone doesn't seem to read fat16 card, give fat32 a try.

If you can't find your device, make sure that it is inserted into the card reader before you start gparted.

That I think is all covered,

Regards
Iain

[EDIT]
Yes, by the looks of that you must format it to fat32.

---

### Post by skydiver|goose on 2008-03-22
much thanks!

[edit]

It won't stop scanning for devices..

---

### Post by ibuclaw on 2008-03-22
Can the phone read/write to the SD card?

Can Ubuntu read/write to the SD card?

If the two above questions are yes, just close the App, no worries.

Regards
Iain

---

### Post by skydiver|goose on 2008-03-22
neither of them can

---

### Post by ibuclaw on 2008-03-22
Oh dear,
Have you rebooted Ubuntu? Take the SD Card out first before you do and insert back in when the gdm login screen comes up.

open the terminal and enter:
```
 lsscsi 
```

If terminal echos back that the command isn't found, you'll need to install it ("apt-get install lsscsi")

If your SD Card isn't at the bottom of the list, then this may be beyond me.
To be honest, I've tried this on similar devices with no problems.

---

### Post by ibuclaw on 2008-03-22
I've looked up a bit:

```

sudo -s
umount /dev/sda1
mkfs.vfat /dev/sda1

```

Is how to do it in the console.

Maybe worth a shot...

---

### Post by skydiver|goose on 2008-03-22
just got to work. I'm working on it...

---

### Post by skydiver|goose on 2008-03-22
gparted won't read it unmounted, and terminal won't do it

---

### Post by cherva on 2008-03-22
I have the same problem with 2GB SD card and whatever I do she is read only ... I format it with  mkfs.vfat /dev/sdc1 but after that gparted says that the space is unalocated and even that the space is 1gb only ....

---

