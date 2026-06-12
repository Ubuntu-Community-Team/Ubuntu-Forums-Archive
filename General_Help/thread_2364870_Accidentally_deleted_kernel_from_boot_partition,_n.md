---
title: "Accidentally deleted kernel from /boot partition, now ubuntu won't boot"
date: 2017-06-29
forum: General Help
---

### Post by bei2 on 2017-06-29
Running 16.04, was getting notifications that /boot partition was getting full so I deleted a bunch of old kernel files fromt the boot partition. I accidentally deleted one of the current kernel files, and now I get a blank screen when I try to boot. It's the vmlinuz file. I tried downloading the deleted file and copying to boot parition, but this has not worked. I have an important file on that laptop. The /home folder is encrypted and unfortunately I did not create a separate /home partition, so I think there's no way I can recover that file unless I can get the thing to boot. Or is there any other way to get this file? I don't mind re-installing as long as I can recover it.Created this account to ask about this, any help would be much appreciated. 

Thanks,
bei2

---

### Post by deadflowr on 2017-06-29
You can try a chroot to recover
Do you have an Ubuntu installation media (dvd,usb)?

---

### Post by bei2 on 2017-06-29
Thanks for quick reply, yes I do have a live USB of 16.04

---

### Post by bei2 on 2017-06-29
I may have already attempted a chroot. I followed the guide at this link:

[https://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels#28100](https://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels#28100) 

It didn't work, I still just get a blank screen and noo boot

---

### Post by deadflowr on 2017-06-29
Boot back into the chroot
look in  the boot folder.
If you still have any initrd.img files, look at the version at the end (the -4.4.0-77-generic part)
(best the look for the newest one, ala 4.4.0-77 would be older than 4.4.0-88)
then try running the reinstall command for which ever you version you found
like,
```
sudo apt-get install --reinstall linux-image-4.4.0-77-generic
```
change the version string name to whatever the one you found was.

Hope that makes sense

---

### Post by bei2 on 2017-06-29
Thanks, I will try that. I'm actually able to look in the /boot partition now, because I'm running a live OS on the lopatop that won't boot. I see initrd.img-4.8.0.56-generic. There's one other older one on there too. I guess I will try that again, but I think I tried it before without fixing the problem. I chrooted and ran a command to re-install kernel, but it may have been a different command. I will try again. I'll login to this account from another computer so I can keep checking this thread.

---

### Post by bei2 on 2017-06-29
> **deadflowr said:**
> Boot back into the chroot
look in  the boot folder.
If you still have any initrd.img files, look at the version at the end (the -4.4.0-77-generic part)
(best the look for the newest one, ala 4.4.0-77 would be older than 4.4.0-88)
then try running the reinstall command for which ever you version you found
like,
```
sudo apt-get install --reinstall linux-image-4.4.0-77-generic
```
change the version string name to whatever the one you found was.

Hope that makes sense

One more question before I attempt this: Does the version # have to  match whatever kernel was running before I deleted the file, or is it OK  if I go with a different version #? I tried just copy/pasting a few  different files and don't remember which kernel I was on before it  stopped booting. I guess I can just try a few different versions and see  if 1 works.

---

### Post by CatKiller on 2017-06-29
I think ```
sudo apt-get install --reinstall linux-image-generic
``` will pull the latest available. If it doesn't, then you might need to specify the version.

EDIT: Actually, I just noticed you were on the 4.8 branch previously. It would be linux-image-generic-hwe-16.04 if you want to stick with that, although you can fiddle with which kernel you're using after you can get it to boot again.

EDIT 2: In case you have a full /boot again in the future, removing the old kernels through the package manager is much safer than deleting random files.

---

### Post by bei2 on 2017-06-29
So I have been trying to do the chroot thing but I am having trouble getting the encrypted sytem partition mounted from live USB. I am able to unlock the partition with the cryptsetup command, but when I try to mount I get an error message.


```
sudo mount /dev/mapper/sda3_crypt /mnt

mount: wrong fs type, bad option, bad superblock, or other error
```

I am able to mount the /boot partition, which is not encrypted, but I can't figure out how to mount root system, even though I was able to unlock with decryption password.

I'm close to 100% certain that the partition is not corrupted, as everything was working fine until the kernel got deleted.

---

### Post by deadflowr on 2017-06-29
Sorry,
I thought you just had an encrypted home.
Perhaps look over this
[http://www.jmdeldin.com/posts/2016/mounting-an-encrypted-drive-in-ubuntu.html]("http://www.jmdeldin.com/posts/2016/mounting-an-encrypted-drive-in-ubuntu.html")
or that:
[https://ubuntuforums.org/showthread.php?t=2216572&page=2&p=12986821#post12986821]("https://ubuntuforums.org/showthread.php?t=2216572&page=2&p=12986821#post12986821")

Unfortunately, I'm out of my element in terms of FDE (full disk encryption) recovery. (I do backups which negates any need to.)

---

### Post by bei2 on 2017-06-29
> **deadflowr said:**
> Sorry,
I thought you just had an encrypted home.
Perhaps look over this
[http://www.jmdeldin.com/posts/2016/mounting-an-encrypted-drive-in-ubuntu.html](http://www.jmdeldin.com/posts/2016/mounting-an-encrypted-drive-in-ubuntu.html)
or that:
[https://ubuntuforums.org/showthread.php?t=2216572&page=2&p=12986821#post12986821](https://ubuntuforums.org/showthread.php?t=2216572&page=2&p=12986821#post12986821)

Unfortunately, I'm out of my element in terms of FDE (full disk encryption) recovery. (I do backups which negates any need to.)

Thanks I'll look at those guides and see if I have any luck. In future I will defintely backup, or maybe switch to VMs with snapshots. I gotta get out of the stone age lol :D

---

### Post by bei2 on 2017-06-29
I came across this in another guide:

> When running cryptsetup luksOpen, you must use the same name as the one that is in /etc/crypttab on the root parition (sda3_crypt in this example).

Is there any way to find out the name in /etc/crypttab without being able to access the partition? like is it a standard name on all installations? I'm having trouble unlocking the lvm, so maybe this is the issue


Also: I'm trying to use the first of the 2 guides posted above. I'm stuck at this part:


> Check vgdisplay again:

 # vgdisplay
--- Volume group ---
VG Name               ubuntu-vg
System ID
Format                lvm2
Metadata Areas        1
Metadata Sequence No  4
VG Access             read/write
VG Status             resizable
MAX LV                0
Cur LV                1
Open LV               0
Max PV                0
Cur PV                1
Act PV                1
VG Size               238.23 GiB
PE Size               4.00 MiB
Total PE              60987
Alloc PE / Size       56910 / 222.30 GiB
Free  PE / Size       4077 / 15.93 GiB
VG UUID               lIcU2S-NJ3d-gAPj-wIwP-3pJ9-F9LC-2X4akS


When I enter that command I get no output at all, just a fresh command line. I ran vgscan and that found no logical volumes. Shouldn't something called ubuntu-vg be showing up? That's how it works in all the guides I've read, and I'm not seeing any ubuntu-vg.

---

### Post by TheFu on 2017-06-29
You can definitely mount the encrypted LVM LVs. I've had to do it myself before ... about 8 wks ago for a few days when I was resizing the encrypted partition. I didn't want the entire drive encrypted - too much hassle to show a working OS in an airport and I'd rather not decrypt it for someone else's use.  It isn't hard, just need to get the LVs known, so you can mount them.  **sudo vgscan** should do that on a liveCD/Flash boot.  May need to install LVM into the environment, I don't recall.

All the vgdisplay does it convince the flash-boot that you have LVM with VGs and LVs. Next you have to mount the correct LV to the correct location - / or swap usually.  You can forget about the cryptab stuff. Shouldn't matter.  As part of the new kernel being installed, the crypt stuff should be added to the initrd boot and grub to prompt for the unlock code.

I like the format of the **sudo lsblk** best. It shows the relationship of partitions, encryption, PVs, VGs, and LVs in a nice way.

Hope that's clear enough?  I'll look for my notes, but don't remember it being anything unexpected. All normal cryptsetup and lvm stuff.

Ok ... my notes - you'll need to modify them for your situation.
```
DEV=/dev/sdbX
PV=whatever-the-PV-is

sudo cryptsetup luksOpen $DEV $PV
sudo vgscan 
sudo mkdir /mnt/root /mnt/Stuff

sudo mount /dev/mapper/$PV*root /mnt/root
sudo mount /dev/mapper/$PV*Stuff /mnt/Stuff   # this is just for some extra files, Stuff.

```
I didn't enable the swap, as you can see.  These notes were for an external disk, not my internal boot, but should get you started.

BTW, in the future, **NEVER** delete files that were installed by the package manager directly. Always remove them through the package manager.  I suspect you've already toasted that.  That goes for settings, programs, libraries and automatically generated files by the installation process.  Data files create/used by the program POST install don't count.

---

