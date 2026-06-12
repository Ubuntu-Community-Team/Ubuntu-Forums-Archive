---
title: "mnt-sdc"
date: 2018-06-11
forum: General Help
---

### Post by SciFiFan on 2018-06-11
Hello everyone,
 Yes, I made a mistake when I tried to install a 4 TB external drive. I tried posting this on Ask Ubuntu, but whoever tried to help me assumed that I had much more knowledge than I do, which is almost none. While I have been using Ubuntu solely for almost 10 years, I have not even tried to get into the programming side. Everything I have ever done with Ubuntu has been scripts written by others and copied/pasted into terminal.
 I tried to use the Disks Utility in Ubuntu 16.04 LTS which went badly for me.  My drive appeared there as a generic storage device. I clicked on the gear setting then clicked on the “edit mount options”. There I tried to do some things, but nothing appeared to work as I wanted and knew I would have to learn more. I must have clicked on OK instead of Cancel and now my system will not boot. Need some help to get my system back, please.
 I have a SSD as the main drive and a 1TB drive for secondary and wanted to add a 4 TB external drive.
 
 In the emergency mode, I looked at the journals and saw that:
 mnt-sdc.mounts: Mount process exited code=exited status=32 Failed to mount /mnt/sdc
 Dependency failed for Local File Systems 

 
 
 In the emergency mode, I used cat /etc/fstab to get this:
 # /etc/ fstab: static file system information  
 # / was on / dev/sda2 during installation UUID=3c94b6f9 -56e9-4638-a087-c89893a67aaa/ ext4 noatime,errors=remount- ro 0 1  
 # / boot /efi was on /dev/sda1 during installation UUID=4CF7-1565 /boot/efi vfat unmask=0077 0 1 
# swap was on /dev/sda3 during installation UUID=cc723f40-24ae-41c7-883c-c275b941ffcb none          swap sw 0 0 
/dev/sdc /mnt/sdc auto sw 0 0

---

### Post by TheFu on 2018-06-11
* Ensure all the disks you want to have mounted via the fstab are connected.
* Boot from a flash boot (usb is fine). Think ISO boot with the same version of Ubuntu - the exact DE doesn't matter.
* Install boot-repair (this will be a RAM-only install).
* Run the "get info" thing and post the URL back here.

With the information it provides (which is much more complete than we'd has for manually with 5+ commands), someone here can probably make an fstab that will work and have the new 4TB disk.

BTW, the 4TB drive you have ... it is probably NTFS formatted and if it will only be connected to Linux and it won't be an OS or applications disk, then I'd use a simple partition and ext4 file system.  Set that up before you put any data on it.

I wouldn't put any USB devices into an fstab.  It is too easy for them to disappear and fstab entries don't like that.  I use autofs for this myself.

FYI ... a few things.
/dev/sdc is the entire disk. The whole disk device is used by partition managers, but pretty much nothing else.
/dev/sdc1 is the first primary partition.  File systems are almost always put into a partition.

Generally, 
```
sdc = whole disk
 sdc1 = 1st partition
    mkfs -t ext4 /dev/sdc1    # will wipe anything on sdc1 and create a new file system, type ext4
    sudo mkdir /data    # make a mount point (empty directory)
    sudo mount -t ext4 /dev/sdc1 /data   # mount the new file system to the mount point.

```
It is possible to mount using the device, LABEL, UUID, PATH, and a few other tag-like methods.  Almost always, for internal disk, it is best to use the UUID since device names are dependent on the order a kernel discovers the disk.  That can change from boot to boot.  Using UUIDs, you can swap SATA connectors around to different ports on the motherboard and it won't matter.
For external USB storage, I prefer to mount using LABELs.   If you do a long-listing (ls -al) in the /dev/disk/by-* directories, the LABEL/UUID to current device will be shown.  They are automatically created at storage discovery and symbolic links created.

I'm assuming you aren't using encryption or LVM.    That makes things a little harder.  I use both, but won't help with manually doing encryption if there are issues because I've failed too many times.  LVM is usually beyond a beginner due to add complexity and flexibility.

BTW, if you had a backup, you could just put back the last version of the fstab and be done.  That would save everyone time.  It is smart to make a backup before doing things with system files. If not a system backup, then at least just copy the original file to file-orig for safety. Having a backup of everything in /etc/ is just smart and it is tiny. Even experts make mistakes.  I've locked myself out of sudo about 10 times because I was adding the same wrong config lines 10 times.  I'm stubborn and persistent.

---

### Post by SciFiFan on 2018-06-12
Ran the "boot repair" which didn't work, or it did and gave me a URL of:
[http://paste.ubuntu.com/p/GsR6mBtMwM/](http://paste.ubuntu.com/p/GsR6mBtMwM/)

---

