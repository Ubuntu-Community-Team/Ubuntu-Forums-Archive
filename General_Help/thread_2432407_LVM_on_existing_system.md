---
title: "LVM on existing system"
date: 2019-12-02
forum: General Help
---

### Post by zkab on 2019-12-02
I have Ubuntu 18.04.3 LTS on a Samsung SSD EVO 960 and have used the entire disk when I install Ubuntu.
Now I am running out of space and want to add another SSD and also take advantage of LVM.
My question is if I can use the existing disk to install LVM without destroying data and after that include the new SSD.
I have as follows:

~$ ls -la /dev/nvme0*
crw------- 1 root root 240, 0 dec  2 11:45 /dev/nvme0
brw-rw---- 1 root disk 259, 0 dec  2 12:07 /dev/nvme0n1
brw-rw---- 1 root disk 259, 1 dec  2 12:07 /dev/nvme0n1p1
brw-rw---- 1 root disk 259, 2 dec  2 12:07 /dev/nvme0n1p2

~$ df
Filesystem     1K-blocks      Used Available Use% Mounted on
udev            15376396         0  15376396   0% /dev
tmpfs            3086696      1492   3085204   1% /run
/dev/nvme0n1p2 238798492 151905908  74692548  68% /
tmpfs           15433472     69540  15363932   1% /dev/shm
tmpfs               5120         4      5116   1% /run/lock
tmpfs           15433472         0  15433472   0% /sys/fs/cgroup
/dev/nvme0n1p1    523248      6232    517016   2% /boot/efi
tmpfs            3086692        16   3086676   1% /run/user/1000

Can I make 'sudo pvcreate /dev/nvme0n1p1' without destroying my boot&system disk /dev/nvme0n1?

---

### Post by TheFu on 2019-12-02
> **zkab said:**
> 
My question is if I can use the existing disk to install LVM without destroying data and after that include the new SSD.
....
 Can I make 'sudo pvcreate /dev/nvme0n1p1' without destroying my boot&system disk /dev/nvme0n1? 


No.

You can setup LVM on the new storage, however.

OTOH, if your backup and recovery method doesn't allow easily backing up from 1 system and restoring to another, with different storage, networking, CPUs, and motherboard, then I'd say you need a better backup technique.

But that is just me.

---

### Post by zkab on 2019-12-02
OK ... so LVM should always be created on new disks ...
After I started this thread I saw in 'https://wiki.ubuntu.com/Lvm' following:
'You can install the lvm2 package on an existing system, or the desktop livecd and manually set it up, and then install to it.' 
Doesn't that mean it can be installed on existing systems or have I misunderstood?

---

### Post by TheFu on 2019-12-02
Those are true, but "existing system" doesn't mean the same partitions already used without data being wiped. You have to backup the data, setup the LVM, restore the data.
Or
you can have a running system on 1 disk (A), add another disk (B), partition "B", create LVM PVs into 1 or more partitions on "B" and use it that way.  All without touching "A".  For example, 
```
sdd                                   7.3T disk             
&#9492;&#9472;sdd1                                7.3T part LVM2_member 
  &#9500;&#9472;istar--8TB-istar--back3--a        3.7T lvm  ext4        /misc/b-D3
  &#9492;&#9472;istar--8TB-istar--back3--b        3.6T lvm  ext4        /misc/b-D4
$ sudo vgs
  VG             #PV #LV #SN Attr   VSize   VFree 
  istar-8TB        1   2   0 wz--n-   7.28t **14.03g**
...
$ sudo lvs
  LV             VG             Attr       LSize   Pool Origin Data%   
  istar-back3-a  istar-8TB      -wi-ao----   3.65t                                                    
  istar-back3-b  istar-8TB      -wi-ao----   3.62t      

```
sdd is an 8TB disk.
sdd1 is a partition that fills the entire disk. It is also a PV.
istar-8TB is the VG that uses the total PV.
istar-back3-a and istar-back3-b are the LVs that take storage from the VG, just a little less than everything available.  This leaves room for an emergency increase where it is needed just before storage is really all used up.

Any LVM isn't a "disk" thing. It is a "Partition" thing.  Windows people seem to get those confused, because MSFT calls partitions "drives." This is factually incorrect.

---

### Post by zkab on 2019-12-02
OK ... thanks for your help ... I will study it carefully

---

### Post by TheFu on 2019-12-02
The stuff I posted in this thread was "for example", not any suggestion. 

To do an install so the OS leverages LVM is possible either using the manual setup stuff or just selecting "Use LVM on whole disk" (or something similar).  Post install, I immediately shrink the size of the root LV to 25G, create a /home LV (25G to start) and a swap LV (4.1G size), move over any /etc/fstab entries as needed (or not) and remove the swapfile that 18.04 and later use. With this basic setup, I'm ready to add more LVs where desired or increase existing LVs as needed, on-demand.  For some server-only machines that will never have user accounts, I won't bother with a separate HOME LV/partition. It isn't worth the hassle when there aren't any users.  All the "data" for those systems are stored elsewhere.

Don't forget to leave room for LVM snapshots, so clean backups can use snapshots.  For some systems, 1G is plenty, but others might need 10G or 100G - just depends on the amount of data changing while backups are happening. Often times, we forget to mention this.

**lsblk -o name,size,type,fstype,mountpoint** is an extremely handy command. I've made it an alias.
Same for **df -hT** - much better than a straight df.
Obviously, use **pvs**, **vgs**, **lvs** to get summary of LVM setups, but still need the lsblk alias above.

---

### Post by kevdog on 2019-12-03
@TheFu

Just curious if this strategy is the best when thinking forward.  Although LVM isn't going away, Ubuntu is moving toward ZFS.  ZFS has ability to create pools spanning several disks and has its own method of creating snapshots.  The only problem at this moment with using ZOL, is that it cant encrypt root since bootloader isn't capable of decrypting during startup.  Bootloaders at this point can decrypt LVM encrypted partitions at the time of boot. I'm just wondering your position on possibly recommending use of ZFS over LVM in terms of "future-proofness", particularly if user is going to start-over.

---

### Post by TheFu on 2019-12-03
I work with what we have today.  The future is unknown until 6 months after a stable release happens.  When it comes to data, I'm extremely risk-adverse.  Data is more important than hardware.  If I lose all my computers, it would suck, but as long as the data were available somewhere, it isn't the end of the world.  OTOH, without the data, what's the point of having any computer?

For someone new like the OP, trying to mix both LVM and ZFS could be confusing.  LVM will be used on boot and OS parts of systems for the foreseeable future.  ZFS on the data parts.  Eventually, ZFS will be the default, except on purpose built or constrained systems.

I want to see how well the upgrade process works for ZFS booted systems.  I'm hopeful, but want to see it working first, across thousands of other-people's-systems.  My systems aren't for debugging issues.  I did that in the 1990s. No more.  Stuff that is proven to work and all the hassles are understood is what I want. For OS areas, LVM has that, ZFS does not.

IMHO.

I ran JFS for years after ext3 was available and only switched to ext4 around 5 yrs after it was the standard. I completely expect it to become THE DEFAULT file system and volume management across all non-constrained Linux systems.  It has been the detail solution for LXD for some years.

---

### Post by kevdog on 2019-12-03
@TheFu

I understand your sentiments.  I get the hesitation with ZFS, however this filesystem has been used by oracle and BSD for a long long time.  I think the new part is the incorporation of ZFS on root with ZOL within Linux.  I get it might not be prime time yet for production systems, however I'm betting OP is running a home based system -- which is ideal for testing.  Would be even better if virtualized for testing.

---

### Post by TheFu on 2019-12-03
> **kevdog said:**
> @TheFu

I understand your sentiments.  I get the hesitation with ZFS, however this filesystem has been used by oracle and BSD for a long long time.  I think the new part is the incorporation of ZFS on root with ZOL within Linux.  I get it might not be prime time yet for production systems, however I'm betting OP is running a home based system -- which is ideal for testing.  Would be even better if virtualized for testing.

Oracle isn't a reference that impresses me.  I've dealt with them on a number of projects. The Sun Micro guys were good, but most left.  Oracle DBAs are great, if you use Oracle's DBMS. [https://www.theregister.co.uk/2019/12/04/oracle_product_manager_lawsuit/](https://www.theregister.co.uk/2019/12/04/oracle_product_manager_lawsuit/)

I started using ZFS at work around 2006/2007 on Solaris machines.  No issues with the Solaris or BSD implementations or the Linux 64-bit implementation for data use.  LXD stuff on Ubuntu uses it by default today.  It is all solid.

For larger data storage, ZFS is a viable option, I've just got so much on LVM+ext4 to make switching non-trivial.

My concern with ZFS is for OS and boot storage only, which is what this thread is mostly about. 

Remember when BTRFS was going to be the new default boot file system?  Then Redhat deprecated it and it lost favor across many distros?  SuSE is the main distro still using BTRFS, right?  I'm a wait-n-see guy.

There are lots of different solutions to this problem.  Only zkab can pick the best answer for the requirements.  ZFS for data is definitely a viable option.
LVM+ext4 is also a viable option.
ext4 or xfs are also viable options without any volume management.

---

### Post by zkab on 2019-12-05
Thanks for you input ... after I read your thoughts about ZFS vs LVM I will go for LVM.
But I need some advice from you experienced guys.
As mentioned before I have existing system on disk A.
My intention is to ...

1) add a new disk B and create PV for the whole disk B. Then create a VG that includes disk B:s PV
2) make a backup of disk A with 'tar -cvpzf backup.tar.gz --exclude=/backup.tar.gz --one-file-system /'
3)  create PV  for the whole disk A and add the new PV to the VG that already exists
4) create one LV for my VG
5) restore the tar-file to disk B:s LV
6) reboot

Will this work ?

---

### Post by TheFu on 2019-12-05
I can't tell what the goal of this exercise might be.  It might work, but I doubt it.   If you are trying to convert a non-LVM system into an LVM-system that boots from LVM storage, then no, this is not sufficient.  To boot LVM storage, there must be non-LVM areas for UEFI and /boot files. These must be configured with the ability to activate LVM VGs, discover LVs.  I don't know if that capability is automatic or manually setup.

The entire B disk cannot be one entire PV if you expect it to boot with no connections to the A disk.
If these are spinning disks, beware that having data spread across both disks either striped or concatenated means that when 1 disk files, all data is lost.  Disk failures happen all the time.  I had one start failing just before Thanksgiving.  One of my disks fails almost every year.  The most recent is a 4TB backup disk that is 5+ yrs old.  I have an 8TB replacement, just need to hook it up and make some decisions about moving some data around.

If you want a backup, use a backup tool, not tar.  tar was designed for use when huge disks were 20MB in size. It is a good choice for needs just like ZIP file would be used, but not for system backups.  Use tar when you want to sneaker-net some files using non-Linux file systems on a flash drive while retaining owner, group and permissions.  tar doesn't know anything about LVM or any file system.

Image backups : use fsarchiver or ddrescue or partimage or clonezilla to make the image files; These are normally used at the whole disk device or partition level, pulling the file system over with them.

File backups : use rdiff-backup or duplicity or Back-In-Time ;  if you use duplicity, be aware that full backups must be scheduled either weekly or monthly between the incremental backups.   The other two tools listed keep the full backup for the most recent version, with reverse-incremental backups as diffs.gz files going back in each older version. Limiting storage used is by removing the oldest versions of the reverse-incremental backups. Versioned backups will change your life and you will sleep much better.

If you want to copy files from A ---> B, use rsync.

Once you have LVM setup, you could use pvmove to migrate data from disk A to disk B.

What I would do is 
* create a file-based backup of my data, my settings, system data, system settings, and a list of manually installed packages.  This is my normal backup method using rdiff-backup.  If the file system supports it, I'd use an LVM snapshot.  If not, I'd stop all DBMS processes, stop any web servers, stop any massive programs like thunderbird which keeps files open.
* Perform a fresh install of the OS version I want, choosing LVM during the install process to which ever disk I want to hold the boot information. I would ignore the other disk completely.
* At first reboot on the new OS install, I'd resize the LVs to the sizes I need, clearly keeping / (25G) and /home (25G to start) and other storage areas in separate LVs.  Having 1 huge LV is an anti-pattern. It should be avoided. The power of LVM comes by extending the file system as needed, not making it huge to start.
* Restore my data, settings, system data, system settings to the directory locations required. Files under /etc/ will need to be selectively restored so LVM and disk settings aren't harmed.  But settings like a DNS-over-HTTPS proxy or system power settings previously solved should be restored.
* Lastly, feed my list of manually installed packages into the package manager for installation. As these packages see the prior settings, they will see the prior data, and accept the settings and data as needed.  
* Bam! You have YOUR system back. A system that doesn't require backing up program files saving about 4G of backup storage.  It is flexible about the underlying storage ... so you can change it out for ZFS or Sheepdog replication or move to a VM or move to a physical install or change the entire system out as you like with minimal worry.  This restore should take about 30-45 minutes, not counting any huge media files which should be restored last, after everything else is finished. 

That's what I would do.  Well, really I'd pull disk A out of the machine. Put Disk B in and do the fresh install there with LVM.  Then resize the LVs as needed and restore the backup data.  I'd ignore disk A completely until "B" was working exactly and my backup restore process was 100% validated onto the LVM using OS.

Around 2002, I was using LVM to concatenate a single LV across 3 physical disks.  I didn't have backup religion at the time. I was stupid.  One of those disks failed, doesn't matter which one. LVM freaked out and all data in the same LV was lost.  That experience taught me a few things.  
* Don't make LVs larger than what the backup storage can handle.  At the time, I had a 250GB (or was it MB) tape drive. Backups were a pain and would take a very long time.
* Don't merge file systems across different physical devices unless it is for RAID1, RAID10, RAID5 or RAID6 purposes.
* Don't use RAID0 or concatenation across different physical devices!
* Have current, versioned, daily, automatic, backups where the restore has been validated to work.  Initially, setting this up took me 5 attempts or so. A few times, I had the cart, but no horse problem. Then I had a chicken, but no egg.  The order and what gets backed up matters.  There are settings and metadata about the system which I gather daily to be included in my backups. Things like all the crontabs for users which aren't stored in /etc/.  Having disk, partition, and LVM information is helpful if you want to recreate what was there before.  People accidentally delete partition tables all the time, but don't harm any data.  With a machine-readable partition table saved, putting it back exactly like it was is relatively easy.  Without that data, well, humans will guess and be close, so getting most of the data off into a backup will work, but a new system install will be necessary.  You get the idea.

But it is your box, not mine.

---

### Post by zkab on 2019-12-06
Thanks for your comprehensive reply ... most valuable to me.

---

