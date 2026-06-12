---
title: "Data isn't being saved in usb upon removal"
date: 2014-12-11
forum: General Help
---

### Post by Jahidul_Hamid on 2014-12-11
When I remove usb after finishing data transfer (file operation completed), I find an empty folder with nothing inside. But if I first eject and then remove the usb, it takes some time to eject and now I have the folder with everything there. So why I have to eject everytime and then remove, is there some config problem for which data isn't being saved instantly..?

xubuntu 14.04 LTS

---

### Post by lisati on 2014-12-11
The need to "safely remove" a device before unplugging it is normal for both *nix and Windows systems. The reason for this is that file operations are commonly buffered. You need to ensure that the buffers are properly flushed, otherwise you risk losing part (or all) of your data. 

I'm not aware of any system settings that will help eliminate or reduce the need for this, and will happily stand corrected if other forum users have any extra information.

---

### Post by sudodus on 2014-12-12
> **Jahidul_Hamid said:**
> When I remove usb after finishing data transfer (file operation completed), I find an empty folder with nothing inside. But if I first eject and then remove the usb, it takes some time to eject and now I have the folder with everything there. So why I have to eject everytime and then remove, is there some config problem for which data isn't being saved instantly..?

xubuntu 14.04 LTS

> **lisati said:**
> The need to "safely remove" a device before unplugging it is normal for both *nix and Windows systems. The reason for this is that file operations are commonly buffered. You need to ensure that the buffers are properly flushed, otherwise you risk losing part (or all) of your data. 

I'm not aware of any system settings that will help eliminate or reduce the need for this, and will happily stand corrected if other forum users have any extra information.

Long ago (before USB was invented) there were computers that did not buffer the data (for example with old DOS operating systems). I remember when buffering was introduced into DOS, and people were told (at shutdown) to wait until the shutdown had finished to switch off the main power. Since then it has been important to consider flushing the buffers in PCs. It is possible to make systems that write to the drives before continuing, but computers with such systems will be slow and inconvenient to use.

---

### Post by Jahidul_Hamid on 2014-12-12
In linux Mint 17 LTS this doesn't occur everytime (but frequently), in windows (7,8,8.1) I have never seen this problem.

In xubuntu no matter how much I wait for the buffering to complete it seems that it (buffering) starts only when i try to eject...

---

### Post by lisati on 2014-12-12
> **Jahidul_Hamid said:**
> In linux Mint 17 LTS this doesn't occur everytime (but frequently), in windows (7,8,8.1) I have never seen this problem.

In xubuntu no matter how much I wait for the buffering to complete it seems that it (buffering) starts only when i try to eject...

I think you have misunderstood what I was referring to. By "buffering" I meant that data doesn't always get written to a disk or USB device immediately, but is held in an area of memory sometimes known as a buffer, and sometimes known as a write cache. It might seem like a copy operation has completed, but if the device is removed before the contents of the buffer is completely copied to the device, then there is a risk of data being lost. 

An article written from the Windows perspective can be found here: [http://www.howtogeek.com/118546/htg-explains-do-you-really-need-to-safely-remove-usb-sticks/](http://www.howtogeek.com/118546/htg-explains-do-you-really-need-to-safely-remove-usb-sticks/)

---

### Post by Impavidus on 2014-12-12
Reading the man page for mount (yes, it's very long):```

FILESYSTEM INDEPENDENT MOUNT OPTIONS
       Some of  these  options  are  only  useful  when  they  appear  in  the
       /etc/fstab file.

       Some  of  these  options could be enabled or disabled by default in the
       system kernel.  To  check  the  current  setting  see  the  options  in
       /proc/mounts.

       The  following  options  apply  to any filesystem that is being mounted
       (but not every filesystem actually honors them - e.g., the sync  option
       today has effect only for ext2, ext3, fat, vfat and ufs):

       async  All  I/O  to  the filesystem should be done asynchronously. (See
              also the sync option.)

...

       sync   All  I/O to the filesystem should be done synchronously. In case
              of media with limited number of write cycles  (e.g.  some  flash
              drives) "sync" may cause life-cycle shortening.

...

FILESYSTEM SPECIFIC MOUNT OPTIONS
...
Mount options for fat
...
       flush  If set, the filesystem will try to flush to disk more early than
              normal.  Not set by default.

```
When I plug in a FAT32 usb drive, it is automounted with the flush option. This should flush all buffered data to the drive in a short time, like seconds, but not at once. I assume Windows by default uses something similar.

---

### Post by Jahidul_Hamid on 2014-12-12
> **Impavidus said:**
> 
When I plug in a FAT32 usb drive, it is automounted with the flush option. This should flush all buffered data to the drive in a short time, like seconds, but not at once. I assume Windows by default uses something similar.

I think you got the point here....

I just noticed that the partition table was in GPT, I changed it to msdos and it works now as expected...

Though i am getting a boot error when making it bootable with unetbootin, but don't think it's that big of a problem to solve...

thnks for the answers..

---

