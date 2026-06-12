---
title: "Change from LVM to EXT4"
date: 2022-05-18
forum: General Help
---

### Post by kosta88 on 2022-05-18
Hello,

just out front: I am  only 1 year Linux user so...

One my 3 Linux servers that I set up a year ago, I created LVM partitions (default setup). I however don't need that, not nearly, as far as I understand it.
I would like to revert to simple EXT4 partitions.
Is there a relatively simple procedure that I can follow? Logically, coming from windows, I would have to create a new EXT4 partition, copy data, change some reference (under windows it would be a drive letter).

Thanks
Srdan

---

### Post by TheFu on 2022-05-18
No simple method.  Sorry.   LVM provides so much more flexibility and you still have ext4 LVs, so I'd question the desire to remove LVM.  90% of the time, in these forums, people want to add LVM for some of the features provided.  I've not seen anyone before you ask to remove it.

But, before we say it is extremely difficult, if you will post the output from these commands, we'll actually have some facts on which to base the answer.
```
sudo parted -l /dev/sd[a-z]
sudo pvs
sudo vgs
sudo lvs
lsblk -e 7 -o name,size,type,fstype,mountpoint
df -hT -x squashfs -x tmpfs -x devtmpfs
```

If you don't use code tags in the post, I won't answer. Too hard to read without them. Please show the exact command and output.  When you post, if it doesn't look like the block above, then the code-tags aren't correct.

But I'd really encourage you to seek a solution for storage that includes LVM.

Now, if you wanted to move from LVM+ext4 into ZFS, I could see that making sense, though I'd still push for LVM to be used for the OS parts and ZFS only for use with data.  There are different opinions on this.

---

### Post by kosta88 on 2022-05-18
> [COLOR=#000000]I'd question the desire to remove LVM[/COLOR]

This is relatively simple to answer: administrative overhead and complexity for something I don't need. Or better said: I don't see the need. And I see I am only confused by it (complexity) and annoyed when I want to do simple tasks like resize the partition (which I did couple of times according to some online tutorial, but really, holy c...).
As far as ZFS etc, I really have no need at this level. I have a server running disks in ZFS and TrueNAS + Synology 8-bay NAS. Those are all for data-storage and backups. The only high performing piece is the server based on Intel Xeon Silver, ECC RAM and NVME with ESXi. So to minimise any administration overhead, I think it is in my best interest to go from LVM to EXT4. That's the way I see it.

As for the results of those commands:

```

root@nextcloud:/# sudo parted -l /dev/sda
Model: VMware Virtual disk (scsi)
Disk /dev/sda: 21.5GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2097kB  1049kB                     bios_grub
 2      2097kB  1076MB  1074MB  ext4
 3      1076MB  20.0GB  18.9GB




Model: VMware Virtual disk (scsi)
Disk /dev/sdb: 21.5GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  20.0GB  20.0GB  ext4




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-ubuntu--lv: 18.9GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system  Flags
 1      0.00B  18.9GB  18.9GB  ext4




root@nextcloud:/# sudo parted -l /dev/sdb
Model: VMware Virtual disk (scsi)
Disk /dev/sda: 21.5GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2097kB  1049kB                     bios_grub
 2      2097kB  1076MB  1074MB  ext4
 3      1076MB  20.0GB  18.9GB




Model: VMware Virtual disk (scsi)
Disk /dev/sdb: 21.5GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  20.0GB  20.0GB  ext4




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-ubuntu--lv: 18.9GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system  Flags
 1      0.00B  18.9GB  18.9GB  ext4


root@nextcloud:/# sudo pvs
  PV         VG        Fmt  Attr PSize  PFree
  /dev/sda3  ubuntu-vg lvm2 a--  17.62g    0 


root@nextcloud:/# sudo vgs
  VG        #PV #LV #SN Attr   VSize  VFree
  ubuntu-vg   1   1   0 wz--n- 17.62g    0 


root@nextcloud:/# sudo lvs
  LV        VG        Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  ubuntu-lv ubuntu-vg -wi-ao---- 17.62g    


root@nextcloud:/# lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                       SIZE TYPE FSTYPE      MOUNTPOINT
sda                         20G disk             
&#9500;&#9472;sda1                       1M part             
&#9500;&#9472;sda2                       1G part ext4        /boot
&#9492;&#9472;sda3                    17.6G part LVM2_member 
  &#9492;&#9472;ubuntu--vg-ubuntu--lv 17.6G lvm  ext4        /
sdb                         20G disk             
&#9492;&#9472;sdb1                    18.6G part             /mnt/disk2-part1

root@nextcloud:/# df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem                           Type  Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-ubuntu--lv    ext4   18G  8.1G  8.5G  49% /
/dev/sda2                            ext4  976M  237M  673M  27% /boot
192.168.110.101:/volume1/NAS-Storage nfs4   22T   21T  1.3T  95% /mnt/nas
192.168.110.101:/volume1/nextcloud   nfs4   22T   21T  1.3T  95% /mnt/nextcloud-data
/dev/sdb1                            ext4   19G   24K   18G   1% /mnt/disk2-part1

```

Note that sdb is a partition I created to mount as a second partition to copy data. That's about it.

---

### Post by TheFu on 2022-05-18
LVM makes resizing trivial!  It is 1 command, 5 seconds. Zero downtime, even for the file system being resized.
If that isn't your experience, then you are doing it wrong.  You shouldn't have to touch any partition.  LVM frees us from dealing with partitions.

```
# sudo pvs
  PV         VG        Fmt  Attr PSize  PFree
  /dev/sda3  ubuntu-vg lvm2 a--  **17.62g**    0 
```
That's pretty odd.  If you have a 500G physical HDD, then the PV should be 500G, the VG should be 500G and then you'd make different LVs as small as possible to start inside the VG.

```
# lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                       SIZE TYPE FSTYPE      MOUNTPOINT
sda                         **20G disk**             
&#9500;&#9472;sda1                       1M part             
&#9500;&#9472;sda2                       1G part ext4        /boot
&#9492;&#9472;**sda3                    17.6G** part LVM2_member 
  &#9492;&#9472;ubuntu--vg-ubuntu--lv 17.6G lvm  ext4        /
```

If you want 1 partition, that sorta defeats the reason for partitions or LVM.  There are some security reasons why this isn't a good idea. There are some different mount options that should be used for different file system mounts. That isn't possible when only 1 huge file system is created. This is very important for Linux server security.

20G is much too small for a Desktop Ubuntu, I'm sad to say.  40G is about the minimal.  For Ubuntu servers, we can get down to 1.3G, if there isn't any data. A more typical size is 8G for servers with a little data.  My nextcloud VM has 20G connected with a few TB from NFS.  The OS is using 14G and 1G seldom used swap.  Oddly, I set that up without LVM inside the VM, but the VM sits in block storage provided using LVM on the host system.

The way to move from LVM to non-LVM is to use your normal file-based backup method - the method you'd use to restore to completely different physical hardware. In the method I use, the underlying storage is completely unimportant.  For 20G, the restore process would be less than 30 minutes, with 15 minutes taken doing a fresh minimal Ubuntu install.

BTW, I was in a similar situation when I move a 16.04 desktop to 20.04.  The bloat in 20.04 was tremendous.  I ended up adding another LVM-PV from a different virtual disk in the VM. Then I added that 2nd PV to the original VG and used the normal lvextend command with existing LVs.  All of this happened while the VM was running. Zero downtime.  Without LVM, that wouldn't be possible.  I use KVM-QEMU for my hypervisor, but that probably doesn't matter. KVM with virt-manager compares to VMware ESXi and vSphere.

OT: BTW, since this is a VMware VM of some sort, why not use virtio disk controllers for the VM?  It is more efficient than using virtual SATA or SAS controllers.

---

### Post by kosta88 on 2022-05-18
> [COLOR=#000000]LVM makes resizing trivial! It is 1 command, 5 seconds.[/COLOR][COLOR=#000000]
Say what?
[/COLOR][How to resize an Ubuntu 18.04/20.04 LVM disk » Vander Host Knowledgebase]("https://kb.vander.host/operating-systems/how-to-resize-an-ubuntu-18-04-lvm-disk/")

> [COLOR=#000000]If you have a 500G physical HDD[/COLOR][COLOR=#000000]
Who said anything about 500G physical HDD? I have an ESXi Host, which has 1TB flash NVME. I am adding and expanding disks as necessary in vCenter.

[/COLOR]> [COLOR=#000000]20G is much too small for a Desktop Ubuntu, I'm sad to say. 40G is about the minimal.
Sorry if misunderstood, OS is Ubuntu Server, currently on latest version 22.04.

[/COLOR]> [COLOR=#000000]OT: BTW, since this is a VMware VM of some sort, why not use virtio disk controllers for the VM? It is more efficient than using virtual SATA or SAS controllers.
[/COLOR][COLOR=#000000]What do you mean by "virtio"? I use LSI Logic Parallel, this is what vCenter sets as default for Linux. There is VMware Paravirtual, not sure if that works with Linux, I only know it needs drivers. And current googling says it's recommended. I'll see what that's about.

[/COLOR]> [COLOR=#000000]The way to move from LVM to non-LVM is to use your normal file-based backup method - the method you'd use to restore to completely different physical hardware. In the method I use, the underlying storage is completely unimportant. For 20G, the restore process would be less than 30 minutes, with 15 minutes taken doing a fresh minimal Ubuntu install.
[/COLOR][COLOR=#000000]I will have to look up what you mean by that. If I understand correctly, you are saying I should install a new Ubuntu server without LVM and then restore the data on /, right?[/COLOR]

---

### Post by TheFu on 2022-05-18
> **kosta88 said:**
>  I will have to look up what you mean by that. If I understand correctly, you are saying I should install a new Ubuntu server without LVM and then restore the data on /, right?

Yep. If you want to remove LVM, that's the answer.

My company used to deploy ESXi for clients, but we stopped in 2011 when VMware license changes were going to cost 3x more.  Before the license renewal date, we moved all to KVM with Libvirt and virt-manager.  No regrets today. It was an excellent choice. Clients are happier.  Even the nearly 100% MS-Windows Server companies, though we did switch their file and print servers to Linux too (sssssh, don't tell them).

Running inside a VM just means there are many, many, more options to add storage. LVM can make that fairly quick and easy too.  
[Https://ubuntuforums.org/showthread.php?t=2444855&p=13963156#post13963156](Https://ubuntuforums.org/showthread.php?t=2444855&p=13963156#post13963156) is 1-way how.  

If I could tolerate downtime, there are all sorts of options with increasing the block storage from the VM host, using gparted from alternate boot media to either add another partition in the storage or resize the partition to be larger.  I probably would just add another partition, create a PV on it, add that new PV to the VG, then use normal lvextend or lvcreate to make new LVs.  I'd also leave 5G inside the VG unallocated to any LV for use as snapshot storage and emergency need storage, for the next time space becomes tight in any LV on in the system.  That would be the 5 second lvextend that to get the storage working until the next maintenance window for adding more vHDD, new PV, extending the VG with the 3rd PV, .... yadda, yadda, yadda.

With the first extension, I'd specifically split off the OS, /var and data into separate LVs.  Also, I'd put the small swap into an LV too. 

Almost too many choices, but only if LVM is there.

---

### Post by kosta88 on 2022-05-18
> [COLOR=#000000]If I could tolerate downtime, there are all sorts of options with increasing the block storage from the VM host, using gparted from alternate boot media to either add another partition in the storage or resize the partition to be larger. I probably would just add another partition, create a PV on it, add that new PV to the VG, then use normal lvextend or lvcreate to make new LVs. I'd also leave 5G inside the VG unallocated to any LV for use as snapshot storage and emergency need storage, for the next time space becomes tight in any LV on in the system. That would be the 5 second lvextend that to get the storage working until the next maintenance window for adding more vHDD, new PV, extending the VG with the 3rd PV, .... yadda, yadda, yadda.

And you see, this is exactly why I tend to leave it. What you just wrote is for me right out gibberish. As I said, I am a senior IT admin in a windows world, I know my ins and outs in AD and lots in the world of VMware, but when it comes to Linux, I am at the basics. Being 43, I barely have time to keeping up with even that, beside the family and some hobbies. So, a tendency on my side to keep it simple is hopefully clear. I manage my Linux machines at home which do nothing else but host 12 docker containers, and another for Unifi controller. And at work, we also have some Linux machines, but all are managed by external partners, we have 0 time to work ourselves into that.[/COLOR]

---

### Post by Tadaen_Sylvermane on 2022-05-18
Ok to put simple. That guide you linked is a joke. A properly partioned drive for lvm has 2 partitions. One is either mbr or efi. The rest ends up being you pv. Sounds to me like you partitioned like normal then put lvm on each partition which is indeed pointless and over complicated. Lvm isn't the problem. Use either or. Never both. Either standard partitions or lvm on a single one. 

Lvm when done correctly makes using standard partitions a laughable joke of an idea...

[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

That guide is written by a fool if they find all that stuff necessary. It's only necessary if you did it wrong in the first place.

---

### Post by kosta88 on 2022-05-18
I didn't "do" anything. I installed Ubuntu server and left it as it is. It used the space of the VM disk I assigned in vCenter and that's it. As for sdb, you can ignore that, because that is what I created today when attempting to create a simple EXT4 partition. I added a 2nd disk in vCenter and created partition with parted. That's it.

---

### Post by Tadaen_Sylvermane on 2022-05-18
My apologies. Didn't mean to insult. The default Ubuntu thing is... not great imho. Manually is much better I think. I think we can fix this. Eliminating lvm is the wrong answer here. A strictly hypothetical - You can add an unlimited number of 5gb hard drives to your vm (or real machine?) and with lvm they are all one. Need 5 more gigs but don't want to create a 20g file? Create a 5g and add it to the lvm. Rinse lather repeat. Situation dictates of course. No pooling or merging software... no bs. This works for your root filesystem. It can do swap to. anything really. In the case of a vm this isn't a huge issue. With physical machines though be aware that more hard drives = more chances to fail. In the case of LVM think raid 0 data loss if a single disk fails. Hence... backups regardless of what you do that should be your priority depending on how essential said system is. Of course one could go on and on because you can also put lvm on top of raid. 2 raid 1 sets same thing as 2 individual drives but obviously with teh raid 1 for each pair.

First a flowchart

[https://www.tecmint.com/create-lvm-storage-in-linux/](https://www.tecmint.com/create-lvm-storage-in-linux/)

Steps to fix or extend LVM > sdb

All of this is using the gdisk command line program

Redo partition on sdb to include a 1MB bios partition in gdisk. create partition > size = 1M > type = ef02
Create another partition 1gb and make it type 8300 (default linux file system). this will be a backup boot partition which will just sit there. No need to format, just create and leave it alone.
Finally fill the rest of the space on dev sdb with a single partition, type 8e00

Once you've written your partition table your next pv should be /dev/sdb3? (confirm this)

Run the command

```
pvcreate /dev/sdb3
```

then this. Confirm vg name first.

```
vgextend ubuntu-vg /dev/sdb3
```

Finally extend your logical volume.

```
lvextend -L +15g /dev/ubuntu-vg/ubuntu-lv
```

What this has done is create another physical volume. A volume group is multiple physical volumes. Then you extended the existing volume group to include the new pv. And finally at this point as far as lvm is concerned you have now doubled your available space and need only extend your volume (or create others?) to fill the additional space.

Once you've extended your lv running this command will resize the filesystem to properly see the new lv space

```
resize2fs /dev/ubuntu-vg/ubuntu-lv
```

Again I apologize for insinuating anything. I know this can be frustrating. Delete the link to that guide....

Before running any of the aforementioned commands be sure you are doing the correctly. Proper /dev/sd? device and numbers... vg and lv names of course.

All of this can be done live with zero need to reboot. For the record if you want to shrink logical volumes it isn't quite as easy but near as I can tell that happens practically never in any logical scenario. Once LVM clicks in your brain you will wonder how any computer can operate without it's features. Also always leave some free space in your volume group. This allows live snapshots that can be mounted and backed up while the system continues on it's merry way.

---

### Post by TheFu on 2022-05-18
> **kosta88 said:**
> And you see, this is exactly why I tend to leave it. What you just wrote is for me right out gibberish. As I said, I am a senior IT admin in a windows world, I know my ins and outs in AD and lots in the world of VMware, but when it comes to Linux, I am at the basics. Being 43, I barely have time to keeping up with even that, beside the family and some hobbies. So, a tendency on my side to keep it simple is hopefully clear. I manage my Linux machines at home which do nothing else but host 12 docker containers, and another for Unifi controller. And at work, we also have some Linux machines, but all are managed by external partners, we have 0 time to work ourselves into that.

I wrote that in that way because I'd assumed you were a Linux admin above beginner based on prior posts in this thread. Sorry.
In the link I provided to ubuntu forums, I showed the exact LVM commands that I used. All the other commands, that I didn't show, you seem to already know.

I also wrote that paragraph sorta as a joke, since it isn't what I've done.  The only answer to remove LVM from the OS part of a system is to perform a fresh install. Period.

But I still have hope that you'll solve the immediate issue. You've already added some extra storage. If you tagged that as LVM, used **vgextend** to add the new PV to the existing VG, they just expand the existing LV, perhaps 5G to free up some space.  Since sda and sdb are physically on the same SSD, the warnings against putting LVs on different disks that aren't for RAIDx reasons don't really matter.  If sda and sdb were on different disks, if either failed, you'd lose everything, like RAID0 would cause, even with concatenated LVs. That could be it for now. 2 commands.  If you wanted to make it prettier, then you'd likely want to make a separate /var, /home, and /where-ever-your-nextcloud-data-directory-is.  This should be different from the nextcloud php scripts, BTW.  I use /opt/nc-data, as an example, but ... anything outside /var/www/ or /home/ should be fine.

We all have different skills. I know very little about MSFT the last decade. Prior to that, I knew some high-level stuff and enough point-n-click to get by as a programmer.  Different needs demand different skills. Nothing wrong with that.  I've run LDAP directories for a few small companies as a centralized authentication system for most login needs. We didn't use AD.  Only had 1 Windows system in the entire company - for Quickbooks. Some fights just aren't worth fighting. Don't mess with the system that gets people paid. That's a big rule, but we did move it into a virtual machine off a non-secure desktop. The accountants used x2go to access it. Getting them setup for that access was a chore. Accounts are good at money, not so much with computers. Obviously, not all accounts are bad with computers. Ours just wanted to know what to type. They didn't care why.

Docker isn't really Linux, unless you are building the containers yourself and rebuilding them every time you need to refresh things (should be weekly).  That's more like inserting a plug into a wall socket, IMHO.  The main risk of linux containers that we don't create ourselves is that the vast majority are from unknown sources.  Getting a docker container directly from the same project team that makes the F/LOSS software it runs is different. We're already trusting them.  But getting a container from some 3rd party is scary.  It's like downloading setup.exe from bittorrent. Completely untrustworthy, IME.

---

### Post by kosta88 on 2022-05-18
No, I don't want to extend 1st volume on second. I don't want additional PVs for my usage. I have 10GB disk, a single one, and I want to make that 15GB. Why would I want to add another PV to the LVM, just for the sake of it? Way simpler is to just make the disk in vCenter bigger, and extend in the OS.

---

### Post by kosta88 on 2022-05-18
> **TheFu said:**
> I wrote that in that way because I'd assumed you were a Linux admin above beginner based on prior posts in this thread. Sorry.
In the link I provided to ubuntu forums, I showed the exact LVM commands that I used. All the other commands, that I didn't show, you seem to already know.

I also wrote that paragraph sorta as a joke, since it isn't what I've done.  The only answer to remove LVM from the OS part of a system is to perform a fresh install. Period.

But I still have hope that you'll solve the immediate issue. You've already added some extra storage. If you tagged that as LVM, used **vgextend** to add the new PV to the existing VG, they just expand the existing LV, perhaps 5G to free up some space.  Since sda and sdb are physically on the same SSD, the warnings against putting LVs on different disks that aren't for RAIDx reasons don't really matter.  If sda and sdb were on different disks, if either failed, you'd lose everything, like RAID0 would cause, even with concatenated LVs. That could be it for now. 2 commands.  If you wanted to make it prettier, then you'd likely want to make a separate /var, /home, and /where-ever-your-nextcloud-data-directory-is.  This should be different from the nextcloud php scripts, BTW.  I use /opt/nc-data, as an example, but ... anything outside /var/www/ or /home/ should be fine.

We all have different skills. I know very little about MSFT the last decade. Prior to that, I knew some high-level stuff and enough point-n-click to get by as a programmer.  Different needs demand different skills. Nothing wrong with that.  I've run LDAP directories for a few small companies as a centralized authentication system for most login needs. We didn't use AD.  Only had 1 Windows system in the entire company - for Quickbooks. Some fights just aren't worth fighting. Don't mess with the system that gets people paid. That's a big rule, but we did move it into a virtual machine off a non-secure desktop. The accountants used x2go to access it. Getting them setup for that access was a chore. Accounts are good at money, not so much with computers. Obviously, not all accounts are bad with computers. Ours just wanted to know what to type. They didn't care why.

Docker isn't really Linux, unless you are building the containers yourself and rebuilding them every time you need to refresh things (should be weekly).  That's more like inserting a plug into a wall socket, IMHO.  The main risk of linux containers that we don't create ourselves is that the vast majority are from unknown sources.  Getting a docker container directly from the same project team that makes the F/LOSS software it runs is different. We're already trusting them.  But getting a container from some 3rd party is scary.  It's like downloading setup.exe from bittorrent. Completely untrustworthy, IME.

Thank you for your insights.
After reading up a bit about LVM, I now understand what it basically is: it's what MS has in it's world, Storage Spaces. It's the same principle. You have PVs which are put into VG, on which LV are created. Storage spaces does just that. And I wouldn't dream of wanting to use Storage Spaces here at home.
I simply see no benefit, even if it's a cool tech (and I *really *like cool tech).

I am aware Docker isn't "Linux". It just runs well under Linux and that's why I have it there. It also simplifies any kind of administration, which is positive in my case. I really only want it to run smoothly and fast, consume least possible resources and if I get to learn a bit of Linux along the way, I'm all for it. But trust me, if I need one and half days to update all my Ubuntu, resize some partitions, things get scary. And if it's unnecessarily complex, even worse. If I want to learn LVM, I will do that on standalone Linux VM on my own terms. But I need my services running (restart or short offline is no issue), and I have work that pays - my Linux at home does not ;-)

I am using Linuxserver Docker releases and all is well with automatic updates, as long as OS is up to date and there is space on disk :)

---

### Post by Tadaen_Sylvermane on 2022-05-18
> **kosta88 said:**
> No, I don't want to extend 1st volume on second. I don't want additional PVs for my usage. I have 10GB disk, a single one, and I want to make that 15GB. Why would I want to add another PV to the LVM, just for the sake of it? Way simpler is to just make the disk in vCenter bigger, and extend in the OS.

If it was simpler why did you post asking for help? Up to you of course but I can't help but see the irony there. I wish you the best.

---

### Post by TheFu on 2022-05-18
> **Tadaen_Sylvermane said:**
> If it was simpler why did you post asking for help? Up to you of course but I can't help but see the irony there. I wish you the best.

I assume he was hoping for there to be some magical method.  There is a magical method, with LVM, but there isn't a magical way to remove LVM.

There is something good to be said about K.I.S.S.  The trade-off is between future flexibility and simplicity.  For most of the world, storage isn't that tight and having 20G extra unused in a system provides tremendous flexibility, especially if LVM is used.  The OP isn't interested in that, which is 100% fine.

I remember the first time I heard that DOS used drive letters. That seemed like a really dumb idea to me. Limited to only 26 drives?  Why not just mount storage to an empty directory exactly where it is needed?  Plus we had over 100 disks connected to the servers. 26 wouldn't work.  Different perspectives, that's all.

BTW, MS-Storage Spaces is 30 yrs late.  LVM is based on Veritas VM which has been around since, at least the early 1990s. It is extremely standard, so much that AIX and HP-UX, and created their own versions modeled after Veritas' products.  LVM on Linux has been enterprise ready over 20 yrs that I know about.

Seems we've beaten this thread into submission. Good luck to all.  For the next people and lurkers, hope this is helpful.

---

