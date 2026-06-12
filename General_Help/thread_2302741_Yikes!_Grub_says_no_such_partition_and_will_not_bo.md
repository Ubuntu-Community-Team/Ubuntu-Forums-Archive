---
title: "Yikes! Grub says no such partition and will not boot!"
date: 2015-11-12
forum: General Help
---

### Post by rexyoung on 2015-11-12
Help!

I have a dual boot system with windows 10 and Ubuntu 15.10. The windows side started the windows 10.x upgrade today and  at some point attempted an automatic reboot.  That reboot failed. The error message says no such partition and then goes to grub rescue>

I was able to use a live Ubuntu cd to download and run boot repair which said it had repaired the error. Alas, it did not, much to my sorrow. 

It did, however, create a site with a printout of what my system is doing. It is located at [http://paste.ubuntu.com/13244016](http://paste.ubuntu.com/13244016). 

Can some kind (and knowledgeable) soul decipher that printout and tell me how to fix the problem?

---

### Post by yancek on 2015-11-12
Did this dual boot ever work?  What version of windows did you have before trying the upgrade to windows 10?  If you look at the boot repair output, there is no sign of Ubuntu or anything related to Linux other than the swap partition on sda5.  From that it appears your Ubuntu installation has been overwritten.  You get the grub rescue because there is minimal Grub boot code in the MBR (shown at the very top of the boot repair output) looking for the rest of the Grub boot files on the Ubuntu partition (sda6) and you can see by the listing of partitions that there is no sda6 partition.  You have about 432GB in the Extended partition (sda4) which is not being used so you can reinsall Ubuntu there, creating a partition while installing.

---

### Post by oldfred on 2015-11-13
You do show a large gap in your extended partition.

And Windows installs or upgrades rewrite partition table and "forget" to include the Linux partition. It has been a bug for years in all versions of Windows. And I am sure they are hard at work fixing it, to make it easier for users to dual boot.

       Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)#

---

### Post by rexyoung on 2015-11-13
Thanks, yancek and oldfred, for looking at this.

For over two years I have used the dual boot with ubuntu and, at first, windows 8 and 8.1, and then, since it came out in July, windows 10.  The upgrade which caused my problem was the mega upgrade released by windows yesterday which is supposed to upgrade windows 10 to windows 10.xxx.  So I suspect that there may well be others who run into this same problem....

In any event, it sounds like my best move now may be to reinstall ubuntu in hopes that it will recreate a proper grub environment allowing both windows 10 and ubuntu to coexist peacefully once again.  I've got backups for everything so that my only real loss will be the loss of time, not data.

Does that sound right to you guys?

---

### Post by oldfred on 2015-11-13
As long as you have good backups, that will work.
Always good idea to have backup.

But you can try parted rescue, just to see if it works. You know start & end sectors as start is just after start of extended partition and end is just before start of swap.

/dev/sda4       [COLOR=#ff0000]1,023,326,206[/COLOR] 1,953,503,999   930,177,794   f W95 Extended (LBA)
/dev/sda5       [COLOR=#ff0000]1,945,182,393[/COLOR] 1,953,503,999     8,321,607  82 Linux swap / Solaris

---

