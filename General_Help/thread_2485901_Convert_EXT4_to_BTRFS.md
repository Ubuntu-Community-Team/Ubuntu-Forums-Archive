---
title: "Convert EXT4 to BTRFS"
date: 2023-04-13
forum: General Help
---

### Post by Methanoid on 2023-04-13
I have a cloud server (so headless) with Ubuntu 18.04 on it (needs to stay on 18/04 for "reasons") but EXT4.  I'd like to convert it to BTRFS with Zstd compression to save space.

Could I boot the installation ISO and then use that to do the modification to my existing install with the fstransform tool and (presumably) editing the fstab after that ?? Seems theoretically possible but I'd not be confident and dont want to trash a system I use daily! Or is there some other way that is safer?

---

### Post by ActionParsnip on 2023-04-13
You'd need to reinstall on BTRFS. Is space really a premium for you?
18.04 goes end of life at the end of the month, after which you will receive no updates and no support in the official channels. You will simply be instructed to upgrade.
You could always run a full backup, reinstall the OS to BTRFS then do a full file restore to the BTRFS. Sounds faffy

---

### Post by Methanoid on 2023-04-14
> **ActionParsnip said:**
> You'd need to reinstall on BTRFS. Is space really a premium for you?
18.04 goes end of life at the end of the month, after which you will receive no updates and no support in the official channels. You will simply be instructed to upgrade.
You could always run a full backup, reinstall the OS to BTRFS then do a full file restore to the BTRFS. Sounds faffy

Actually I didnt need to re-install and I'm well aware 18.04 is old (and not gonna explain why I can't move to 23.04 etc).

FYI and for anyone else with similar

Wasn't difficult and didnt need the backup partition AND snapshot I took just in case. In short:

_Boot Gparted Live CD_
Shrink sda2 down from 1Gb to 200MB [ was using under 100MB so reclaimed that space as can't upgrade my cloud server)
Resize/move sda3 to make space to create sda4 for backup [ wasn't needed, just resize to gain the 800MB from above]

_Boot Ubuntu 20.04 LiveCD_

At installer Ctrl-Alt-F2-F6 to drop to tty
sudo -s

-------not needed--------
mkdir /home/old
mkdir /home/new
mount /dev/sda3 /home/old
mount /dev/sda4 /home/new
rsync -avxHAX --progress /home/old/ /home/new/
-------not needed--------

apt update && install fstransform
fstransform /dev/sda3 btrfs --force-untested-file-systems
blkid /dev/sda3 [get UUID for fstab]
nano /etc/fstab
[fix root entry ] UUID=xxxxxxxxxxxxxxxxx / btrfs compress=zstd 0 0

mount /dev/sda3 /mnt
mount --bind /dev /mnt/dev
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys
chroot /mnt
mount /dev/sda2 /boot
update-initramfs -u
update-grub

reboot, done!

Finally, 

btrfs filesystem defragment -r -v -czstd / [FORCES RECOMPRESSION]

---

### Post by DuckHook on 2023-04-14
> **Methanoid said:**
> …not gonna explain why I can't move to 23.04 etc…
Um… ooh&#8209;kay…

Just be advised that, for obvious reasons, the seasoned helpers on these forums will not run zombie versions. Hence, there is no point asking for help with 18.04 starting mere days from now.

You may wish to consider signing up for Ubuntu Pro and registering this machine for ESM. That will extend support for your Bionic machine by another 5 yrs. Pro is free for personal use up to 5 machines.

If you decide on this, you should do so quickly. I'm not sure that registration can be done successfully once an OS actually falls out of support.

---

