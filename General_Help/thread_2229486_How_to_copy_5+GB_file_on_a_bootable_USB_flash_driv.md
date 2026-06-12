---
title: "How to copy 5+GB file on a bootable USB flash drive?"
date: 2014-06-13
forum: General Help
---

### Post by lu333031 on 2014-06-13
I need a bootable USB flash drive that also has a large file (5+GB) on it.

I can creat a bootable USB flash drive from my 32-bit linux system (Ubuntu 12.04LTS) but I cannot copy the large file to the USB flash drive because the process of creating of the bootable USB flash drive turns the flash drive into a FAT32 format even though I start with the flash drive formatted as ext4. Since FAT32 does not allow copying files greater than 4GB or so, my copy fails.

Is there a way to somehow partition the USB flash drive with different formats (FAT32 and ext4) so that the Startup Creator can be directed to use the FAT32 partition for the booting part leaving the rest of the USB drive in ext4 format?

I must have the large file on the bootable USB flash drive and not on a separate medium.

Thanks.

Lu

---

### Post by stalkingwolf on 2014-06-13
its slow but copy the large file in smaller sections. Is the drive you are copying from a larger drive? You might be able to just clone the file.

---

### Post by lu333031 on 2014-06-13
Yes, the file to be copied is a compressed (.gz) file residing on the 160GB HD of my linux system. 
How would I copy it in parts and make it whole on the target (USB flash drive)?
How would I clone it?

Thanks.

Lu

---

### Post by yancek on 2014-06-13
What software did you use to create the bootable flash?
Did you create it with persistence?  If you did, you could create another partition if you have space on the flash drive and format it as ext2 and then create a mount point for it and put an entry in the /etc/fstab file.  If you don't have persistence, you would have to manually mount it every time you boot.

---

### Post by lu333031 on 2014-06-13
I used the native ubuntu Startup Creator to create the bootable drive. I did not see any options for anything except selecting the source and the target. I used the iso image saved on my HD as the source.

---

### Post by lu333031 on 2014-06-13
I just tried the following -


>
> cd  /media/<myUSBDrive>/<TgtDir>
> sudo dd if=$HOME/<SrcDir>/<LargeSrcFile>   >    ./<LargeTgtFile>
>

It seemed to go well for a couple of minutes and then failed with 


-----------------
dd: writing to `standard output': File too large
8388608+0 records in
8388607+1 records out
4294967295 bytes (4.3 GB) copied, 185.055 s, 23.2 MB/s
-----------------

I created the large file (the source) using dd (piped through gzip) so why the size problem?  :(
(The USB flash drive has over 20GB free).


Thanks.

Lu

---

### Post by yancek on 2014-06-13
Using the command below gives an option to  select the amount of Stored in reserved extra space, the default is 1GB.  This will give persistence.  Unetbootin also gives that option.  Using either of these options will overwrite whatever you now have on the flash, if that matters.

gksudo usb-creator-gtk

---

### Post by lu333031 on 2014-06-13
"gksudo usb-creator-gtk" invokes the same GUI (apparently) that Startup Disk Creator does. However, going via this command ends in the following failure -

--------------------------------
(usb-creator-gtk:13208): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.UB3JHX': No such file or directory

(usb-creator-gtk:13208): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
--------------------------------
 
I tried it twice. I did not get any failures while creating the bootable flash drive earlier with Startup Disk Creator. The flash drive is not expected to have anything much more than the files created by ubuntu to make it bootable and my large file which needs an ext4 format. So as of now, no data on the flash drive is precious.

But thanks.

Lu

---

### Post by mc4man on 2014-06-13
Pretty simple - 
First create a small Fat32 partition big enough to install to (lately 1.2GB or so
Then create another partition that supports large files, ntfs or ext2/3/4
After that open s-d-c & install to the fat partition

ex. in screen, the fat has 14.04 live installed (scr.2, the other  is ntfs (scr 1

---

### Post by C.S.Cameron on 2014-06-14
To expand the above method a little:

Following is a step by step for making Live USB's with persistence size only limited by flash drive size.
I would make the first partition oversize because it is the only one a Windows machine can see.
You can revise partition size later using gparted.

Boot Live CD or Live USB.
Plug in flash drive.
Start Partition Editor.
Create 10 GB FAT32 partition, (on the left side of the bar). (size is optional, extra space can be used for file storage and transfer to Windows machines).
Create a 10 GB ext2 partition to the right of this, labeled it "casper-rw". (ext3 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, Go to the root folder of your Live USB
Enter the syslinux directory, (or for UNetbootin the root directory).
Make the syslinux.cfg file writeable
Replace the contents of the file syslinux.cfg with:


```
    default persistent
    label persistent
      say Booting a persistent Ubuntu session...
      kernel /casper/vmlinuz
      append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```

Shutdown, remove CD, reboot.


First time booting go to users and groups and create an account with yourself up as an Administrator, with password if desired.

Note:
The above code will bypass the Try/Install and Language screens.

---

### Post by lu333031 on 2014-06-16
mc4man, I was able to solve my problem last week and move on by doing something similar to what you suggest. I had not been able to partition my flash drive with GParted using my linux system. I didn't try to figure out why after trying a few things which did not work. So I made 2 partitions on the flash drive using the Disk Utility on my MacBook instead. Made a 4GB partition of type MSDOS and the rest as one of the MacOS types. When I inserted this flash drive into my linux system and invoked the StartupDiskCreator, it was only able to see the 4GB partitition so it was quite straighforward to create the bootable flash drive on that partition. 

Then I invoked GParted again and it showed 4GB of the (now) FAT32 boot partition and the rest as "unknown". So I created a 20GB or so partition of type ext4 at the higher end of the flash memory leaving the middle section unallocated (probably not necessary but I didn't want the two to be next to each other :)). I was then able to copy my large file from my HD to the ext4 partition with a cp command. The ext4 parition had to be mounted on a directory created on the flash drive. I've been able to boot with this flash drive and do what I wanted with the large file after having to tweak some scripts for the extra mount operation etc.

I don't know if my method is the most elegant or simple solution to my dilemma but it seems clean enough and is definitely doing the needful.

Thanks.

Lu

---

