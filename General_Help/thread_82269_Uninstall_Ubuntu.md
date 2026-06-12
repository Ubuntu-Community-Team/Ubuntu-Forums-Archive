---
title: "Uninstall Ubuntu"
date: 2005-10-26
forum: General Help
---

### Post by UniQe on 2005-10-26
I want to uninstall Ubuntu Breezy badger 5.10. How do i uninstall it??

I`ve tried to boot with the Windows XP and used the recovery console to fix the mbr, using the "fixmbr" command. But it says something like "Your partitions maybe unable to access". I dont want to destroy my windows partitions.
I have partition my hdd like this:

C: Windows, Programs, etc. (20,5 gb)
D: Movies, Music, etc. (~ 43 gb)
H: Experiment. My experiment hdd (8 gb)

I: Ubuntu Breezy badger (9,42 gb)
J: Swap file (~450 mb)

I dont want Ubuntu anymore. I dont want I: and J:... Can anyone help me??
And that fucking "GRUB loader" or what it is... I dont want it!

---

### Post by munkymonkjr on 2005-10-26
cool your bacon. I recommend first you boot up a livecd and repatition your drive via qtarted, gparged, or fdisk if you like text mode. then change G so its bigger or create a new partition if you will. Then clean your mbr and you shall be set. Better yet, reinstall windows, it will take care of everything.

---

### Post by Hallavej on 2005-10-26
He he he. Be VERY careful is my advice. I ones lost 40gb because i used winXP to manage my partition. Partition magic will do the trick, but it is not free.  *removed illegal software reference*.

---

### Post by UniQe on 2005-10-26
Cant i just run "fixmbr", and then erase my Ubuntu partition and repartition my hdd?? or will the GRUB loader not be erased??

God I really need help!

---

### Post by metoo on 2005-10-26
Sure, if you know how to operate fixmbr this would do it. Or use the repair from your windows CD. To clear the mbr was already answered before in this forum, search for it, I don't have the exact command. This will remove grub only.

For the Linux partitions: these are currently marked as Linux/swap in the harddisk partition table, so windows might not see them.

The repair/installer from the windows CD sees them, but this is risky. Use fdisk under windows or cfdisk from a Linux live CD to reset these to something that windows can access. W95 LBA is a good try when using cfdisk.
This is the tricky operation. With both tools, you can erase your windows partition as well...

Then you can re-format them from windows with either fat32 or ntfs.

If you want to combine the partitions to one again, delete them and re-create 1 big partition when beeing either in fdisk or in cfdisk, whatever you choose.

---

### Post by aysiu on 2005-10-26
Microsoft is more than happy to provide [instructions](http://support.microsoft.com/default.aspx?scid=kb;en-us;314458) for you.

---

### Post by UniQe on 2005-10-26
I have figured out an easy way, but i dont no if it will work.

First I fix the mbr using the "fixmbr" command in the recovery console on the windows xp cd. In windows, I erase the linux partitions using Norton Partition Magic. I guess I can repartition the free hdd space to extend an existing windows ntfs partition.

(Sorry for my bad english. i am 14 years old and comes from sweden.)

---

### Post by Moriak on 2005-10-26
When I need to delete a partition or fix the MBR for windows, I use [ranish partition manager]("http://www.ranish.com/part/"). 

If you can boot from a diskette you might want to give it a try. 

I recommend to create the partition using the OS installer (ubuntu installer or fdisk / windows installer). I had problems before when creating the partition with this software. But when the MBR is screwed, this is a nice little tools to put windows back in.

Hope this help

Jonathan.

---

