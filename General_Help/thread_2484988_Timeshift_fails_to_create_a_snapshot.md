---
title: "Timeshift fails to create a snapshot"
date: 2023-03-16
forum: General Help
---

### Post by mrgou on 2023-03-16
I've just set up Ubuntu on a new computer, and I can't manage to get Timeshift to work. Since the GUI doesn't list any snapshot, even after creating one manually, I ran it from the terminal. After spending several minutes creating the snapshot, it ends up with an error:

```
$ sudo timeshift --create --debug
D: Main()
D: 
D: Running Timeshift v21.09.1
D: 
D: Session log file: /var/log/timeshift/2023-03-16_18-03-42_ondemand.log
D: Distribution: Ubuntu 22.04 (jammy)
D: DIST_ID: Ubuntu
D: Main: check_dependencies()
D: Main: add_default_exclude_entries()
D: Main: add_default_exclude_entries(): exit
D: update_partitions()
D: df -T -B1
D: Device: get_disk_space_using_df(): 2
D: Device: get_mounted_filesystems_using_mtab(): 2
D: Device: get_filesystems(): 20
D: partition list updated
D: detect_system_devices()
D: /boot/efi is mapped to device: /dev/nvme0n1p1, UUID=318C-4088
D: / is mapped to device: /dev/nvme0n1p2, UUID=3d22a390-73f9-4b70-be4e-6ec2dfe3ebdb
D: Searching subvolume for system at path: /
D: Users: user_name root
D: Encrypted home users: 
D: Encrypted home dirs:

D: Encrypted private dirs:

D: Main: load_app_config()
App config loaded: /etc/timeshift/timeshift.json
D: IconManager: init()
D: bin_path: /usr/bin/timeshift
D: found images directory: /usr/share/timeshift/images
D: Main(): ok
D: AppConsole: parse_arguments()
D: Main: initialize_repo()
D: backup_uuid=3d22a390-73f9-4b70-be4e-6ec2dfe3ebdb
D: backup_parent_uuid=
D: Setting snapshot device from config file
D: repo: creating from uuid
D: SnapshotRepo: from_uuid(): RSYNC
D: uuid=3d22a390-73f9-4b70-be4e-6ec2dfe3ebdb
D: SnapshotRepo: init_from_device()
D: 
D: SnapshotRepo: unlock_and_mount_devices()
D: device=/dev/nvme0n1p2
D: SnapshotRepo: unlock_and_mount_device()
D: device=/dev/nvme0n1p2
D: Device: get_mounted_filesystems_using_mtab(): 2
D: ------------------
D: arg=3d22a390-73f9-4b70-be4e-6ec2dfe3ebdb, device=/dev/nvme0n1p2
D: /run/timeshift/backup
D: /var/snap/firefox/common/host-hunspell
D: /
D: ------------------

/dev/nvme0n1p2 is mounted at: /run/timeshift/backup, options: rw,relatime,errors=remount-ro

D: SnapshotRepo: load_snapshots()
D: loading snapshots from '/run/timeshift/backup/timeshift/snapshots': 0 found
D: SnapshotRepo: unlock_and_mount_device(): exit
D: Selected snapshot device: /dev/nvme0n1p2
D: Free space: 382.2 GB
D: SnapshotRepo: check_status()
D: SnapshotRepo: available()
D: is_available: ok
D: SnapshotRepo: has_snapshots()
D: SnapshotRepo: has_space()
D: df -T -B1 '/dev/nvme0n1p2'
D: Device: get_disk_space_using_df(): 1
D: no snapshots
D: SnapshotRepo: check_status(): exit
D: SnapshotRepo: init_from_device(): exit
D: SnapshotRepo: from_uuid(): exit
D: Main: initialize_repo(): exit
D: AppConsole: start_application()
D: Main: create_snapshot()
D: SnapshotRepo: has_space()
D: df -T -B1 '/dev/nvme0n1p2'
D: Device: get_disk_space_using_df(): 1
D: no snapshots
D: Main: backup_and_rotate()
D: SnapshotRepo: available()
D: is_available: ok
D: SnapshotRepo: has_space()
D: df -T -B1 '/dev/nvme0n1p2'
D: Device: get_disk_space_using_df(): 1
D: no snapshots
------------------------------------------------------------------------------
Creating new snapshot...(RSYNC)
Saving to device: /dev/nvme0n1p2, mounted at path: /run/timeshift/backup
D: Main: save_exclude_list_for_backup()
D: Main: create_exclude_list_for_backup()
D: Main: create_exclude_list_for_backup(): exit
Synching files with rsync...
D: RsyncTask:execute()
D: rsync -aii --recursive --verbose --delete --force --stats --sparse --delete-excluded --log-file='/run/timeshift/backup/timeshift/snapshots/2023-03-16_18-03-42/rsync-log' --exclude-from='/run/timeshift/backup/timeshift/snapshots/2023-03-16_18-03-42/exclude.list' --delete-excluded '/' '/run/timeshift/backup/timeshift/snapshots/2023-03-16_18-03-42/localhost/'
D: RsyncTask:prepare(): saved: /tmp/G4fVRUBw/2023-03-16_18-03-42/script.sh
D: AsyncTask: child_pid: 60870
D: AsyncTask: finish(): entermaining)
D: exit_code: 0
E: rsync returned an error                                                      
E: Failed to create new snapshot
Failed to create snapshot
------------------------------------------------------------------------------
D: SnapshotRepo: load_snapshots()
D: loading snapshots from '/run/timeshift/backup/timeshift/snapshots': 0 found
D: SnapshotRepo: auto_remove()
D: SnapshotRepo: remove_untagged()
D: SnapshotRepo: load_snapshots()
D: loading snapshots from '/run/timeshift/backup/timeshift/snapshots': 0 found
D: SnapshotRepo: load_snapshots()
D: loading snapshots from '/run/timeshift/backup/timeshift/snapshots': 0 found
Removing snapshots (incomplete):
------------------------------------------------------------------------------
Removing '2023-03-16_18-03-42'...
D: RsyncTask:execute()
D: rm -rfv '/run/timeshift/backup/timeshift/snapshots/2023-03-16_18-03-42/'
D: RsyncTask:prepare(): saved: /tmp/G4fVRUBw/2023-03-16_18-06-54/script.sh
D: AsyncTask: child_pid: 62277
D: AsyncTask: finish(): entermaining)
D: exit_code: 0
Removed '2023-03-16_18-03-42'                                                   
------------------------------------------------------------------------------
D: SnapshotRepo: load_snapshots()
D: loading snapshots from '/run/timeshift/backup/timeshift/snapshots': 0 found
D: SnapshotRepo: load_snapshots()
D: loading snapshots from '/run/timeshift/backup/timeshift/snapshots': 0 found
D: rm -rf "/run/timeshift/backup/timeshift/snapshots-boot/"
D: rm -rf "/run/timeshift/backup/timeshift/snapshots-hourly/"
D: rm -rf "/run/timeshift/backup/timeshift/snapshots-daily/"
D: rm -rf "/run/timeshift/backup/timeshift/snapshots-weekly/"
D: rm -rf "/run/timeshift/backup/timeshift/snapshots-monthly/"
D: rm -rf "/run/timeshift/backup/timeshift/snapshots-ondemand/"
D: Symlinks updated
D: exit_app()
D: crontab -l
D: Failed to read cron tab
D: crontab -l
D: Failed to read cron tab
D: Cron task exists: /etc/cron.d/timeshift-hourly
D: unmount_target_device()
D: clean_logs()
D: rm -rf '/tmp/G4fVRUBw'
```

I'm not sure what I'm looking for, so hoping someone can help!

---

### Post by mrgou on 2023-03-16
Here's also the full log: [https://pastebin.com/a1tW3ZUJ](https://pastebin.com/a1tW3ZUJ)

---

### Post by TheFu on 2023-03-16
3 things come to mind.
a) Do you have a 2nd drive connected that has a native Linux file system on it?
b) Which file system is being used on the source storage?
c) If you are using any encryption that isn't already unlocked, backups tend not to work.  This is 1 of the many reasons why using LUKS encryption is best and trying to encrypt just a home directory doesn't really work.

If you run, 
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```
when all the storage is mounted, source and target, then someone might be able to help.

---

### Post by mrgou on 2023-03-16
a) No
b) & c) Sorry, I don't know. Maybe this gives you the required info:

```
$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/nvme0n1p2 ext4  468G  112G  333G  26% /
/dev/nvme0n1p1 vfat  511M  9.5M  502M   2% /boot/efi
```

---

### Post by TheFu on 2023-03-16
If you don't have a 2nd storage device, then any backup tool being used is fairly useless.  Backups have to go to a different storage device.  

Most people would get a $40 2TB external USB3 HDD and write backups there.  If you want a DR, disaster recovery, plan too, then get 2 USB3 external HDDs and every Friday, swap one of them at your workplace in a locked drawer.

Looks like you are using ext4 for the OS and booting with UEFI.  That means the system can't use more advanced snapshot capabilities that LVM2 or BTRFS would allow.  Neither of those are "backups", but they go make it possible to take backups of 100% quiesced areas so no file corruption due to the file changing while a backup is happening is even possible.  On a single-user desktop, this isn't normally a big deal.  Even I don't bother.

So the only question really remaining is "c" - encryption.  I see that LUKS isn't be used, but I also see method of an encrypted HOME directory in the first logs. Those could just be very detailed logs showing that they were checking for encryption. There's nothing listed, so that could easily mean nothing was found.

You do know that all backup tools have to be configured before they can be run.  Typically, at a minimum, the target directory that's mounted on a different storage device is the least requirement.  Run the GUI, set that, after you connect a USB drive that has a native Linux file system (not NTFS, not exFAT, not FAT32) and try again.

---

### Post by mrgou on 2023-03-17
I did run the configuration in the Timeshift GUI. I don't mind if snapshots are on the same drive as the system, so I don't also have to bother about the external drive being plugged in during when scheduled snapshots are being created. On my previous laptop, I used it to restore it to an earlier state (e.g. after an update that didn't work as expected). When I set up the OS from the boot drive, I applied pretty much all the default settings, so I expected everything to work similarly.

---

### Post by TheFu on 2023-03-17
> **mrgou said:**
> I did run the configuration in the Timeshift GUI. I don't mind if snapshots are on the same drive as the system, so I don't also have to bother about the external drive being plugged in during when scheduled snapshots are being created. On my previous laptop, I used it to restore it to an earlier state (e.g. after an update that didn't work as expected). When I set up the OS from the boot drive, I applied pretty much all the default settings, so I expected everything to work similarly.

If that's all you want, you can skip timeshift completely and just load LVM2 or BTRFS or ZFS as part of the installation.  Then you can automate creation of rolling snapshots every hour or 4 hrs or day or week and retain them as long as you have space to hold them.  

I guess the key to using timeshift in that way would be to ensure the target storage is NOT part of the source storage.

LVM setup at install time is 1 checkbox and you get to use ext4 as the file system.  

BTRFS and ZFS include both specialized file systems AND volume management.  On a single disk system, BTRFS is fine, unless you run virtual machines, then it should probably be avoided.

I've not had happy results installing 20.04 with ZFS. The performance was bad.  However, last month I installed Linux Mint 21.1 with ZFS as the OS file system and performance has been fine.  I haven't setup rolling snapshots, but it is in my plan.  I do nightly, versioned, network backups for all my systems, so I'd probably go with 48 hours of rolling snapshots in my situation.  Wish I had more clear answers, but until I set it up, I only know that it's possible, not the details for what doing it entails.  

Creating a single snapshot is easy with all three of the volume management tools. I need to get the OS and user data areas. Since those are separate on my systems, 2 commands are needed:
LVM: 
```

  sudo lvcreate -L1G -s -n rootsnapshot /dev/hadar-vg/root
  sudo lvcreate -L1G -s -n homesnapshot /dev/hadar-vg/home

```
ZFS: 
```
  sudo zfs snapshot rpool/ROOT@friMorning
  sudo zfs snapshot rpool/USERDATA@friMorning

```
I don't have BTRFS anywhere, so can't test commands before posting.

These snapshots have to be managed. 

With LVM, typically, I create a snapshot before doing backups, use the snapshot to get a clean backup, then remove the snapshots so the allocated storage can be used normally again.
```
sudo mount -o ro /dev/hadar-vg/rootsnapshot /mnt/backup-root
# backup the /mnt/backup-root area using any backup tool; rsync could be used, but it isn't exactly a great backup tool. There are better tools that have built-in versioning.
sudo umount /mnt/backup-root
sudo lvremove  /dev/hadar-vg/rootsnapshot

```
For LVM, [https://www.howtoforge.com/linux_lvm_snapshots](https://www.howtoforge.com/linux_lvm_snapshots) shows more clearly how to create snapshots, mount them read-only, use some backup tool to get the data to different storage, umount it, then remove the snapshot that isn't used anymore.

With ZFS there are automatic tools available like **sanoid**, which will do the rolling snapshots. These can be mounted and backed up, though ZFS has a built-in zsend command for remote backups.
```
  sudo zfs destroy rpool/ROOT@friMorning
  sudo zfs destroy rpool/USERDATA@friMorning

```
ZFS has a rollback command and will automatically remove any changes made after the specific named snapshot is rolled back. Very powerful.  Learn more here: [https://ubuntu.com/tutorials/using-zfs-snapshots-clones](https://ubuntu.com/tutorials/using-zfs-snapshots-clones)

---

### Post by mrgou on 2023-03-17
I have to confess that I have no idea what LVM is, so to make it simple to a newbie like me, I just reinstalled Ubuntu entirely, selecting LVM when presented. So far so good: Timeshift snapshots work as expected.

---

### Post by TheFu on 2023-03-17
> **mrgou said:**
> I have to confess that I have no idea what LVM is, so to make it simple to a newbie like me, I just reinstalled Ubuntu entirely, selecting LVM when presented. So far so good: Timeshift snapshots work as expected.

Well, LVM wouldn't help or harm timeshift.  

For the way you are using Timeshift (not for backups), you could use LVM and an LVM snapshot takes less than 2 seconds to finish, regardless of size.  No timeshift involved.  

If you are going to keep using timeshift and aren't too far along, and only plan to have 1 storage device used (no btrfs file systems spanning across multiple storage devices), then btrfs would integrate better.  Sorry that I didn't make it clear previously.  [https://github.com/linuxmint/timeshift](https://github.com/linuxmint/timeshift) is the timeshift project page. If you scroll down a bit, you can see how their examples use btrfs.

Timeshift is actually internally setup to work best with BTRFS, not LVM nor ZFS.
If you like, if you post the output (use forum code-tags please!) for these 4 commands, I can make suggestions around your LVM setup. Different Ubuntu versions and installers handle LVM setup differently.  Many that I've seen sized the LVs in a not-so-great manner. The sooner that is fixed, the more flexible your setup would be in the future.

```
lsblk -e 7 -o name,size,type,fstype,mountpoint
sudo pvs
sudo vgs
sudo lvs
```
Those commands will tell me much about your LVM setup.  Usually the "root" LV is much too large and they don't create a "home" or "swap" or "var" LVs.  LVM is about providing you/us with flexibility to add storage where it is needed, when it is needed.  For example, here's an LVM setup I created last fall:

```
NAME                                  SIZE TYPE FSTYPE      LABEL      MOUNTPOINT
nvme0n1                             465.8G disk                        
&#9500;&#9472;nvme0n1p1                            50M part vfat        EFI        /boot/efi
&#9500;&#9472;nvme0n1p2                           600M part ext4        boot       /boot
&#9492;&#9472;nvme0n1p3                           465G part LVM2_member            
  &#9500;&#9472;vg00-swap                         4.1G lvm  swap                   [SWAP]
  &#9500;&#9472;vg00-root--00                      35G lvm  ext4        root       /
  &#9500;&#9472;vg00-var                           55G lvm  ext4        var        /var
  &#9492;&#9472;vg00-home                          26G lvm  ext4        home       /home
```
I have 4 LVs allocated now using the same VG, vg00, with 1 PV, nvme0n1p3.  What's important is that the drive is 500G total, but I used less than 150G for the current LVs.

```
$ df -hT -x squashfs -x tmpfs -x devtmpfs |grep vg00
/dev/mapper/vg00-root--00                   ext4   35G   11G   22G  33% /
/dev/mapper/vg00-home                       ext4   26G  9.8G   15G  41% /home
/dev/mapper/vg00-var                        ext4   54G   33G   19G  64% /var

```
As you can see, I sized the LVs larger than necessary, but over time as more space is needed, eventually, I can add some of the unused storage where it is needed, when it is needed.  Those additions take 5 seconds and don't require rebooting.  Attached is an image meant to show the relationship that lsblk also shows above. 

Just know that with LVM, you have enterprise flexibility that allows all sorts of capabilities if you need them.  Most of the time, LVM LVs (Logical Volumes) can be treated like a regular partition would for file systems, labels, fsck and other stuff. The difference is that for LVM commands, 99% of the time, the file system can remain used, mounted, busy, while the changes are made.  For an enterprise, that's very important.

---

