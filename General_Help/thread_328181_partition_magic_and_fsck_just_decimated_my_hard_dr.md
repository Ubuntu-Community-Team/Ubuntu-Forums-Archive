---
title: "partition magic and fsck just decimated my hard drive - help???"
date: 2006-12-30
forum: General Help
---

### Post by kerinin on 2006-12-30
I just added a new hard drive to my RAID array and tried to move some of my paritions foreward to make more room for my windows partition, using partition magic.  Partition magic got most of the way through moving the second partition and then crashed - i think it gave me an error about inode tables, but i'm not sure.

I rebooted, and grub gave me system error 17, so i booted into the 6.06 liveCD to see what was going on.  i started running fsck on the parition containing my /home folder, and it gave me a screenfull of errors saying something like 'short read', and asked if i wanted to 'force rewrite'.  i, stupidly, said yes, assuming that it knew what it was doing.  after a few thousand of these errors, i started getting paranoid and stopped fsck.

well it turns out (probably unsurprisingly to you guys who know what you're doing) that i was destroying the data on my home directory.  My question is - can i get it back?  has it been deleted permanently, or is there some utility i can use to reconstruct the drive.  I can mount the drive and access portions of the data - the directory structure seems to be intact, only some directories don't really exist when you try to go into them.

Please help - i have an enormous amount of very important information on this hard drive.

Thanks
-Ryan

---

### Post by Sef on 2006-12-30
Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").

Another one to check out is [Trinity Rescue Kit]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12").

Once you have fixed your problem or recovered you data, do this to change your partitions:

1) Do **not** use Partition Magic.  It and Linux do not always get along.

2) Use [GParted]("http://gparted.sourceforge.net") instead.  It is no cost and works great with Linux and other oses.

---

### Post by kerinin on 2006-12-30
Test disk doesn't want to play with my spanned RAID array - it tells me that the drive is too small because it isn't reading the other drive.  It also doesn't seem to do anything outside of checking the partitions.  My partitions are fine, it's the data on the partition thats messed up.

Trinity rescue doesn't seem to have anything that will help either - what i need is some way to either recover the files and delete the inodes or (preferably) reconstruct the inodes.  Is this even possible?  When fsck force-rewrote those inodes did it leave the data intact, and if so how can i get at it?

I agree about gparted vs partition magic, and i only use partition magic when i need to shift partitions.  gparted will expand partitions, but it won't let you move the start point.  In any case, i won't be using parition magic ever again.

should i just run fsck again and let it rewrite all the inodes?  will that put my files in the lost+found?

---

