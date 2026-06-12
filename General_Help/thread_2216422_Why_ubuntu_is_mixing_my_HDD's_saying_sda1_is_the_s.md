---
title: "Why ubuntu is mixing my HDD's saying sda1 is the same as sdb6"
date: 2014-04-11
forum: General Help
---

### Post by ryanpantano on 2014-04-11
So i have this problem which i really don't know what to do with it, but it's making me alot of problems.The problem is not only locked to sda1 and sdb6 partitions it can change from boot to boot.
First thing that happened to me is that i was on windows, working regularly as i do in photoshop, and installing the game over Steam in background(so game is not cracked i counldn't get a virus if that matters).

When i finished with photoshop i wanted to boot back to Linux when suddenly i got an error on boot like

    Couldn't boot device /mount/sdb1 

    ```
s for continue or m for manual recovery
```

So i hit s to continue boot when in linux i see the partition is missing. So i typed

```
sudo fdisk -l
```

And i see the partition is there, only invisible on ubuntu, i checked than with gparted and i noticed that sdb1 is actually the partition where is my linux installation. What the heck now?  but im missing the other partition sdb2, not sdb1 like it said on boot.
So i went back to windows and i one of the partitions is basically formated it was the sdb6 partition which was missing in linux.
So i went back on linux and same error on boot and started in deep look.

THE HDD AND PARTITION CONFIGURATION BEFORE I HAD A PROBLEM WAS LIKE THIS 

```
sdb Maxtor HDD

     sdb1 extended
       sdb5 swap
       sdb6 ext4 Linux
     
     sdb2 ntfs label Second

sda Hitachi HDD

sda1 ntfs label Storage
     sda2 ntfs label System reserved (this is windows 100mb system reserved partition)
     sda3 ntfs (windows installation partition)
```


So the sdb2 partition is now missing and not able to mount. I have the same partition configuration now. But take a look at this.
Gparted is showing that partition is mounted and not able to unmount, while partition is not mounted and visible at all in nautilus. Krusader however shows that partition is there, but not able to mount it.

[ATTACH=CONFIG]251957[/ATTACH][ATTACH=CONFIG]251958[/ATTACH]

So investigating further more fdisk -l says this


    Disk /dev/sda: 250.1 GB, 250059350016 bytes
    255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0xc17e8984


    Device Boot      Start         End      Blocks   Id  System
    /dev/sda1            2048   278386687   139192320    7  HPFS/NTFS/exFAT
    /dev/sda2   *   278386688   278591487      102400    7  HPFS/NTFS/exFAT
    /dev/sda3       278591488   488394751   104901632    7  HPFS/NTFS/exFAT


    Disk /dev/sdb: 251.0 GB, 251000193024 bytes
    255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0xc17e89fa


    Device Boot      Start         End      Blocks   Id  System
    /dev/sdb1   *        2046   204797951   102397953    5  Extended
    /dev/sdb2       204797952   490233855   142717952    7  HPFS/NTFS/exFAT
    /dev/sdb5            2048    20477951    10237952   82  Linux swap / Solaris
    /dev/sdb6        20480000   204797951    92158976   83  Linux


Let some similar numbers not confuse you because both HDD's are 250GB SATA II(or one is SATA I i think that's not important)

Than i opened /etc/fstab to check if it have something changed and compared to the old backup file, but nothing is different there, it's by defaults.


    # /etc/fstab: static file system information.
    #
    # Use 'blkid' to print the universally unique identifier for a
    # device; this may be used with UUID= as a more robust way to name devices
    # that works even if disks are added and removed. See fstab(5).
    #
    # <file system> <mount point>   <type>  <options>       <dump>  <pass>
    proc                                       /proc        proc  nodev,noexec,nosuid  0     0  
    # / was on /dev/sda6 during installation
    UUID=885cb3b6-ec34-4dda-a0d6-d3da291684e3  /            ext4  errors=remount-ro    0  1  
    # swap was on /dev/sda5 during installation
    UUID=d56da767-41cc-4d13-9739-9ab86fd6d648  none         swap  sw                   0  0 


So for the final step i used Storage Device Manager (it's basically gui for fstab) and that's where i noticed strange thing in naming my hdd's and partitions, take a look at screenshoots. In 2 of the different partitions and on different hdd's it's say they are the same and that they are the same hdd.

This should be the first disk (sda)

[ATTACH=CONFIG]251956[/ATTACH]

And this should be the second disk (sdb)

[ATTACH=CONFIG]251955[/ATTACH]

Notice how it says that sda1 is the same partition and HDD as sdb2, and weirdest thing is that now when i started Storage Device Manager again, sda1 is missing from the list.

Now after restarting my pc, sda1 says it's sdb6, weird right? is it a disk problem or is it ubuntu problem?

[ATTACH=CONFIG]251954[/ATTACH]

Anyone have any thoughts on this?

---

### Post by oldfred on 2014-04-11
Did you copy sda1 to sdb6?

Post this, if UUIDs are the same that would be the issue:
       sudo blkid -c /dev/null -o list

---

### Post by ryanpantano on 2014-04-12
> **oldfred said:**
> Did you copy sda1 to sdb6?

Nope i didn't do anything, as i said last that i was doing is that i was on windows, installing game over steam, and working in photoshop. Next i restarted to ubuntu and there was a problem.

I just restarted pc again and now sda1 is showing that is actually sdb2 maxtor hdd (sda is Hitachi hdd)

Here's output of your command

```

/dev/sda1  ntfs         Storage                      /media/Storage                              04F8EF0CF8EEFB36
/dev/sda2  ntfs         System Reserved         /media/System Reserved                 7E08AC9F08AC57C3
/dev/sda3  ntfs                                         /media/3C40B35D40B31C98              3C40B35D40B31C98
/dev/sdb2  ntfs         Second                      /media/Second                               34EC0018680F8CEE
/dev/sdb5  swap                                      <swap>                                         d56da767-41cc-4d13-9739-9ab86fd6d648
/dev/sdb6  ext4                                        /                                                  885cb3b6-ec34-4dda-a0d6-d3da291684e3



```

Problem looks like it is if i set it to boot on startup sda1 will change it's mind on next reboot to be something else like sdb6 again. I mounted partitions now with Disk Utility but i still don't see sda1 in nautilus untill i mount the partition.


[FONT=arial black]EDIT:

[/FONT]I just restarted my pc 2 more times and both times i had different results, take a look at screenshots

[ATTACH=CONFIG]251968[/ATTACH][ATTACH=CONFIG]251967[/ATTACH]

Now on first screenshot where i have sda1 sda2 sda5 sda6, on that boot i have partitions like i had before, "storage" and "second" are listed when i click on Places and i can mount them both with no problem.

---

### Post by mcduck on 2014-04-12
The device names depend on the order in which the computer recognizes the devices when it boots up. On some motherboards the order can change on every boot or if you have any removable drives plugged in or not. Which is the reason why Ubuntu by default uses UUIDs to point to actual specific filesystems instead of relying on the device names.

So, if you have at any point edited your /etc/fstab, make sure it's still using UUID and not the device names.

---

### Post by ryanpantano on 2014-04-12
> **mcduck said:**
> The device names depend on the order in which the computer recognizes the devices when it boots up. On some motherboards the order can change on every boot or if you have any removable drives plugged in or not. Which is the reason why Ubuntu by default uses UUIDs to point to actual specific filesystems instead of relying on the device names.

So, if you have at any point edited your /etc/fstab, make sure it's still using UUID and not the device names.

Nope as i said the /etv/fstab is as default, and i don't have any removable devices or anything different, my ubuntu is working on same setup for last 6 months, and it's always loading sata1, sata2, sata3 ... however yesterday it stoped loading hdd which was on sata1, so i switched them in sata4 and sata5 ports, and i noticed that speed of hdd's is extremely slow with copying files 2MB/s while they should copy at least 30MB/s so it might be the motherboard problem instead ubuntu ? ill test hdd's on other pc to see what will it come up.

---

