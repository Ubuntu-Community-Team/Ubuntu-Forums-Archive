---
title: "Boot problems"
date: 2013-02-27
forum: General Help
---

### Post by aarontheryan on 2013-02-27
When I select Ubuntu from the GRUB screen I get this error message:

"Error: Attempt to read or write outside of disk 'hd0'

Press any key to continue..."

I've been getting this error for a few days and I click any key and it boots normally, but today it just became unresponsive when I pressed any key and doesn't boot into Ubuntu. 
Any way to fix this? 

I'm using ubuntu 12.10 and running it alongside Windows 7 by the way.

---

### Post by csad on 2013-02-27
Did you upgrade from 12.04 to 12.10 or something? Any idea what caused this? Because it sounds to me like something broke your grub.

What's the output of this:

```
sudo fdisk -lu
```

---

### Post by fdrake on 2013-02-27
boot from a live cd and follow steps "Method #2 with live cd" ([link]("http://theguyonthe3rdfloor.wordpress.com/2013/02/27/ubuntu-lost-password/")) untill step #3 (where it says "mount -o rw,remount /")
at this point run these commands:
```

wget https://sourceforge.net/projects/bootinfoscript/files/latest/download
tar -zxvf download
./bootinfoscript
less RESULTS.txt

```
attach here the content of the results file as an attachment please.

---

### Post by aarontheryan on 2013-02-27
> **csad said:**
> Did you upgrade from 12.04 to 12.10 or something? Any idea what caused this? Because it sounds to me like something broke your grub.

What's the output of this:

```
sudo fdisk -lu
```

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00088b99

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2   *      206848   531826687   265809920    7  HPFS/NTFS/exFAT
/dev/sda3       531826688   932274175   200223744   83  Linux
/dev/sda4       932274176   976771071    22248448   82  Linux swap / Solaris
```

---

### Post by aarontheryan on 2013-02-27
> **fdrake said:**
> boot from a live cd and follow steps "Method #2 with live cd" ([link]("http://theguyonthe3rdfloor.wordpress.com/2013/02/27/ubuntu-lost-password/")) untill step #3 (where it says "mount -o rw,remount /")
at this point run these commands:
```

wget https://sourceforge.net/projects/bootinfoscript/files/latest/download
tar -zxvf download
./bootinfoscript
gedit RESULTS.txt

```attach here the content of the results file as an attachment please.

There you go!

---

### Post by oldfred on 2013-02-27
You attached the down load info of the script. You need to run script as shown in links to script and it generates a new file results.txt which you can post in code tags (# in edit panel) or attach.

You can also run BootInfo report which runs bootscript plus it adds some extra data. It also can reinstall grub or make other repairs.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by aarontheryan on 2013-03-01
> **fdrake said:**
> boot from a live cd and follow steps "Method #2 with live cd" ([link]("http://theguyonthe3rdfloor.wordpress.com/2013/02/27/ubuntu-lost-password/")) untill step #3 (where it says "mount -o rw,remount /")
at this point run these commands:
```

wget https://sourceforge.net/projects/bootinfoscript/files/latest/download
tar -zxvf download
./bootinfoscript
less RESULTS.txt

```
attach here the content of the results file as an attachment please.

> **oldfred said:**
> You attached the down load info of the script. You need to run script as shown in links to script and it generates a new file results.txt which you can post in code tags (# in edit panel) or attach.

You can also run BootInfo report which runs bootscript plus it adds some extra data. It also can reinstall grub or make other repairs.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

Okay so I got this from boot repair: 

Please write on a paper the following URL:
[http://paste.ubuntu.com/5576240/](http://paste.ubuntu.com/5576240/)

In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] or to your favorite support forum.

No change has been performed on your computer.

---

### Post by oldfred on 2013-03-01
Did you install the 32bit version?

Does it boot or is error while running?

You have a large / (root) partition and we have seen where that causes grub boot issues. It seems to get lost when files are too far apart or too far from beginning of drive. Most reinstall with smaller / partition and separate /home or data partition(s) or create a small /boot near the beginning of the drive.

---

### Post by aarontheryan on 2013-03-04
> **oldfred said:**
> Did you install the 32bit version?

Does it boot or is error while running?

You have a large / (root) partition and we have seen where that causes grub boot issues. It seems to get lost when files are too far apart or too far from beginning of drive. Most reinstall with smaller / partition and separate /home or data partition(s) or create a small /boot near the beginning of the drive.

Yeah, I installed the 32 bit version. 
And it doesn't boot. Just when I select the Ubunut option that error springs up and then my computer becomes unresponsive. 

So I should probably re-install ubuntu on a smaller partition? I kind of need the memory though because I keep a lot of my photography, music and other files on my hard drive.

---

### Post by oldfred on 2013-03-04
I normally suggest 10 to 25GB for / (root) and then have separate /home or data partition(s). You can from gparted try shrinking your current / partition to see if that helps. About 50% that I suggest that to find it works. Or you may have to have a separate small /boot near the beginning of the drive.

If shrinking works, you can use gparted from liveCD and create a new partition for /home.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

or you can just create a partition for data and mount that into /home.
      
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

With dual booting with Windows you should really have a shared NTFS data partition so you do not write into the Windows system partition. Use shared data NTFS for any data you may want in both systems and set Windows as read only from Ubuntu.
      
 Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Mount NTFS partition:
[http://ubuntuforums.org/showthread.php?t=1927504](http://ubuntuforums.org/showthread.php?t=1927504)

---

### Post by aarontheryan on 2013-03-19
> **oldfred said:**
> I normally suggest 10 to 25GB for / (root) and then have separate /home or data partition(s). You can from gparted try shrinking your current / partition to see if that helps. About 50% that I suggest that to find it works. Or you may have to have a separate small /boot near the beginning of the drive.

If shrinking works, you can use gparted from liveCD and create a new partition for /home.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

or you can just create a partition for data and mount that into /home.
      
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

With dual booting with Windows you should really have a shared NTFS data partition so you do not write into the Windows system partition. Use shared data NTFS for any data you may want in both systems and set Windows as read only from Ubuntu.
      
 Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Mount NTFS partition:
[http://ubuntuforums.org/showthread.php?t=1927504](http://ubuntuforums.org/showthread.php?t=1927504)

I tried resizing sda3 from 190 GB to 20 GB using gparted but it is not allowing me to do that. It starts the process but n error message pops up and doesn't allow the operation to continue. The error just says "unable to resize partition". 

I really have no idea what to do here.

---

### Post by oldfred on 2013-03-19
If you have used 30GB how do you shrink to 20GB or dld you houseclean down to 15GB or move /home to a new partition?

From line 650 in your BootInfo:
>  /dev/sda3      ext4       188G   [COLOR=#ff0000]30G[/COLOR]  149G  17% /mnt/boot-sav/sda3



---

### Post by aarontheryan on 2013-03-19
> **oldfred said:**
> If you have used 30GB how do you shrink to 20GB or dld you houseclean down to 15GB or move /home to a new partition?

From line 650 in your BootInfo:

I did a fresh install of ubuntu on that partition (sda 3) because it wasn't allowing me to re-size. It's still not letting me re-size the partition after the fresh install. 
Should I install again and re-size during the set-up?

---

### Post by oldfred on 2013-03-19
Because you have the 4 primary partitions, I would reinstall, but create a 25GB / (root), /home for all but space for swap, and swap of 2GB or equal to RAM in GiB if you want to hibernate. You have to create an extended partition, so you can have many logical partitions.

         Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)


 [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

---

### Post by aarontheryan on 2013-04-03
> **oldfred said:**
> Because you have the 4 primary partitions, I would reinstall, but create a 25GB / (root), /home for all but space for swap, and swap of 2GB or equal to RAM in GiB if you want to hibernate. You have to create an extended partition, so you can have many logical partitions.

         Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)


 [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

Sorry about the delay in replying to this, many things came up that required my attention, but I managed to solve it.

What I did was I completely cleaned my hard drive by re-installing windows and then re-installing linux. This time I clicked "install windows side by side" and I created a shared 250 GB hard drive for each partition to see if it worked and up until now it has been working fine without a problem. If a problem does arise I can always come back to this thread again. I'm now experiencing other problems but they're unrelated to this (I think anyway) but I'll post aout them in another thread.

Thanks for the replies, everyone! I owe you one.

---

