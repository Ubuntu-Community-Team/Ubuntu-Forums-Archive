---
title: "Create LVM using existing partition"
date: 2018-03-30
forum: General Help
---

### Post by cruzer001 on 2018-03-30
I am creating my first LVM and would appreciate it if someone could confirm that my intended method is correct.

I have a 650G unformatted partition (sda3) I wish to convert and have installed lvm2.

I first create a physical volume.
```
sudo pvcreate /dev/sda3
```
I next create a volume group (named lvm).
```
sudo vgcreate lvm /dev/sda3
```
And last my logical volume(s) (450G for data storage)
```
sudo lvcreate -n data -L 450g lvm
```
Leaving 200G of free space for future installs (I hope it works like that).

Thanks

---

### Post by TheFu on 2018-03-30
I'd recommend against using "lvm" for the VG name.  Also, "data" is fairly generic. You might find that you need unique names for these in the future for certain reasons.

I always follow a howtoforge guide when setting up my LVM stuff manually.  It isn't something I do often enough to ensure that your exact commands are perfect. Sorry.  On an empty partition, it really isn't much to risk, assuming sda3 really is the correct partition.

For anything complex, I'll create some VM storage (the number matching what I plan, just much smaller sizes) and boot an Ubuntu disto ISO into that VM with the storage needed.  Then I test/practice it.  Basically, zero risks that way.

It is also a good idea to leave some space for snapshots to be used during backups.  How much is needed depends on how much data changes during that period. Could be that 1G is plenty or 10G could be tight. Just depends.

I'd also recommend consideration for backup storage whenever setting up new storage.  I have a rule. If I can't backup the primary storage, then I won't make it available. Around here, backups are NOT optional.  I learned that the hard way.

---

### Post by Dennis N on 2018-03-30
> And last my logical volume(s) (450G for data storage)
```
sudo lvcreate -n data -L 450g lvm
```

Don't forget, there is another step: you need to create a file system for your logical volume before it can be used.

---

### Post by cruzer001 on 2018-03-31
Hello TheFu
I'll have to give some thought on new names.  I didn't run across any howtoforge guides, my search pretty much stopped at redhat where I did find a very detailed guide.

[https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/logical_volume_manager_administration/index](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/logical_volume_manager_administration/index)

This will replace my ext4 backup partition which I'll keep around for a while.

@Dennis N
Thank you!  I did not know there was yet one more step.  I think gparted can handle that.

---

### Post by TheFu on 2018-03-31
gparted doesn't understand LVM.

There is another step - you have to mount the storage.  That just means treating the LV like a partition ... though I've never seen UUIDs used to mount LVs.

I don't find that RH docs all that useful most of the time, but for LVM stuff, it is the same on all Linux from the shell.  Should be fine.  The RH docs make some assumptions that are valid for RH installed systems by RH trained people. Often, Debian stuff is a little different.  [https://www.howtoforge.com/linux_lvm](https://www.howtoforge.com/linux_lvm) is what I was thinking.

---

### Post by cruzer001 on 2018-03-31
> I don't find that RH docs all that useful most of the time
Same here, one reason I started this thread.

I was under the impression that gparted could handle lvm, back to the drawing board on that one.  I do want to find a gui for all this, should be one out there.

And that is a most comprehensive guide, have to read through it also.  Going to keep it simple for now, just one partition.

After I get my honey do list finished today I'll get on this.

Thanks

---

### Post by TheFu on 2018-03-31
I've seen 1 LVM gui and it only supported viewing the data, not modifying it.

GUIs don't work on non-gui-servers, so there isn't much push for it in my mind.  Plus people interested enough to deal with LVM complexities tend to be admins.

Good luck. Would be helpful if you find a GUI to post it back here.

---

### Post by Dennis N on 2018-03-31
> I do want to find a gui for all this, should be one out there.

A gui tool is **system-config-lvm**. If you are using 16.04 then it is in the Ubuntu repository. Since then, it's been removed for some reason. I've looked at it, but decided to stick to terminal commands for the lvm work.

---

### Post by cruzer001 on 2018-04-02
It's done :)  Thank you both for your input, it really helped me.  I made some last minute partitioning changes and it ended up like this:

```
# pvcreate /dev/sda4
# vgcreate mylvm /dev/sda4
# lvcreate -n data -L 250g mylvm
# mkfs.ext4 /dev/mapper/mylvm-data
```

Leaving me 250G of free space on the lvm partition.

My new data partition automounts from "sdb" just like I want it to, but I did not need to make a fdisk entry.  Plus everything I read indicated a mount point was necessary, which I did not create.  I don't understand that, but like I say it works.

I took a look at system-config-lvm.  Upstream support was dropped long ago and Ubuntu devs have now dropped it because of Wayland incompatibility.  I'm running 18.04 so I guess cli will have to do for now.

Thanks again

---

### Post by Dennis N on 2018-04-02
In Ubuntu /etc/fstab at least, you don't need to create the mount point first. If it does not exist, it is automatically created. In other systems, that is not true - Fedora, for example, is one. Like you, I learned this by accident when I neglected to make a mount point folder before using my fstab entry. However, with the mount command, you do need to have an existing mount point.

---

### Post by cruzer001 on 2018-04-02
Right you are, mystery solved :)

At some point in the future I will install other distros to this.  Have any tips on that?

Thanks

---

### Post by TheFu on 2018-04-02
> **cruzer001 said:**
> Right you are, mystery solved :)

At some point in the future I will install other distros to this.  Have any tips on that?

Thanks

Best to assume a mount point isn't made. For all we know, that is a bug in the current mount.
Other tips? chown for the mounted location to be whatever you need, while retaining the least permissions necessary.
For non-OS storage, when you make the file system, it might be good to reduce/zero the reserved inodes that only root can use.  tune2fs /path/to/lv  or device-with-file-system will show it.
For example:
```
sudo tune2fs -l  /dev/mapper/ubuntu--vg-root|grep -i reserv

``` that's an 'el', not a one (1) or eye (I).

I never mount anything permanently under either /mnt/ or /media/.  Been burned.

Whenever mounting backup storage, be certain it worked and have your backup scripts validate the expected device was actually mounted.  Been burned.

Check SMART data weekly.  Keep versions for each disk for at least a month. Monitoring any changes over time is the key to avoiding almost 80% of the failed-disk surprises.  About 22% fail without any warnings, sadly.

There are thousands other things, but they come over time via experience.  Having a mentor or being on a team help with this. When all the admins on a team quickly chat about things they are doing for the first time, that experience knowledge is shared exponentially.  It is much harder to learn when working alone.

---

### Post by cruzer001 on 2018-04-02
@TheFu

A big thanks for that!  I do appreciate the tips.
> I never mount anything permanently under either /mnt/ or /media/. Been burned.
I do use /media for my permanent mounts.  When 18.04rc (or later) comes out I will wipe the disk (sdb) and reinstall and maybe then move my mount points to my home directory.  Just because backing up my home directory is 90% of my backup plan, would be a nice touch to have all mounts there.

---

### Post by TheFu on 2018-04-02
> **cruzer001 said:**
> @TheFu

A big thanks for that!  I do appreciate the tips.

I do use /media for my permanent mounts.  When 18.04rc (or later) comes out I will wipe the disk (sdb) and reinstall and maybe then move my mount points to my home directory.  Just because backing up my home directory is 90% of my backup plan, would be a nice touch to have all mounts there.

I think mounting storage under any userid HOME is also a not-so-great idea.  I mean like /home/thefu/data for the mount point. The main reason for NOT mounting extra storage under a HOME is because most people don't usually include separate backup storage in their plans.  
Use a symbolic link to get around that, if you want easy access to the storage, or mount /home/ using the other storage, which is a "best practice."  

Perhaps we are saying the same things?

I played with the alpha last month for a week.  Probably won't touch it until July, so the initial ooops bugs get handled before I see it.  I just migrated most of my remaining 14.04 systems to 16.04 in Feb. ;)  Most were pretty easy, but a few weren't and took a few days to fix.  I did my bleeding edge time with Linux in the 1990s. Almost everything had to be custom compiled back then.

---

### Post by Dennis N on 2018-04-02
I have 5 OS installed in multiboot LVM setup on this machine. There are also 2 other OS on standard partitions on the same disk, done before I was converted last year to preferring LVM.

Just repeat what you did for the first LVM install and create the new logical volume first, then use the "Something Else" choice for installation type. The detected LVs appear at the top of the partitioning screen. 

```
dmn@Sydney:~$ lsblk -o name,fstype,label
NAME                   FSTYPE      LABEL
sdb                                
&#9500;&#9472;sdb1                 vfat        EFI
&#9500;&#9472;sdb2                 ext4        Manjaro-XFCE
&#9500;&#9472;sdb3                 ext4        Manjaro-MATE
&#9500;&#9472;sdb4                 vfat        EFI
&#9500;&#9472;sdb5                 LVM2_member 
&#9474; &#9500;&#9472;os_vg-mint_xfce    ext4        Mint-XFCE
&#9474; &#9500;&#9472;os_vg-mint_mate    ext4        Mint-MATE
&#9474; &#9500;&#9472;os_vg-korora_gnome ext4        Korora-GNOME
&#9474; &#9492;&#9472;os_vg-umate_1710   ext4        Ubuntu-Mate-1710
&#9500;&#9472;sdb6                 vfat        EFI
&#9492;&#9472;sdb7                 LVM2_member 
  &#9492;&#9472;os_vg-ubuntu_1710  ext4        Ubuntu-1710

```

---

### Post by TheFu on 2018-04-03
1 last tip - while you can merge storage, an LV, going across different PVs on different disks, don't, unless you have a backup solution that handled the entire LV size.  About 15 yrs ago, I merged 3 HDDs into a single LV, concatenated, not striped.  Worked great until 1 of those disks failed.  I wasn't as familiar with LVM then, didn't have good backups, and lost all the data on all 3 disks.  About 80% of my data at the time. That taught me to get backup religion and not to span file systems across physical disks.

Today, I limit any file system to 4TB - an easy size for backup storage. Use RAID1 and RAID10, but not RAID5/6. RAID 5/6 on large (2T+) HDDs is counter productive at restore time.  Nothing you probably don't already know. 

I've been disappointed with Ubuntu's installation storage config options. Getting multi-boot with encryption and LVM working seems impossible.  I have resized the encrypted partition later - what a pain since the calculations have to be guessed.

---

### Post by cruzer001 on 2018-04-03
Again, thank you both.

I'm feeling pretty good about how this turned out and doubt that I will have any other expansion needs.  Both laptop and desktop have two drives (hdd & ssd) backing up each other and not going to combine them.  Now that I know extra distros will work easily, I'm all set and this project is complete.

Thanks again for all the help.

---

