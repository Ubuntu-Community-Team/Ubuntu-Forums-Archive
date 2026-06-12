---
title: "Increasing size of ubuntu on dual boot installation"
date: 2016-02-27
forum: General Help
---

### Post by bizhat on 2016-02-27
I had dual boot between Windows and Ubuntu. Windows stopped working after grub update, since i am happy with ubuntu, i did not try fixing it.

Now my ubuntu installation partition is almost full, i need to free up some disk space.

```

root@hon-pc-01:~# df -h | grep sda
/dev/sda5       243G  205G   27G  89% /
root@hon-pc-01:~# 

```

I deleted my windows partition

```

root@hon-pc-01:~# parted /dev/sda rm 2
Information: You may need to update /etc/fstab.                           

root@hon-pc-01:~# parted /dev/sda
GNU Parted 2.3
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Model: ATA ST31000528AS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type      File system     Flags
 4      528GB  799GB   271GB   extended
 5      528GB  793GB   265GB   logical   ext4
 6      793GB  799GB   6433MB  logical   linux-swap(v1)
 3      799GB  1000GB  201GB   primary

(parted) print free                                                       
Model: ATA ST31000528AS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
        32.3kB  528GB   528GB             Free Space
 4      528GB   799GB   271GB   extended
 5      528GB   793GB   265GB   logical   ext4
 6      793GB   799GB   6433MB  logical   linux-swap(v1)
 3      799GB   1000GB  201GB   primary
        1000GB  1000GB  2843kB            Free Space

(parted) quit                                                             
root@hon-pc-01:~#

```

Now disk have free space at start. Is there anyway i can get these free space used by linux installation ?

I can't boot on USB as my graphics card (GTX 750 TI) is not supported, so i get black screen on booting with USB, so can i do resize with rescue ? In that case, since no GUI, i need commands to  be used to increasing partition size.

I am using Ubuntu 14.04

```

root@hon-pc-01:~# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.4 LTS
Release:	14.04
Codename:	trusty
root@hon-pc-01:~# 

```

Thanks,

Boby

---

### Post by Topsiho on 2016-02-27
Hello Bizhat,

My guess is that your /dev/sda5, in which partition Ubuntu is installed, is getting full after many updates.
When updating, files are downloaded, used for the update, and after that NOT removed. Same for every Linux image file.
After a while your partition gets full.

So you have to get rid of these files:

sudo apt-get clean
sudo apt-get autoremove

After this you should have plenty of space on /dev/sda5 again, if I'm right.

Next updates you should do this every time, to prevent clogging your Ubuntu installation :)

Topsiho

---

### Post by bizhat on 2016-02-27
Thanks for the reply, I will do the cleaning when I am back on pc.

I do auto remove, purge packages that are uninstalled (reinstalled packages) and remove old kernels.

I think this is due to my files, I have some steam games and few videos that take up space.

If it's not possible to resize on rescue with parted out similar command line tools, I will create passion on free space and use it for some of the data, but I prefer resizing partition :)

---

### Post by Topsiho on 2016-02-27
Great.
see man apt-get
short: clean will clean update files that are not used anymore.
 and autoremove  removes the many Linux image files and header files up to the two latest ones.

Both files, update and Linux image- and header files can eat up a considerable amount of space.

I have the same problem with the computer of a friend of mine, which stopped working at all: his / partition (20 GB) was 100% full!!! Many many Linux image files ...
I'll have to instruct him how to do these same instructions, which worries me: he is quite computer illiterate. And uses his Linux box without any problem. Except this one !

If anyone can suggest a solution for this (automatically do this after an update), he or she is welcome.
Now my solution is to give him a / partition of 80 GB :(

Topsiho

---

### Post by yancek on 2016-02-27
You have 2 primary partitions, sda 3 and sda4 so you can simply create another primary partition of the space preceding sda4, your Extended partition then create a mount point for it and an entry in fstab so it is mounted on boot.  You could actually create 2 primaries, use this to store your moves and data.

---

### Post by yassine3 on 2016-02-27
Use Gparted LiveCD, I guess this shouldn&#8217;t have issue with your display card.

---

### Post by oldfred on 2016-02-27
With newer Ubuntu and nomodeset, your nVidia card should work.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by bizhat on 2016-02-27
> **Topsiho said:**
> Great.
see man apt-get
short: clean will clean update files that are not used anymore.


Did it, no change, it is my games and other files that take up space :)

```

boby@hon-pc-01:~ $ sudo apt-get clean
[sudo] password for boby: 
boby@hon-pc-01:~ $ df -h | grep sda
/dev/sda5       243G  204G   27G  89% /
boby@hon-pc-01:~ $ 

```

I think i have to look at using the free space available in my HDD, most of my file usage is in /home too.


> **yassine3 said:**
> Use Gparted LiveCD, I guess this shouldn’t have issue with your display card.

I did tried. after install or try screen, i click try, screen went black after showing up some error related to GPU 2 times. 

> **oldfred said:**
> With newer Ubuntu and nomodeset, your nVidia card should work.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Thanks oldfred, i think i tried with Ubuntu 14.04.3 LTS. I will try this.

---

### Post by bizhat on 2016-02-27
I was able to boot into LiveCD with nomodset (not sure if this is how it got fixed or my long wait this time). But after i am on desktop, i think i can't change extended partition size.

[img]http://i.imgur.com/0DHcHWl.png[/img]

Property of extended partition says Busy, but sda is not mounted.

Can't we resize an extended partition ?

---

### Post by grahammechanical on 2016-02-27
We can resize an extended partition but first we must remove that key icon alongside both sda4 & sda6. The live session is using the swap partition and so swap is on and that is preventing you from resizing sda4.

I may have these directions wrong but I think that you select sda6 and the open the Partition menu and in the list you will see that swap is on. You need to change that to swap = off. That should then remove the key icons against both sda6 & sda4 and then you can resize sda4 and follow that by resizing sda5.

Regards.

---

### Post by QLee on 2016-02-27
> **bizhat said:**
>  Property of extended partition says Busy, but sda is not mounted.  Can't we resize an extended partition ?  The extended partition is Busy because one of the extended partitions inside of it is mounted, the swap. Note the "key" icon in the screen shot, that means locked or "busy", in use.  Unless the system is really short of memory you could probably just turn the swap off and try to expand the extended partition and then the partition with Ubuntu on it. It probably can work but it might be a long process for gparted to add to the partition and move your files up to the beginning of the new partition and there is some danger of corruption with a process like that.  I have done it and had it work successfully but no guarantee.  Since you have nothing but Ubuntu on that drive and don't care about Windows, it might be faster and easier to backup your /home and restore it after reinstalling Ubuntu and letting it use the whole drive with just a partition for Ubuntu and one for swap. Or, like oldfred usually suggests, maybe a small (25 GB) partition for Ubuntu and a large partition for /home or just for Data. Or, do what  yancek suggested, that could work also. Or, use one of the clone programs depending on what you understand best.  I guess this isn't helpful if you don't  have a removable drive large enough for backup.  Plenty of people here to help.  Don't just do things until you have understood and made a choice.  [edit] I see grahammenical already mentioned the key icon while I was typing. That is the correct way to turn swap off.

---

### Post by bizhat on 2016-02-27
I disabled swap, but doing the re size, i got following warning.

[img]http://i.imgur.com/qKPYYIj.png[/img]

I don't want to lose my data... so i have to look for other ways, may be format free space, move home to it.

I can't wait to get Ubuntu 16.04, i will be reinstalling when it release, so only need to use current installation for 2 more months.

> **QLee said:**
> Since you have nothing but Ubuntu on that drive and don't care about Windows, it might be faster and easier to backup your /home and restore it after reinstalling Ubuntu and letting it use the whole drive with just a partition for Ubuntu and one for swap. 

I can copy existing /home and use it when i do reinstall ? 

In future i do plan to have a partition for /home, when i upgrade to Ubutnu 16, will i able to use same /home partition ?


> **QLee said:**
> 
use one of the clone programs depending on what you understand best.  I guess this isn't helpful if you don't  have a removable drive large enough for backup.  Plenty of people here to help.  Don't just do things until you have understood and made a choice. 

Never used any. Can you recommend an easy to use one, i will try to lean it.

---

### Post by deadflowr on 2016-02-28
You need to fill in the unallocated space in front of you data, so move it.
Easy to do by this:
Place your mouse over sda5 and right click.
Open Resize/Move.
In the resize window place mouse on the sda5 partition so that a closed fist shows.
Hold down the mouse button and drag it over to the left to fill in the space.

Now while still in the resize/move window put the mouse at the right side border of your sda5 partition.
A arrow should be showing.
As with holding the mouse to move the partition over do the same to resize it.
Drag the border to the right to fill in the unallocated space.
When filled simply click on the resize/move button.
The click on the Apply all operations button in the main gparted window.

So basically you want to move the sda5 partition to the left and then resize it to the right.

Does that make sense?


I have done this numerous times. And has worked every time.

The only caveat I can think of is how healthy the disk is.
(A failing hard drive with a bunch of bad sectors might be problematic, I do not know if it would be, but it is something to think about.)

It will take a while, since the data will be physically moved.
Byte by byte.

---

### Post by oldfred on 2016-02-28
See this on backups:
[http://ubuntuforums.org/showthread.php?t=2315304&p=13447231#post13447231](http://ubuntuforums.org/showthread.php?t=2315304&p=13447231#post13447231)

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
[http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)

I like to copy to other drives & flash drives.

 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

If you copy /home you cannot copy it back during install. If on same system as working install, then you can select it, but DO NOT tick the format box.

To mount it afterwards, or move it from inside / to new partition.
      To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by bizhat on 2016-02-28
Thanks for the the info, i will do the move home directory step.

Can anyone help with wine installation issue with NVIDIA GTX 750 TI ?

[http://ubuntuforums.org/showthread.php?t=2315165](http://ubuntuforums.org/showthread.php?t=2315165)

---

