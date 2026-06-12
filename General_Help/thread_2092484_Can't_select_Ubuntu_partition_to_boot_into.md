---
title: "Can't select Ubuntu partition to boot into?"
date: 2012-12-08
forum: General Help
---

### Post by Nagantman on 2012-12-08
I'm using a Dell Dimension 2400 computer that has Windows XP on it. I successfully installed Ubuntu  12.04 into a partition. For some reason when I restart my computer, when I go to boot options that partition isn't a choice for booting into. I tried out Ubuntu with my CD and used Boot-Repair, to no avail. What do I do? Any and all help greatly appreciated.

---

### Post by Kirk Schnable on 2012-12-08
> **Nagantman said:**
> I'm using a Dell Dimension 2400 computer that has Windows XP on it. I successfully installed Ubuntu  12.04 into a partition. For some reason when I restart my computer, when I go to boot options that partition isn't a choice for booting into. I tried out Ubuntu with my CD and used Boot-Repair, to no avail. What do I do? Any and all help greatly appreciated.


What happens when you boot?  Does the GRUB boot loader ever appear, does the computer boot straight to Windows XP, black screen, or other?

---

### Post by Nagantman on 2012-12-08
When I turn the computer on, I hit the F2 key. After that I go to boot setup yet my partition isn't there. Only boot from floppy disk, cd-r drive, and c:/ not my partition.

---

### Post by oldfred on 2012-12-08
Computers do not boot partitions. They boot MBR.

       Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
    
You need to install grub2's boot loader to the MBR of sda. Boot-Repair can do that for you. If you then still have issues post link to BootInfo report that it creates.

       MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by Nagantman on 2012-12-08
Here are the results after using Boot-Repair and using the recommended option. 

Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/1418257/](http://paste.ubuntu.com/1418257/)

In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] or to your favorite support forum.

You can now reboot your computer.

---

### Post by oldfred on 2012-12-08
Does it boot Ubuntu? 
And does Windows chain load entry work ok? 

Script looks ok.

---

### Post by Nagantman on 2012-12-08
Everything seems to be fine now, when I woke up this morning it gave me the option to boot into Windows XP or Ubuntu. I still have a few issues though. I created a swap partition and I don't think it is working. Ubuntu also freezes up on me and I have to reboot sometimes. Also sometimes when I log in, the words are all screwed up, and it is very hard to read everything. A bit hard to explain, unfortunately I didn't screen shot it. The only way I know how to solve it, is by rebooting.

---

### Post by oldfred on 2012-12-08
It may be a video issue?
What video card/chip do you have?

How much RAM do you have? Ubuntu needs 512KB minimum and then only 2D may work.

What does this show from terminal:

free -m

---

### Post by Nagantman on 2012-12-08
total       used       free     shared    buffers     cached
Mem:          1505       1180        324          0         69        794
-/+ buffers/cache:        316       1188
Swap:            0          0          0
nagantman@nagantman-Dimension-2400:~$ 

I did create a linux-swap partition though so how do get it working? Intel Corporation 82845G/GL chipset

---

### Post by Kirk Schnable on 2012-12-08
> **Nagantman said:**
> I did create a linux-swap partition though so how do get it working?

This section of the Ubuntu community documentation discusses how to use the **swapon** command to enable your swap partition. 

[https://help.ubuntu.com/community/SwapFaq#Why_is_my_swap_not_being_used.3F]("https://help.ubuntu.com/community/SwapFaq#Why_is_my_swap_not_being_used.3F")

---

### Post by Nagantman on 2012-12-08
Kirk I&#8217;m a bit confused here are the results after  
cat /etc/fstab 

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=76e10564-2322-438f-9bbf-42744c35a453 /               ext4    errors=remount-ro 0       1
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
nagantman@nagantman-Dimension-2400:~$ 

[IMG]http://file:///home/nagantman/Pictures/Link%20to%20GParted.png[/IMG]

---

### Post by Nagantman on 2012-12-08
I'm rather new to Linux and am still getting use to Terminal and reading what it tells me after executing commands.

---

### Post by Kirk Schnable on 2012-12-08
> **Nagantman said:**
> Kirk I’m a bit confused here are the results after  
cat /etc/fstab 

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=76e10564-2322-438f-9bbf-42744c35a453 /               ext4    errors=remount-ro 0       1
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
nagantman@nagantman-Dimension-2400:~$ 

[IMG]http://file:///home/nagantman/Pictures/Link%20to%20GParted.png[/IMG]
I don't see a swap partition in your fstab. By the way, the image you posted does not work...

---

### Post by Kirk Schnable on 2012-12-08
> **Nagantman said:**
> I'm rather new to Linux and am still getting use to Terminal and reading what it tells me after executing commands.
Please provide the output of:
```
sudo fdisk -l
``` 
And I will assist you in identifying your swap partition if it exists.

---

### Post by Nagantman on 2012-12-08
Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2a402a3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    53266431    26632192    7  HPFS/NTFS/exFAT
/dev/sda2        57362432    78123007    10380288   83  Linux
/dev/sda3        53266432    57362431     2048000   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by Kirk Schnable on 2012-12-08
> **Nagantman said:**
> Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2a402a3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    53266431    26632192    7  HPFS/NTFS/exFAT
/dev/sda2        57362432    78123007    10380288   83  Linux
/dev/sda3        53266432    57362431     2048000   82  Linux swap / Solaris

Partition table entries are not in disk order

/dev/sda3 is your swap partition.  This should activate it if it's deactivated:
```
sudo swapon /dev/sda3
```

---

### Post by Nagantman on 2012-12-08
Yes, I knew it was sda3, and I had tried that  command just to get this 

nagantman@nagantman-Dimension-2400:~$ sudo swapon /dev/sda3
[sudo] password for nagantman: 
nagantman@nagantman-Dimension-2400:~$ 

No result?

---

### Post by Kirk Schnable on 2012-12-08
> **Nagantman said:**
> Yes, I knew it was sda3, and I had tried that  command just to get this 

nagantman@nagantman-Dimension-2400:~$ sudo swapon /dev/sda3
[sudo] password for nagantman: 
nagantman@nagantman-Dimension-2400:~$ 

No result?

Can I get the outputs of:

```
cat /proc/swaps
```

```
free
```

---

### Post by Nagantman on 2012-12-08
There you are-

nagantman@nagantman-Dimension-2400:~$ cat /proc/swaps
Filename                Type        Size    Used    Priority
/dev/sda3                               partition    2047996    0    -1
nagantman@nagantman-Dimension-2400:~$ free
             total       used       free     shared    buffers     cached
Mem:       1541700     839948     701752          0     100896     428244
-/+ buffers/cache:     310808    1230892
Swap:      2047996          0    2047996
nagantman@nagantman-Dimension-2400:~$

---

### Post by Kirk Schnable on 2012-12-08
> **Nagantman said:**
> There you are-

nagantman@nagantman-Dimension-2400:~$ cat /proc/swaps
Filename                Type        Size    Used    Priority
/dev/sda3                               partition    2047996    0    -1
nagantman@nagantman-Dimension-2400:~$ free
             total       used       free     shared    buffers     cached
Mem:       1541700     839948     701752          0     100896     428244
-/+ buffers/cache:     310808    1230892
Swap:      2047996          0    2047996
nagantman@nagantman-Dimension-2400:~$

Your swap looks like it's working to me. It's normal for it to be empty unless it's needed.

---

### Post by Nagantman on 2012-12-08
Hmmm alright another question if you don't mind. Running 12.04 Ubuntu on this old desktop to start getting into Linux. Dell Dimension 2400 1 core processor, 1 gigabyte of ram. I have this computer dual booted with Windows XP. Ubuntu outperforms it in every way. But for some reason, when it comes to scrolling down on websites it's very choppy. In terms of launching Firefox and just generally going around through folders, various settings etc. Everything is very efficient but when it comes to something so simple like scrolling down it is a major nuisance, and no my internet is not the problem.

---

### Post by Kirk Schnable on 2012-12-08
> **Nagantman said:**
> Hmmm alright another question if you don't mind. Running 12.04 Ubuntu on this old desktop to start getting into Linux. Dell Dimension 2400 1 core processor, 1 gigabyte of ram. I have this computer dual booted with Windows XP. Ubuntu outperforms it in every way. But for some reason, when it comes to scrolling down on websites it's very choppy. In terms of launching Firefox and just generally going around through folders, various settings etc. Everything is very efficient but when it comes to something so simple like scrolling down it is a major nuisance, and no my internet is not the problem.

Navigating folders could definitely be slow because your Dell Dimension 2400 probably has an ancient and slow IDE hard drive in it. I have a Dimension 2400 laying around my house as well, so I know IDE is the only choice for it other than a SATA card in your PCI slot. But, a newer hard drive would probably perform much better. They make IDE solid state drives, too. 

Firefox scrolling could possibly be hard drive related (fetching info from cache) or could be CPU or GPU related. Some looking into the output of **top** while scrolling in Firefox might be insightful.

---

### Post by Nagantman on 2012-12-08
> Some looking into the output of **top** while scrolling in Firefox might be insightful. 
What should I do exactly?

---

### Post by Bartender on 2012-12-08
all you do is open a terminal and type 

```
top
```

then hit Enter.  The top utility keeps track of CPU and memory usage.  So you would push the little top window over to one side of the screen, then go ahead and do whatever it is you want to do in Firefox and see if CPU or mem redlines.

---

### Post by Nagantman on 2012-12-09
Thanks for the help everyone I appreciate it. Firefox seemed to start working correctly for some odd reason. But I will still check the CPU usage.

---

