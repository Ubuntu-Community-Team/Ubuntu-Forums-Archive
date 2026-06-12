---
title: "Moving OS &amp; data to new disks - question"
date: 2020-03-01
forum: General Help
---

### Post by michael351 on 2020-03-01
I have two 1 TB disks mounted as a logical volume with Ubuntu installed in its own partition ext4 filesystem. OS + data are not mirrored.

Recently - these disks are showing bad sectors and I need to migrate off them. 

I have two 2 TB disks on order. I do not have extra bays to install the new drives (1u server). Currently Total OS + data only occupies < 1TB of space on the original drives, 
so I was thinking of removing on 1 TB drive and replace it with the new 2 TB drive and move the OS over to it somehow.

I need suggestions on the best way to do this and appreciate any help. This is the first time I'm messing with logical volumes and disk replacement.

---

### Post by HermanAB on 2020-03-01
I think you should read up on fsarchiver.

---

### Post by oldfred on 2020-03-01
I am a believer in new install. 
That does a major housecleaning that even my regular houseclean does not seem to do.
Avoids issues of duplicate UUIDs & if gpt duplicate GUIDS & issue of backup gpt not at end of drive.

But do not know LVM, does it span both drives as one LVM? Then not sure you can disconnect one drive.
Post this, so someone that knows LVM knows your exact configuration.

sudo parted -l

---

### Post by SeijiSensei on 2020-03-01
When dealing with new disks, I've found a SATA-to-USB connector really helpful.

[https://www.newegg.com/p/pl?d=sata+to+usb](https://www.newegg.com/p/pl?d=sata+to+usb)

You don't even need to open the case. Just connect the new drive to the USB port via the adapter, and you can format it and copy over the stuff you need.

Another option is to use ddrescure (in the gddrescue) package to make a bit-by-bit copy of the existing drive to the new medium. I've only done this with media of the same size. I migrated two laptops to SSD drives by connecting the new drive with the adapter and running ddrescue.  The clones behaved exactly like the original SATA drives I was replacing. Don't know how that works when the target device is larger than the source device, but I'm sure the documentation will help.

---

### Post by TheFu on 2020-03-01
**pvmove**.  It is pretty simple.  Use the built-in LVM commands to make your life easier.  
Use a USB dock for the new disk(s) if you must 
or 
boot from an  "Try Ubuntu" flash disk, install the lvmtools into that environment, activate the VGs - **sudo vgchange -ay**, then use pvmove.
You should be able to figure out the rest.

I wouldn't allow any LV to cross physical disks unless my backups were 100% perfect.  Failing disks means we need to have great backups BEFORE trying anything else.

If you want more advice, we need more data.
```
sudo pvs
sudo vgs
sudo lvs
```
   and 
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```
Clearly, RTFM on pvmove first.  I've used it a few times.  Freakin' amazing.   Stuff like this is why we use LVM, right?
I mount LVM storage using LV paths.  If you use a LABEL or UUID, those might need to be fixed. I don't know.

---

### Post by michael351 on 2020-03-01
These are the disks I need to replace:

> # parted -l
Model: ATA ST31000340NS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1075MB  1074MB  primary  ext4         boot
 2      1075MB  1000GB  999GB   primary               lvm


> Model: ATA ST31000340NS (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags

 1      1049kB  1000GB  1000GB  primary               lvm



> # pvs
  PV         VG Fmt  Attr PSize    PFree
  /dev/sda2  cl lvm2 a--  <930.51g    0
  /dev/sdb1  cl lvm2 a--  <931.51g    0

]# vgs
  VG #PV #LV #SN Attr   VSize  VFree
  cl   2   3   0 wz--n- <1.82t    0

]# lvs
  LV   VG Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  home cl -wi-ao----  1.76t
  root cl -wi-ao---- 50.00g
  swap cl -wi-ao----  7.89g

# lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME          SIZE TYPE FSTYPE      MOUNTPOINT
sda         931.5G disk
&#9500;&#9472;sda1          1G part ext4        /boot
&#9492;&#9472;sda2      930.5G part LVM2_member
  &#9500;&#9472;cl-root    50G lvm  xfs         /
  &#9500;&#9472;cl-swap   7.9G lvm  swap        [SWAP]
  &#9492;&#9472;cl-home   1.8T lvm  xfs         /home
sdb         931.5G disk
&#9492;&#9472;sdb1      931.5G part LVM2_member
  &#9492;&#9472;cl-home   1.8T lvm  xfs         /home

---

### Post by TheFu on 2020-03-01
Please edit the post above and wrap all output in "_code tags_", so it is readable.  Too hard to read as is.

But I will say that xfs doesn't support all the same capabilities that ext4 does, so what I know about LVM is all ext4-based.  Definitely read the manpages to see the xfs caveats for every command.

---

### Post by michael351 on 2020-03-05
I need help on this unfortunately ....

I have a failing 1TB hard drive. What I want to do is copy the OS partition from this failing drive to a USB thumb drive. I will then remove the failing drive and put in a new 2TB hard drive I just received. I then need to boot into the thumb drive and copy the backed up OS to the new internal disk. My expectation would be I could then remove the thumb drive and boot off the new disk with my existing operating system.

What is the best way to do this? thanks

---

### Post by TheFu on 2020-03-05
1st, thanks for attempting to get code tags, but *quotes* are not *code* tags and do not help readability.  Please edit the post, chance all the "QUOTE" stuff so it says "CODE" and save.  I probably missed some critical data due to the bad format.

The best way to migrate has lots of detailed steps that very few volunteers here can post exactly for you to copy paste.  I know that I cannot. I can try to get all the overview steps, but things will almost certainly be missed, command options may be a little off.

You have about 2 TB of stuff.  No way to move that without a 2TB HDD.

Step 1, create a backup of everything.  Whenever doing stuff like this, a tiny error can wipe data. 

If it was me doing this, I'd 
[LIST=1]
[*]connect the new 2TB disk to an external USB3 port, 
[*]boot up using a "Try Ubuntu" desktop flash drive and 
[*]migrate /boot first, 
[*]then the LVM volumes
[*] fix the /etc/fstab to use the new LVs on the new storage only.
[*] shutdown, remove the  old disks
[*]boot using "Try UBuntu" again, setup a chroot to install, update grub - do that
[*]reboot without the flash drive and see the OS come up on 1 disk, mounting all the LVs correctly.
[/LIST]

/boot is just normal BIOS boot - a **tar cvf -  /boot ... | tar xvf /mnt/new-storage/boot** to copy everything over while keeping symlinks would be my method. Suppose rsync could work just as well.

Then I'd make the rest an LVM PV on the new disk and use **pvmove** to get all the LVs from both disks into the new disk. One LV at a time.  That's for the data.  Perhaps resize the /home/ LV to be much smaller first.  Really, LVM should be sized up as needed with as much unallocated inside the VG as possible.  Resizing up with ext4 is 5 seconds on a running system, mostly typing and looking up the exact lvextend options.  Resizing down takes longer and the LV can't be in-use.  But with XFS, there is no way to resize down.  Having room left over for snapshots in the VG is helpful for all sorts of reasons.  With SSDs, it can extend the life drastically if 20% isn't used.

Anyway ... 

Then, I'd remove old disks logically from the new disk OS - ensure /etc/lvm/ and /etc/fstab only point to the new disk.  I always mount LVs using the mapper-paths to the storage, not UUIDs.  Only the /boot/ partition would use a UUID to mount.  **vgchange -ay** to get the LVM objects found by any new OS. That applies to the "Try Ubuntu" boots as well.  -ay not -ya. Order matters with those options.

Then,  I'd shut down the system, pull the old HDDs out, put the new 2TB disk(s) internal.

Then, I'd boot the "try ubuntu" flash disk, setup a chroot for the new disk OS stuff, so we can run a **grub-install**, **update-grub** within the new storage environment. Might need a **mkinitramfs** in there too so the LVM partitions can be mounted in phase 3 of the boot processing.

All the LVs must "appear" to be mounted in same directory locations as the old disks did in the new fstab on the new storage.

After that, Bob's your uncle.  All done. reboot **without** the flash drive connected. See that it comes up.

Anyone see any issues?  Better steps?

For example, should the switch from MBR to GPT partitioning happen?  I would, but that would depend on the BIOS.  Having a few BIOS boot systems that use GPT boot disks has always worked for me, but I hear some BIOSes don't allow it.

I would change from XFS to EXT4. But doing that would mean the pvmove can't be used and the LVM objects would need to be manually created, file systems created manually then the data manually moved over retaining owner, group, permissions, ACLs and if there are any sparse files, then ether tar or rsync would have to be used *with the specific sparse option* enabled.  I'd strongly consider making different, smaller LVs for /home/.  I would NEVER merge storage on different physical disks into a single LV, unless my backups can handle that size of storage onto single media chunks.  My backup storage aligns to LVs, so for the OS and /home stuff, I try to keep that well under 50G total (25G each). Usually, the other files are media stuff, which goes somewhere else completely and gets backed up different than the OS/HOME stuff.

Issues?  I need to sleep on this. Perhaps something important will come to light overnight.

---

### Post by michael351 on 2020-03-05
O.k. - here goes .... !

---

