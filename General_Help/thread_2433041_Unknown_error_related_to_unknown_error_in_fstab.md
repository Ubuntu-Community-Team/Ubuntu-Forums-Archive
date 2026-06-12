---
title: "Unknown error related to unknown error in fstab"
date: 2019-12-12
forum: General Help
---

### Post by makem2 on 2019-12-12
I performed a couple of package removals followed by an 'autoremove' I noticed the following:

```

makem@ssdTOSH:~$
update-initramfs: deferring update (trigger activated)
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for initramfs-tools (0.130ubuntu3.9) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-72-generic
W: initramfs-tools configuration sets RESUME=UUID=68342eb5-6386-48f4-a2ef-e1683ff58be5
W: but no matching swap device is available.
I: The initramfs will attempt to resume from /dev/sda4
I: (UUID=0178c9df-c13e-434d-bb57-b6c19095f4aa)
I: Set the RESUME variable to override this.
makem@ssdTOSH:~$ 

```

The fstab contains the following:

```

# / was on /dev/sda2 during installation
UUID=7f90b906-206f-4806-b66d-a83db8f7f3d0 /               ext4    errors=remount-ro 0    $
# /boot/efi was on /dev/sda1 during installation
UUID=CCBC-12A0  /boot/efi       vfat    umask=0077      0       0
# /home was on /dev/sda3 during installation
UUID=d78428d2-66ad-474b-a7bc-8144945dd6a1 /home           ext4    defaults        0      $
# swap was on /dev/sda4 during installation
#UUID=68342eb5-6386-48f4-a2ef-e1683ff58be5 none            swap    sw              0     $
UUID=0178c9df-c13e-434d-bb57-b6c19095f4aa none  swap    0       0
none /media/ramdisk tmpfs nodev,nosuid,noexec,nodiratime,size=1024M 0 0
#WinData
UUID=D232DC8B32DC75C7   /media/WinData  ntfs defaults   0       0

```

The entry: none /media/ramdisk tmpfs nodev,nosuid,noexec,nodiratime,size=1024M 0 0

Relates to a ram disk which I use.

I am not sure if I just replace the 'none' with the correct 'tmpfs       /media/ramdisk etc' whether it will mess the fstab and lock me out.

---

### Post by Yellow Pasque on 2019-12-14
The warning is telling you that your swap's UUID changed, but initramfs-tools wasn't notified. The good news is that it automatically finds the new swap's UUID. You really don't need to do anything if the Warning doesn't bother you.
If it does, check your /etc/initramfs-tools/conf.d/resume file. If you see:

```
RESUME=UUID=68342eb5-6386-48f4-a2ef-e1683ff58be5
```
change it to:
```
RESUME=UUID=0178c9df-c13e-434d-bb57-b6c19095f4aa
```

> The entry: none /media/ramdisk tmpfs nodev,nosuid,noexec,nodiratime,size=1024M 0 0
Relates to a ram disk which I use.
I am not sure if I just replace the 'none' with the correct 'tmpfs /media/ramdisk etc' whether it will mess the fstab and lock me out. 

Don't touch that. It's unrelated to the Warning.

---

