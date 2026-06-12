---
title: "Need help with gparted, xp and unbutu"
date: 2006-11-18
forum: General Help
---

### Post by japc126 on 2006-11-18
I had Ubuntu and windows installed and living happily together. I decided to remove Ubuntu, so I removed it's partition with gparted and reassigned the space to my xp partition. Obviously (now) xp didn't started because grub had been removed, so i tried to reinstall Unbutu. I popped in the gparted live cd but now it won't let me reduce the size of my xp partition to install Unbutu, because it gives an error. The same happens with the Ubuntu cd. I tried to use my xp installation disk but it doesn't detec any hard disks.

The only solution I see now is to reformat my hard drive and lose a lot of important data, not only mine but of various family members.

Please help, I'm about to have a break down.

---

### Post by aidanr on 2006-11-18
the live cd should have some file system checking tools, open a console and do an fsck on that partition

also if all else fails, you can try mounting the partition from the live cd and copy important docs onto an external drive or something

---

### Post by japc126 on 2006-11-18
err how do i do that?

---

### Post by aidanr on 2006-11-18
not sure about the newer version of gparted (should be similar though) but on the version i have, i right click on the desktop, select aterm and then type in "fsck -r /dev/sda2" without the quotes

---

### Post by japc126 on 2006-11-18
first try:

fsck 1.39 (29-May-2006)
e2fsck 1.39 (29-May-2006)
fsck.ext2: Permission denied while trying to open /dev/sda2
You must have r/w access to the filesystem or be root

second try, using the sudo command before:

fsck 1.39 (29-May-2006)
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda2

---

### Post by aidanr on 2006-11-18
does that happen from the ubuntu live cd aswell?

---

### Post by jimbob on 2006-11-18
If I remember right if you have a Win98 floppy or a CD you should be able to get to an A:/ prompt and type in "fdisk /mbr" ( without the quotes ) to restore the Windows boot record.

Do a search in Ubuntu on '/mbr' - there is a lot of information on how to do it.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by moshuptrail on 2006-11-18
I bet fsck doesn't work for ntfs.  Remember, Ubuntu doesn't write to the proprietary file system.  Try dropping back to Windows to check the filesystem.  What you are looking for is bad blocks, but it won't hurt to defrag the drive a few times.

---

### Post by MrFSL on 2006-11-18
STOP!

Please God stop trying to defrag and fsck before you break something. ;) 

Look you need to repair your MBR. You can do this from your Windows install CD by booting from it and selecting the recovery console. From there you can type help for a list of commands. Then type ***<name of command> /?*** to find out how to use it. FIXMBR is a good place to start.

For another (I think simpiler) solution download [Ranish ]("http://www.ranish.com/part/") and boot from it. This is a great application that just displays your partition table and HDD information and allows you to edit it. You can set your Windows XP partition as active and also set the MBR to "Standard MBR" and you will be all straight.

Disclaimer... Read first then try to use tools to repair. Like all things, if used incorrectly you might damage your system.

---

