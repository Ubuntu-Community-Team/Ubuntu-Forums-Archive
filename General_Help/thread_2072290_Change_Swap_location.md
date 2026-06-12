---
title: "Change Swap location"
date: 2012-10-17
forum: General Help
---

### Post by SuperFreak on 2012-10-17
I want to change the location of SWAP from my SSD (which I gather is a poor location) to my mechanical hard drive (Storage). I tried to unmount Storage so I could shrink the partition and create a Swap partition but I can't seem to unmount it. Below is my FSTAB :

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=fb91ba53-76d5-41af-aa6f-24035b6de7a4 /               ext4 discard,noatime,nodiratime,   errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=6EE3-8F18  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sda4 during installation
UUID=89427c18-2e81-494e-baef-933d3216d968 /home           ext4 discard,noatime,nodiratime,    defaults        0       2
# swap was on /dev/sda5 during installation
# UUID=f531caff-a236-4f4c-a401-3b7fbc067c30 none            swap    sw              0       0
# STORAGE was /dev/sdb1
UUID=b3aaffec-03c9-40dd-b836-35d9346019cb /media/STORAGE	ext4 relatime,errors=remount-ro 0 2

tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
```

---

### Post by Slim Odds on 2012-10-17
use the command "swapoff" to turn off swapping, then you can modify the fstab. Then use "swapon" 

Both require sudo

Also initialize a new swap partition with "mkswap"

---

### Post by SuperFreak on 2012-10-17
Would this be necessary as I have already deleted the Swap partition that was on my SSD, there is no Swap partition now.
I  am sorry if I don't understand. I did try to use the Swapoff command in terminal with sudo but it just brings up a list of swapoff options.
If I try to unmount my Hard Drive partition with GParted I get the following error message:
>  Could not unmount dev/sdb1/
umount: /media/STORAGE: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

Furthermore if I use nemo file manager and try to unmount storage I get:
> Storage can not be umounted
Error unmounting: umount exited with exit code 1: helper failed with:
[mntent]: line 10 in /etc/fstab is bad
[mntent]: line 14 in /etc/fstab is bad
umount: only root can unmount UUID=b3aaffec-03c9-40dd-b836-35d9346019cb from /media/STORAGE


I should add that after deleting the Swap partition I commented it out in FSTAB

---

### Post by Bashing-om on 2012-10-17
SuperFreak; Hi !

Are you trying to manipulate the partitions while they are mounted ? (no can do)
backup important data
From the live cd choose GParted, shrink your storage partition, insure swap is off,make the swap partition in the newly created free space.

UEFI: SSD -> Do your homework if you intend to reclaim the old swap space. Be sure you know how to restore the boot partition in the event something goes south (power outage can happen at any given time !)

[INDENT]just try'n to help <==BDQ

[/INDENT]

---

### Post by Slim Odds on 2012-10-17
Well... that output that you showed is complaining about your fstab file. Did you edit this yourself?

See lines in red (was 10 and 14 in your original)
```

# /etc/fstab: static file system information. 
# 
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices # that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass> proc            /proc           proc    nodev,noexec,nosuid 0       0 
# / was on /dev/sda3 during installation
[COLOR=Red]UUID=fb91ba53-76d5-41af-aa6f-24035b6de7a4 /               ext4 discard,noatime,nodiratime,   errors=remount-ro 0       1[/COLOR] 
# /boot/efi was on /dev/sda1 during installation UUID=6EE3-8F18  /boot/efi       vfat    defaults        0       1 # /home was on /dev/sda4 during installation [COLOR=Red]
UUID=89427c18-2e81-494e-baef-933d3216d968 /home           ext4 discard,noatime,nodiratime,    defaults        0       2[/COLOR] 
# swap was on /dev/sda5 during installation 
# UUID=f531caff-a236-4f4c-a401-3b7fbc067c30 none            swap    sw              0       0 
# STORAGE was /dev/sdb1 
UUID=b3aaffec-03c9-40dd-b836-35d9346019cb /media/STORAGE    ext4 relatime,errors=remount-ro 0 2  tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
```Secondly, as it says, only root can mount or unmount.

---

### Post by SuperFreak on 2012-10-17
Ok, I realize now I should have been doing this with the Live CD. Again there is no swap right now (I deleted it)so I don't see how I can swap off.
I am a little concerned that there is some problem with Fstab as Slim Odds noted but I am not sure what to do about it. I did edit it originally; I think I put the UUIDs in and added discard and noatime to optimize for the SSD. 
Any idea of whether the Fstab needs to be re-edited? I have had no problems up till now.
I do periodic back ups and I will do one shortly before I go farther in this matter. Perhaps the absence of a Swap partition is not very important as I do not hibernate the computer.

---

### Post by SuperFreak on 2012-10-17
I have attached a couple of screenshots from Gparted. I don't understand why I have to be in root to unmount Storage as it contains no system partitions or files; it is as the name decribes just data storage.

---

### Post by Slim Odds on 2012-10-18
> **SuperFreak said:**
> I have attached a couple of screenshots from Gparted. I don't understand why I have to be in root to unmount Storage as it contains no system partitions or files; it is as the name decribes just data storage.
Because "normal" users are not allowed to mount or unmount. If they could, all hell might break loose.

Note that Storage is defined in your fstab and is not auto-mounted. Therefore, it is not unmountable for a normal user.

---

### Post by SuperFreak on 2012-10-18
@Slim Odds  Thanks for clarifying this.
Do I need to fix my fstab and if so should I start a new thread (referring to lines 10 and 14 in fstab which you have highlighted in red)

---

### Post by HermanAB on 2012-10-18
Howdy,

Do yourself a favour and read the swapon man page:
$ man swapon

---

### Post by Slim Odds on 2012-10-18
> **SuperFreak said:**
> @Slim Odds  Thanks for clarifying this.
Do I need to fix my fstab and if so should I start a new thread (referring to lines 10 and 14 in fstab which you have highlighted in red)
Might not be a bad idea. I'll go ahead and comment here anyway. :KS
the UUID must actually match the drive partition that it references. You might want to lookup what UUID means (see wikipedia). It seems that this uses version 4.

Anyway, you can check the drive partition UUID using the command blkid, like this:```
sudo blkid
```
This will list the partition UUID's, which should match those in /etc/fstab. If they don't match, you should update the /etc/fstab to match.

---

### Post by SuperFreak on 2012-10-18
Everything appears to match up

I had a look at the MAN page as suggested. I am beginning to think I do not even need a SWAP partition as I never use hibernation

---

### Post by Slim Odds on 2012-10-18
> **SuperFreak said:**
> Everything appears to match up

I had a look at the MAN page as suggested. I am beginning to think I do not even need a SWAP partition as I never use hibernation
Double check lines 10 and 14 for other errors....

---

### Post by SuperFreak on 2012-10-18
I followed this example to produce my FSTAB 
[http://askubuntu.com/questions/1400/how-do-i-optimize-the-os-for-ssds]("http://askubuntu.com/questions/1400/how-do-i-optimize-the-os-for-ssds")

The only possible error I see if that link was correct is nodiratime may not be needed as that is included under noatime

---

