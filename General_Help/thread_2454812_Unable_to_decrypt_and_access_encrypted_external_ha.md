---
title: "Unable to decrypt and access encrypted external hard drive"
date: 2020-12-06
forum: General Help
---

### Post by michelle-fullwood on 2020-12-06
Hello, I am trying to access the SSD of a previous Ubuntu laptop whose motherboard stopped working. As far as I know, the hard disk was unaffected by the motherboard failure. I extracted the SSD from the old laptop, inserted it into an external enclosure, and am now trying to access it from a working computer.

**The problem:**

When I insert it, two entries appear in the Files GUI, "511 GB Encrypted" and "768 MB Volume". The latter appears to only have folders like [FONT=courier new]grub[/FONT] and [FONT=courier new]initrd[/FONT] images. When I click on the 511 GB Encrypted entry and enter the correct passphrase, it says[FONT=courier new] Error unlocking '511 GB Encrypted': Error unlocking /dev/sdb3: Failed to activate device: File exists"[/FONT].

Similarly, if I try accessing it from the command line, with

```
$ udisksctl unlock -b /dev/sdb3
```

I get the following error:

```
Error unlocking /dev/sdb3: GDBus.Error:org.freedesktop.UDisks2.Error.Failed: Error unlocking /dev/sdb3: Failed to activate device: File exists
```


Searching for solutions, I've tried:

**1) dmsetup remove**

Following [this unix.stackexchange post]("https://unix.stackexchange.com/questions/546306/error-unlocking-a-luks-partition-failed-to-activate-devicefile-exists"), I located the UUID of the device with

```
$ udisksctl info -b /dev/sdb3 | grep 'IdUUID

IdUUID:                     XXYYZZ [shortened for readability]

```

Then, I did [FONT=courier new]dmsetup remove[/FONT], but this failed.

```
$ sudo dmsetup rm luks-XXYYZZ
device-mapper: remove ioctl on luks-XXYYZZ  failed: Device or resource busy
Command failed.

```

**2) Identifying the process using the device**

Next, I tried the advice from this [AskUbuntu StackExchange thread]("https://askubuntu.com/questions/429612/device-mapper-remove-ioctl-on-luks-xxxx-failed-device-or-resource-busy"), and tried to identify the process using the device:

```

$ sudo dmsetup ls | grep XXYYZZ  # (didn't work without sudo)

luks-XXYYZZ    (253:3)

$ sudo lsof | grep 253,3

lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/110/gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/1000/gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse file system /run/user/1000/doc
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse file system /run/user/1000/keybase/kbfs
      Output information may be incomplete.

```

After the warnings, nothing was printed out, indicating that nothing matched the grep, so I couldn't proceed to the next step of killing any processes.


At this point, I'm out of ideas and would appreciate any advice!

---

### Post by TheFu on 2020-12-07
What encryption is being used?  LUKS/dm-crypt will use **cryptsetup** to unlock.  I've never used udisksctl for anything, ever, on any system, at all.

But if the sector where the crypt-key is located is corrupted, forgetaboutit.  Pull out your backups.  Whenever encryption is used, excellent backups are mandatory, not optional.

On Ubuntu, if whole drive encryption is selected during install, the organization will be

partition --> crypt-container --> LVM --> VG --> LVs for root, swap, etc.
Most disk tools only see partition level stuff.  

To access/"open" the crypt-container, cryptsetup open is used.

To access the LVM stuff, **vgchange -ay** is used, then (and only then), can the LVs be mounted just like we'd mount a file system from a partition.

---

### Post by michelle-fullwood on 2020-12-08
Thank you for replying @TheFu! I did "sudo cryptsetup luksOpen /dev/sdb3 volume01" and it went through without complaint. Then when I did "vgchange -ay", I got the following warnings:

WARNING: Device mismatch detected for ubuntu-vg/root which is accessing /dev/mapper/luks-XXYYZZ instead of /dev/mapper/volume01.
WARNING: Device mismatch detected for ubuntu-vg/swap_1 which is accessing /dev/mapper/luks-XXYYZZ instead of /dev/mapper/volume01.

The mounting does not work afterwards, I get "unknown filesystem type 'LVM2_member'".

I will try to investigate this further, but if you have any insights I would be glad to hear them. Thanks again!

---

### Post by dinkidonk on 2020-12-09
cryptsetup does not mount the device, it only maps it. Have you tried to mount it manually?

```
mkdir /media/username/volume01
mount -o defaults /dev/mapper/volume01 /media/username/volume01
```

This should give you access to the contents of the drive, sudo may be required.

What are you trying to accomplish with vgchange?

---

### Post by TheFu on 2020-12-09
> **dinkidonk said:**
>  

What are you trying to accomplish with vgchange?

The -ay tells LVM to activate all VGs. It is required after opening an encrypted container. Without it, no LVM objects will be seen.

File systems are placed onto the LVs, which are split out from the VGs.

After running **sudo vgchange -ay** (only 1 time per boot), you can see the LVs using 
```
sudo lvs
```
From there, mapper links should be created automatically and we can use that to know the path to the LV we want to mount.  Typically, I mount using the mapper created links as 
/dev/{vg-name}/{lv-name}

Here are the LVs on one of my systems, cleaned up to be just the core ones for the base OS:
```
$ ll /dev/hadar-vg/
total 0
drwxr-xr-x  2 root root  340 Dec  5 11:27 ./
drwxr-xr-x 21 root root 4680 Dec  9 01:35 ../
lrwxrwxrwx  1 root root    7 Dec  9 01:35 libvirt-lv -> ../dm-2
lrwxrwxrwx  1 root root    8 Dec  5 11:27 lv-tp-lxd -> ../dm-16
lrwxrwxrwx  1 root root    7 Dec  9 01:35 lxd-lv -> ../dm-9
[B]lrwxrwxrwx  1 root root    7 Dec  9 01:35 root -> ../dm-0
lrwxrwxrwx  1 root root    7 Dec  9 01:35 swap_1 -> ../dm-1[/B]
```

VG-name is hadar-vg.
LV names are root, swap_1, lxd-lv, libvirt-lv, and lv-tp-lxd

To mount "root" LV, the device would be /dev/hadar-vg/root
```
sudo mkdir /mnt/temp-root
sudo mount /dev/hadar-vg/root /mnt/temp-root
```
Simple.
Another useful command, after the LUKS is open and VGs have been activated:
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```

---

### Post by dinkidonk on 2020-12-09
> **TheFu said:**
> The -ay tells LVM to activate all VGs. It is required after opening an encrypted container. Without it, no LVM objects will be seen.

Odd.. Never seen that before and neither "vgchange" nor "lvs" exist on my system (kubuntu 20.04), is this related to encrypted containers with multiple partitions inside?

Whenever I open one of my encrypted drives, I only need to run cryptsetup and then mount the mapped drive. udisksctl also works fine on all my drives, but that command spins up all drives from standby for no reason.

---

### Post by TheFu on 2020-12-09
> **dinkidonk said:**
> Odd.. Never seen that before and neither "vgchange" nor "lvs" exist on my system (kubuntu 20.04), is this related to encrypted containers with multiple partitions inside?

No, it is about LVM.  LVM is normally used when the installation asked for whole-disk encryption, so if we ask for whole disk encryption on any Ubuntu, we get LVM too, usually.  I suppose someone could create a custom install that doesn't use LVM, but does have LUKS encryption.  I've never seen that with Ubuntu flavors.

If someone chooses btrfs or zfs, then LVM wouldn't be used either, I suppose.

---

