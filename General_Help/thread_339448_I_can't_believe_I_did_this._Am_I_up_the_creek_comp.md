---
title: "I can't believe I did this. Am I up the creek completely?"
date: 2007-01-15
forum: General Help
---

### Post by DarkStarAeon on 2007-01-15
Ok, so I had a successful and happy running dual boot of xp and ubuntu for awhile, then, for some unknown reason I thought I could remove the windows partition and give that space to the ubuntu partition via gparted. (Yeah, I know, stop laughing.)

So, I removed the Windows partition and tried to give that free space to Ubuntu, then all at once my senses came back to me and I realized I couldn't do this in the way I was doing it. Unfortunately, it was to late at that point.

Now, Ubuntu still loads up fine, I'm on it now typing this, and the swap is still there too. But the partition formerly known as windows is gone and has been switched from ntfs to ext3 and sits completely empty. (hda1)

So, before I go and painfully start all over, is there any way to either give this free space to the Ubuntu parition (hda2) or perhaps make it like a second drive for Ubuntu...or something else that doesn't involve having to start all over from scratch?

You may ridicule me at will, I deserve it, but try and help me out here with some ideas as you do it ;)

---

### Post by Sef on 2007-01-15
Get [GParted]("http://gparted.sourceforge.net").  It's a graphical partitoner.

---

### Post by DarkStarAeon on 2007-01-15
ALready got it, that's what I used. It won't let me increase the size of the already existing Ubuntu partition.

---

### Post by Nonno Bassotto on 2007-01-15
I can't understand what wrong in what you did. Can you explain the issue in more detail?

---

### Post by ardchoille42 on 2007-01-15
If it were me, I'd just use gparted to format that partition as ext3 (or your choice) and use it as a second drive.. for storage or files or something. This can easily be done and you don't need to start all over.. unless you absolutely want that space combined into the main Ubuntu system.

---

### Post by DarkStarAeon on 2007-01-15
Basically, I opened GParted, deleted the Windows partition, then tried to give the space to the Ubuntu partition, but it won't let me do it. I can only make them smaller or delete them, not make one grow. The Windows partition was ntfs, now it's ext3, and it's empty, and I want to give that space to the Ubuntu partition, but I can't.

Not really sure how else to say it, let me know if you need certain technical info.

---

### Post by DarkStarAeon on 2007-01-15
> **ardchoille42 said:**
> If it were me, I'd just use gparted to format that partition as ext3 (or your choice) and use it as a second drive.. for storage or files or something.


It is formatted as ext3, and I would like to do just what you said, how do I make it show up as a second drive?

---

### Post by Nonno Bassotto on 2007-01-15
Ok, now I read your reply. Well, you can create a new partition and use it under linux. How is it you hard disk partitioned? If you have just one partition, you may consider moving your home to the new partition. Otherwise you could create a new swap partition, delete the current one, in order to have the free space contiguous to your linux partition, and the expand your linux partition.

Whatever you choose: backup, Backup, BACKUP!!!

If you need more details, just ask me. Anyway post here the exact order of your current partitions.

---

### Post by aragorn2909 on 2007-01-15
Can't you just boot from a live cd,  and use gparted or qtparted to resize your linux partition?  I've never tried myself, so I don't know if that would work.

A.B.

---

### Post by Nonno Bassotto on 2007-01-15
Maybe I wasn't clear. I think the issue at hand is that the free space is not adiacent to your ubuntu partition, maybe because there is the swap in the middle.

---

### Post by tribaal on 2007-01-15
Well the surest way to use your now unused partition is to mount it somewhere in your directory tree.

Just add an entry to your /etc/fstab file like the following:

```
/dev/hda1    /mnt/newdrive    ext3    defaults    0    0
```

And reboot your machine. You should now have your empty space available in /mnt/newdrive
Of course, feel free to mount it anywhere else :)

Be careful not to mount it on somthing that already contains data though, since it would make your data inaccessible :(

Hope this helps :)

- trib'

---

### Post by DarkStarAeon on 2007-01-15
hda1 is ext3 and is empty, it was the windows partition (it was ntfs before though)
hda2 is ext3 and is the Ubuntu partition
hda3 is swap

I think I got that right?

I'm not new to linux, but new to Ubuntu, and this is my first time playing with partitions. Sadly, I got the dual boot thing working the first time perfectly, but can't figure out how to change such things as I've described.

So how can I make that hda1 another drive, it's already set up, just empty.

---

### Post by DarkStarAeon on 2007-01-15
> **tribaal said:**
> Well the surest way to use your now unused partition is to mount it somewhere in your directory tree.

Just add an entry to your /etc/fstab file like the following:

```
/dev/hda1    /mnt/newdrive    ext3    defaults    0    0
```

And reboot your machine. You should now have your empty space available in /mnt/newdrive
Of course, feel free to mount it anywhere else :)

Be careful not to mount it on somthing that already contains data though, since it would make your data inaccessible :(

Hope this helps :)

- trib'

Thanks, but I'm noticing in /etc/fstab things look odd. Like it doesn't register that I made changes in gparted. Should I post it up here for you guys to look at?

---

### Post by DarkStarAeon on 2007-01-15
> **aragorn2909 said:**
> Can't you just boot from a live cd,  and use gparted or qtparted to resize your linux partition?  I've never tried myself, so I don't know if that would work.

A.B.

Tried that too.  :(

---

### Post by DarkStarAeon on 2007-01-15
I screwed that up, tried to edit the fstab file, rebooted, got endless errors, then by the grace of the computer gods it let me back in and booted up finally.

Ok, so rather than me continue to screw this up, can anyone tell me how to fix this below?

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=d830afde-72f1-46bc-8ab1-185dfc263ba5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=BA907264907226D3 /mount/hda1     ext3    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=150f9d4e-8e1e-4987-bb1f-1fefe1e59ef7 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

I appreciate the help guys :)

---

### Post by gralbe on 2007-01-15
You're not going to be able to enlarge a partition with another partition that doesn't follow directly after the partition you want to enlarge, but I think you've gathered that at this point. If you are using LVM you could actually do it, but I'm going to assume you aren't.

(BTW, I'm not claiming to be an expert at any of this)

For your fstab... the last entry for the floppy looks odd. Certainly, your floppy drive device isn't sitting at "/dev/". I would start by commenting that entry out. Was the system giving you specific errors? (The floppy entry shouldn't cause any actual boot errors because it's set noauto). 

Did you edit the entry for /dev/hda1? If so and if it's related to the errors you got at bootup, I would replace "UUID=BA907264907226D3" with "/dev/hda1". The UUID, I believe, is almost voodoo and the changes you've made to the partition have probably changed it's appearance to the OS. /dev/hda1 is pretty generic and the OS can cope with that.

-g

---

### Post by jonny on 2007-01-19
As you've discovered, you can't resize and move all types of filesystems.  That gives you three choices:

1. Leave things as they are at least your computer is usable

2. Backup your Linux partition to a second disk, possibly an external USB drive.  Then use a live CD to delete the two partitions that you want to merge, create a new partition in the empty space and format it with an EXT3 file system.  Then use the live CD to restore your Linux system into the new, larger partition.  This is the best approach but it's the most complicated.

3. Mount the empty EXT3 filesystem somewhere where you can easily save data to it.  Note that, unlike Windows, Linux has no concept of drives (c:, d:, etc).  All drives hang off the same filesystem and it's up to you where you mount them.

---

