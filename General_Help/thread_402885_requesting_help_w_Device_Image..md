---
title: "requesting help w/ Device Image."
date: 2007-04-06
forum: General Help
---

### Post by billdotson on 2007-04-06
Hello, I have downloaded the zsplit and unzplit debs and installing them in Ubuntu by doing the following in the terminal:

```

sudo dpkg -i [file_name].deb
sudo dpkg -i [file_name].deb

```

obviously the file name is zsplit and unzsplit.

Now that I have installed them and have moved around files and stuff to have enough space on my external HDD to put the 171GB device image.
I have been reading the documentation on deviceimage.de and AFAIK it seems that you cannot back up the device image to a partition that zsplit or unzsplit is not on.

So, I have an external HDD.  Ubuntu is on the first partition, with swap on the second, an extended on the third w/ a FAT32 and a ext3 logical partition and a fourth partition of 225GB NTFS.  I have enough space on the NTFS partition to backup my Windows install but I cannot seem to get ntfs-3g to work.

What I want to do is: boot into Ubuntu, mount my Windows drive, then use zsplit to make a device image and have the device image be saved to my NTFS partition on my external HDD.  

On the device image website it had a few different scenarios but none of them seem to match what I want to do.   

There is one that looks similar but it involves booting from the device image LiveCD.. which costs money as of right now.
Here is what it is:

```

zsplit -N WinXP_backup -d /dev/hda

```

the explanation of what it does is @ [http://www.device-image.de/main_docu.htm]("http://www.device-image.de/main_docu.htm")

As far as I understand, that command creates one big image from /dev/hda and saves it to the partition that zsplit and unzsplit are running off of.  What I need to do is to boot /dev/sdc1 (external HDD partition Ubuntu is on) then use zsplit to make an image of /dev/sda1 and save that image to /dev/sdc4.  Would I just do the following if I wanted to do so??

```
 
zsplit -N /media/Backup_ntfs/WinXP_backup -d /dev/hda

```

as /media/Backup_ntfs is where /dev/sdc4 is mounted.

Also, I did sudo apt-get install ntfs-3g in Ubuntu, then followed the readme as how to upgrade to the newest FUSE module and then went into my /etc/fstab and changed the ntfs after my /dev/sdc4 entry to ntfs-3g like it instructed.  It didn't do anything and I still could not write to that partition.  I would just make it a ext3 partition but I have 40GB of video on that partition that I can't move somewhere else as I am out of space on all my other partitions.

Thanks.

---

