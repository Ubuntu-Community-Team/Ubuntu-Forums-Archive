---
title: "Questions on partions"
date: 2015-12-31
forum: General Help
---

### Post by Cyber72 on 2015-12-31
I have just installed 14.04 64 bit and want to partition my disk. I think the easiest way may be to reinstall and choose the "something else" option and partition prior to installing. I want to partition for 3 operating systems. (I have watched several youtube videos for GParted but it is the old  story - the people making the videos haven't worked out that there is little point in making a video for people who already know how to use the software so the sensible way to make such a video is to aim it at first timers)

Here is what I have now after an automatic install

```
NAME                           FSTYPE                     SIZE MOUNTPOINT LABEL
sda                                                                     74.5G            
&#9500;&#9472;sda1                         ext2                                243M /boot      
&#9500;&#9472;sda2                                                               1K            
&#9492;&#9472;sda5                         crypto_LUKS                   74.3G            
  &#9492;&#9472;sda5_crypt (dm-0)          LVM2_member           74.3G            
    &#9500;&#9472;ubuntu--vg-root (dm-1)   ext4                         70.4G /          
    &#9492;&#9472;ubuntu--vg-swap_1 (dm-2)                             3.9G            
sr0                                                                      1024M  
```

So my questions:-
1 Why sda5 and not sda3?
2 Can I just make my 3 partitions sda5, sda6 and sda7 and leave the iso to sort out the crypto and swap?

---

### Post by 1clue on 2015-12-31
Are either of your other operating systems Windows?

If not, you might want to try a GPT partition table.  MBR partition tables became obsolete the first time when hard disks exceeded 32 megabytes in size.  My wife has a watch with more memory than that.

That said, you need to be sure that your hardware and your operating systems support this.  And I don't think Ubunt installation medium does this, I use system rescue cd or Gentoo installer for partitioning, but I don't know if that's absolutely necessary anymore.

My reasoning is that MBR is what causes a layout like you have, and GPT has no such limitations.

I might also recommend that you put only one operating system on the bare metal and run the other two in VMs.  You then get your choice of any at any time, even simultaneously.

---

### Post by yancek on 2015-12-31
>  Why sda5 and not sda3?

Most likely because sda2 is an Extended partition which cannot hold data so it contains logical partitions.  Logical partitions are numbered beginning at sda5.

It's not possible to tell from what you posted whether you have any free space.  If you posted the output of fdisk -l it would be more informative.  You are also using LVM and resizing and creating partitions is different than the standard method.   I understand GParted, at least the newer versions can do this.  I've never used LVM but you might take a look at the actual GParted Manual to see if you can find anything there.

 [http://gparted.org/display-doc.php%3Fname%3Dhelp-manual](http://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

---

### Post by 1clue on 2015-12-31
As far as lvm and resizing partitions, if you use ext4, xfs or another newer format you can resize on-the-fly.  It's why I use lvm.

With respect to 3 operating systems I can't be of much help.  In my situation I need simultaneous access and so use KVM or another physical host for those other operating systems, I haven't done dual boot for more than 10 years, probably closer to 20.

I'm also not fluent at all with gparted.  IMO it's horribly unfriendly and unintuitive.  I use gdisk, and GPT partitions. That won't work for all operating systems though.

---

