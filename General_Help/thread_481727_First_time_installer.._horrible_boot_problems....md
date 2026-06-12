---
title: "First time installer.. horrible boot problems..."
date: 2007-06-22
forum: General Help
---

### Post by Mavosa on 2007-06-22
No matter how much I searched, I could not find anything to help fix this problem.. so any help would be appreciated.

I have a really hard time getting my old windows xp partition to boot anymore after installing ubuntu for the first time. I had installed the latest Ubuntu off the live-cd and installed it in this hdd configuration:

/dev/sda1 - ntfs main windows xp partition

/dev/sda2 - extended

/dev/sda5 through 9 all logical storage drives for personal files

/dev/sda11 - linux ext3 for the ubuntu install

/dev/sda10 - linux swap

Created the linux partitions at the end of the hdd, however at the end of the ubuntu install, I installed grub to the /dev/sda1 partition. This caused my windows xp partition to be unreadable under linux, however it is able to read my other ntfs logical partitions no problem. I believe installing grub had corrupted the MBR, however I am confused if fixing the MBR would fix the problem. I am almost considering to ghost my original windows partition, however I would definitely like to save it and make it bootable again. I'm afraid grub had corrupted my windows partition, I would want to know if there would be any way to revert this to make the windows partition work again.

I don't have much linux experience, so please explain everything by step by step if possible, and also link anything of interest if it would be able to help fix my problem. I would post my grub configuration file information, however I don't even know how to access the terminal under the ubuntu dist or how to even retrieve the information.

I will greatly appreciate any help!

---

### Post by merlinus on 2007-06-22
```

cat boot/grub/menu.lst

```You might also post this:

```

cat /etc/fstab

```

and this:

```

sudo fdisk -l

```

(l is a lowercase L)

-merlin

---

### Post by Mavosa on 2007-06-22
> **merlinus said:**
> ```

cat boot/grub/menu.lst

```You might also post this:

```

cat /etc/fstab

```

and this:

```

sudo fdisk -l

```

(l is a lowercase L)

-merlin

This is the live cd since I cannot boot into either partition anymore...

cat boot/grub/menu.lst does not find the file

cat /etc/fstab results:
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda10 swap swap  defaults 0 0

Disk/dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38813 cylinders
Units = cylinders of 16865 * 512 = 8225288 bytes

   Device     Boot      Start       End               Blocks      Id    System
/dev/sda1    *               1        680        5462068+      7     HPFS/NTFS
/dev/sda2                 681    38913    307106572+      5     Extended
/dev/sda5                 681      2543        14964516       7     HPFS/NTFS
/dev/sda6               2544      4329      14346013+      7     HPFS/NTFS
/dev/sda7               4330      7297      23848428+      7     HPFS/NTFS
/dev/sda8               7298    35442      226074681       7    HPFS/NTFS
/dev/sda9             35443    36231          6337611       7    HPFS/NTFS
/dev/sda10           38671    38913          1951866      82   Linux Swap /Solaris
/dev/sda11           36232    38670        19591236      83   Linux

---

### Post by Mavosa on 2007-06-22
I found my menu.lst just now: results:

title  memtest86+
root(hd0,0)
kernal /boot/memtest86+.bin

---

### Post by merlinus on 2007-06-22
Except for sudo fdisk -l, these results are not from your hard disk ubuntu installation but from the RAM that the live cd runs in.

You might try SuperGrub:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

That way you can probably access your ubuntu partition, and maybe even restore or reinstall grub.

-merlin

---

### Post by Mavosa on 2007-06-22
Thats what I figured when I saw the results, thank you for the link I will try it out, hopefully it will restore everything to normal.

---

### Post by louieb on 2007-06-22
> **Mavosa said:**
>  I installed grub to the /dev/sda1 partition.
I hope that was a typo and you meant /dev/sda11. That would have put the GRUB pointer in the boot sector of you Linux partition.
To  change the MBR of the drive to GRUB you would have to use /dev/sda
By installing the GRUB pointer to /dev/sda1  you have overwritten the boot sector of your win partition. 
If what I think is right your drives MBR is untouched. Its you win partitions boot sector that needs fixed. Believe your going to need an XP CD and run fixboot from it in order to get windows back. 

after you get windows to boot you will need to reinstall GRUB only this time you need to install its pointer in the MBR of the drive. or get another boot loader/manager.

---

### Post by Mavosa on 2007-06-23
> **louieb said:**
> I hope that was a typo and you meant /dev/sda11. That would have put the GRUB pointer in the boot sector of you Linux partition.
To  change the MBR of the drive to GRUB you would have to use /dev/sda
By installing the GRUB pointer to /dev/sda1  you have overwritten the boot sector of your win partition. 
If what I think is right your drives MBR is untouched. Its you win partitions boot sector that needs fixed. Believe your going to need an XP CD and run fixboot from it in order to get windows back. 

after you get windows to boot you will need to reinstall GRUB only this time you need to install its pointer in the MBR of the drive. or get another boot loader/manager.

That's exactly what happened. I couldn't fix the mbr for the life of me, I just simply deleted the windows partition and restored from a ghost image. I am pointing grub to install to /sda11 for now, I may have to setup windows' boot.ini to boot into linux, I'm not sure as to what to do exactly though.

---

### Post by BeachBilly on 2007-06-23
Now you've got me scared! I am, obviously, a full stop below Mavosa when it comes to being a first time anything having to do with Linux ... I just ordered Ununtu 7.04. Reading the comments, to get an idea of what I have to look forward to, I ran across this thread. Whoooie! Maybe I should just learn to live with this slow Windows ME that's well past it use-by date.
Oh, lordy ...
bill

---

### Post by louieb on 2007-06-23
Mavosa, Nice  to see you had a backup and got windws back. 
For Dual Booting a machine I use GRUB but thats my choice. Don't  remember if Herman has something on using  NTLDR in the [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/") But heres a thread that describes how to do it.[Booting Using NTloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=351692")  Your on the right track to use NTLDR  by putting grub in the boot sector of the Linux Partition.

Was doing some surfing on the Debian site and I found this [BootPart]("http://www.winimage.com/bootpart.htm").  on this page [Debian Dual Boot Windows and Linux Grub -  Linux with Windows 98 ME NT 2000 and XP]("http://www.aboutdebian.com/dualboot.htm"). If you decide to try   it let me know how it worked.

BeachBilly, I've found win/ME pretty good on low ram machines. If its slow running win/ME  two reasons come to mind one it bogged down by spy and ad ware; or it doesn't have much RAM or both.  To run Linux you really should have at 128MB memory for a light distro like [Puppy Linux ]("http://www.puppylinux.org/user/viewpage.php?page_id=1"). 256MB is fine for something like xUbuntu. Ubuntu run on 256MB but really needs more.

---

