---
title: "Can't update, no space on /boot"
date: 2021-08-08
forum: General Help
---

### Post by laserburn2 on 2021-08-08
Running Ubuntu 20.04 on zfs file system. Disk partitioning was done by the OS installer, it left quite an ample space for everything on my 1TB drive. 

Trying to install new updates, I see quite a number of them are zfs related. I get this error message from the screenshot. There is a lot of space, there are no old kernel clogging /boot, this must be something related to zfs. Can you help me?

---

### Post by laserburn2 on 2021-08-08
Hmmm, trying to update only Chrome, I get the same error. This might be a problem with the Update installer. Let me try the command line update.

---

### Post by laserburn2 on 2021-08-08
Apt did the job, but it is reporting that there was no space for a snapshot and there is a misconfigured package. ZFS worked very well so far, but I'm starting to think it was a mistake to trust it so soon.

ERROR couldn't save system state: Minimum free space to take a snapshot and preserve ZFS performance is 20%.
Free space on pool "bpool" is 13%.
Please remove some states manually to free up space. 


update-initramfs: Generating /boot/initrd.img-5.11.0-25-generic
I: The initramfs will attempt to resume from /dev/nvme0n1p2
I: (UUID=4c4f473a-82f7-443a-9d12-bef62e6cc8cd)
I: Set the RESUME variable to override this.
Error 24 : Write error : cannot write compressed block 
E: mkinitramfs failure lz4 -9 -l 24
update-initramfs: failed for /boot/initrd.img-5.11.0-25-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 installed initramfs-tools package post-installation script subprocess returned error exit status 1
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Setting up gnome-settings-daemon (3.36.1-0ubuntu1.1) ...
Errors were encountered while processing:
 initramfs-tools
ZSys is adding automatic system snapshot to GRUB menu
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by laserburn2 on 2021-08-08
Trying to reconfigure initramfs-tools package yielded no result, so I  tried to uninstall, then install it again, which I found as an advice  somewhere. This worked, also reducing the storage space usage on boot  from the original 239 MB to 181.

df -h /boot
Filesystem                Size  Used Avail Use% Mounted on
bpool/BOOT/ubuntu_yipvqa  345M  181M  164M  53% /boot

Not sure why installer would allocate so little space to /boot.

---

### Post by ActionParsnip on 2021-08-08
Uninstall old unused kernels

---

### Post by laserburn2 on 2021-08-08
Once again, only two kernels installed.

---

### Post by Impavidus on 2021-08-08
The space needed for /boot slowly increases over time. The installer lags a bit behind and systems get used for years without repartitioning. So in year 1 you need X MB, the installer will create a partition of X MB in year 2, you install the system in year 3 and use it until year 8 without repartitioning. By then, that X MB /boot partition is too small. It used to be more of a problem a until few years back, but they increased the size of the automatically generated /boot partition then.

Best make it about 500 MB. Or even 1 GB, if you don't really need the disk space, to be future-proof.

---

### Post by grahammechanical on 2021-08-08
I am not familiar with ZFS file system.

Where does ZFS keep the snapshots? If a snapshot is created every time there is an update and the snapshots are stored in /boot and are not destroyed, then I can see that /boot would run out of space. Are you destroying old snapshots?

Regards

---

### Post by laserburn2 on 2021-08-08
Unfortunately, I don't know that much about ZFS and its implementation on Ubuntu either. I know, kind of stupid to install experimental FS on your home system if you're not prepared to dive deep into its technical guts. But there is one thing about ZFS that I wanted and it came in handy just now.

For you see, I rebooted the system and it wouldn't start properly any more after all the messing I did today. I was greeted with some initramfs prompt where I didn't know what to do. So I restarted it again and from GRUB menu chose restore point from mid-July and it booted like a charm with my current /home! ZFS makes these restore points every time something is installed or uninstalled. There were restore points in the list from end of June till end of July, I guess end of July something went wrong with ZFS and it could no longer manage and create restore points. 

And look at this:
df -h /boot
Filesystem                Size  Used Avail Use% Mounted on
bpool/BOOT/ubuntu_bd76ll  512M  240M  272M  47% /boot

My /boot is now half a gig. I have no idea what's going on here. 

At least I'm glad that my system is bootable again and I even got rid of the stuttering problems that wouldn't go away ever since updating Nvidia driver to 470 branch back in July. I will test if system updates again mess up ZFS. If they do, I'm ok living without updates until Ubuntu 22.04 LTS comes in the spring.

---

### Post by TheFu on 2021-08-08
> **grahammechanical said:**
> I am not familiar with ZFS file system.

Where does ZFS keep the snapshots? If a snapshot is created every time there is an update and the snapshots are stored in /boot and are not destroyed, then I can see that /boot would run out of space. Are you destroying old snapshots?

Regards

Snapshots freeze blocks so they can't be used as needed later.  They are kept where they were originally written, just cataloged under the snapshot name.  There are specific ZFS commands to list the snapshots and to delete old snapshots.

ZFS is marked as EXPERIMENTAL for a reason.  Because it is.
Use ZFS for data storage, not for the OS and anything related to booting.  Especially if you don't understand how to manage ZFS storage.

Please.

---

### Post by grahammechanical on 2021-08-08
I am curious. Some time ago I experimented with the Btrfs file system. With that file system when we load the recovery menu under Advanced options for Ubuntu we get an option to manage Btrfs snapshots. Do we get a similar option when running Ubuntu on the ZFS file system?

Regards

---

### Post by laserburn2 on 2021-08-09
> **grahammechanical said:**
> I am curious. Some time ago I experimented with the Btrfs file system. With that file system when we load the recovery menu under Advanced options for Ubuntu we get an option to manage Btrfs snapshots. Do we get a similar option when running Ubuntu on the ZFS file system?

Yes. The difference is that btrfs makes a snapshop when you ask it to. Zfs makes a snapshot whenever package manager makes a change on the system. This is incredibly useful, because so for I never had a catastrofic system failure when I was expecting it, it's always happening when I don't suspect a thing and didn't prepare.

---

### Post by TheFu on 2021-08-09
With ZFS, be certain you have been removing all snapshots. Ubuntu decided to autocreate snapshots before every apt command.  Get a list of the snapshots and you probably want to delete any that are over 1 month old.

Next, I would gather used storage information for each partition.
The forum software has been blocking attempts to show those commands.
```
df -hT -x squashfs -x tmpfs -x devtmpfs
lsblk -e 7 -o name,size,type,fstype,mountpoint
```

---

### Post by laserburn2 on 2021-08-15
The problem was indeed caused by snapshots. Ubuntu's zsysctl is not good at cleaning up its mess, so snapshots can quickly fill up the tiny bpool that installer creates and there is no good way to detect what's going on until you notice error like this when running apt:
ERROR couldn't save system state: Minimum free space to take a snapshot and preserve ZFS performance is 20%.

To resolve this, you list snapshots on bpool using this command:
zfs list -r -t snapshot -o name,used,referenced,creation bpool/BOOT

Then you need to manually get rid of the old snapshots one by one to reclaim space, example command:
sudo zsysctl state remove kubr2c --system

---

### Post by TheFu on 2021-08-15
> **laserburn2 said:**
> Yes. The difference is that btrfs makes a snapshop when you ask it to. Zfs makes a snapshot whenever package manager makes a change on the system. This is incredibly useful, because so for I never had a catastrofic system failure when I was expecting it, it's always happening when I don't suspect a thing and didn't prepare.

It isn't ZFS that does this. It is Canonical's package management wrapper that does it.  Having a script that automatically removes a snapshot over 30 days old would be smart. Run that daily.  
If that doesn't free enough storage, remove snapshots over 14 days old via a script, run it daily.

---

### Post by laserburn2 on 2021-08-15
> **TheFu said:**
> It isn't ZFS that does this. It is Canonical's package management wrapper that does it.  Having a script that automatically removes a snapshot over 30 days old would be smart. Run that daily.  
If that doesn't free enough storage, remove snapshots over 14 days old via a script, run it daily.


  Ubuntu's zsysctl  does have a garbage collector that is supposed to do this, but for some reason it stopped working on bpool at the end of June, causing it to fill with snapshots. There have been some zfs updates among those I installed today, let's hope they might address this.

---

