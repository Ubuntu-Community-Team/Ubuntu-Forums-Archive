---
title: "What's the Easiest Way to Clone Boot Partition?"
date: 2019-03-28
forum: General Help
---

### Post by cliffflip on 2019-03-28
[COLOR=#242729][FONT=Arial]Right now I'm using a 1TB HDD for Ubuntu 18.10, but the used space is only 50GB (single partition). I'm looking to buy a 250GB SSD and install 18.10 there but I don't want to do clean install because it will take time to set everything the way I want again.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Now I'm in the middle of shrinking the 1TB partition to 100GB, because like I read on Internet, we can't clone partition that's bigger than the destination drive/partition. So, what's the easiest way to do that? I've read about Clonezilla but there's only tutorial for drive-to-drive cloning, not partition-to-partition.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Please help me, thanks :)[/FONT][/COLOR]

---

### Post by TheFu on 2019-03-28
There might be a conversion from 512b sectors into 4k sectors in your migration. This could make attempting to clone the disk a mistake.
Also, if your backup and restore method takes longer than 30-45minutes, then I'd say you need a better solution.  Linux isn't like Windows.  All your settings are relatve to your HOME, so if you want things configured the same, just copy everything from HOME over to the new disk and put it into the same place.  Bit-for-bit cloning is problematic for a few reasons.  But if you use a file-based method, provided everything "appears" to be in the same location inside a file system, all will work.

BTW, "boot partition" isn't clear.  Do you have UEFI?  Or still use Legacy boot?  GPT or MSDOS partitioning?
To provide help for your specific situation, some facts are required.
**df -Th|grep '^/dev/'** will get us some useful data.

Here's mine:
```
$ df -Th|grep '^/dev/'
/dev/sda1                       vfat      511M  3.7M  508M   1% /boot/efi
/dev/sda2                       ext2      721M  142M  543M  21% /boot 
/dev/mapper/ubuntu--vg-root     ext4       25G  7.5G   16G  33% /
/dev/mapper/ubuntu--vg-home--lv ext4       74G   20G   51G  28% /home
/dev/mapper/ubuntu--vg-stuff    ext4       99G   95M   94G   1% /stuff
```

What this shows is that I'm UEFI booting off a FAT32 [required] partition (/boot/efi), from an ext2 [ext3/4 would be fine too] boot partition (/boot), and that I use LVM for storage management with / in one LV, /home in another LV and miscellaneous other stuff in a 3rd LV called /stuff.  I use ext4 for all these other file systems. There are many reasons for this setup.  
You can think of LVs, logical volumes, as partitions.  Do you see the sizes?  / is 25G, /home is 75G and stuff is 100G - the numbers after formatting with a file system are slight less, as shown.   I'm on an SSD and have only allocated what I need, not all that it can hold.  This is good practice for SSDs to provide the longest life span. Adding more space to an LV is trivial using LVM, unlike adding more storage to partitions. Moving an LVM LV from 1 disk to another is trivial too. There are built-in commands for that.

Everything below the actual directories in the storage isn't really that important to the OS and having it work.  As long as the files "appear" in the file system to be in the correct locations, it doesn't matter with just a few rules.  Post your command output and someone can explain what must be specific and what isn't necessary.  

Having HOME separate from / can be very handy for backups and reducing OS upgrade risks.

If you are using LVM and can connect both storage to the system concurrently, that would make this migration much easier.

Lastly, is there a specific reason to run 18.10?  Perhaps hardware that is extremely new?  In general, running the LTS release is better to avoid beta-like software.

---

### Post by VMC on 2019-03-28
Follow TheFu's advice. Also '*fsarchiver*' can clone your Ubuntu and restore it to a larger partition. Its not a bad idea to backup your EFI partition. It saved me grief on Windows once I messed up installing another OS.

---

### Post by abduleliass on 2019-04-19
So how can i read the code.if the portion is done well

---

### Post by HermanAB on 2019-04-19
Basically, there isn't an easy way to clone a system.  The easy way is to reinstall it.

---

