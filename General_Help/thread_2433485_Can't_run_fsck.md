---
title: "Can't run fsck"
date: 2019-12-19
forum: General Help
---

### Post by bews2 on 2019-12-19
Dual boot configuration, after "apk-get upgrade" ubuntu doesn't boot and says "serious hard drive problems".

When I run fsck -f / - it works, but doesn't change anything.
When I run fsck on /dev/loop0 (this is what graphical interface tries to do) it says "You must have r/w access to the filesystem or be root" - but I am root.
When I run ntfsfix it says "Refusing to operate on read-write mounted device" - but it is mounted as ro.

Win7 loads fine, chkdsk doesn't find any problems.

I have no idea what to do in this situation.

---

### Post by CatKiller on 2019-12-19
The loop devices aren't drives, they're snaps.

Don't use fsck on NTFS partitions. Windows is the tool for messing with Windows filesystems.

You can't check the filesystem of a filesystem that's mounted.

Boot into a live USB/DVD and run the fsck on your Linux partitions there.

---

### Post by bews2 on 2019-12-28
I don't have Linux partitions, it's a virtual drive from NTFS (ubuntu was installed from windows).
> [COLOR=#000000]Windows is the tool for messing with Windows filesystems.[/COLOR]
> [COLOR=#000000]Win7 loads fine, chkdsk doesn't find any problems.
[/COLOR]Looks like something wrong inside that virtual drive.

Also, the version with older kernel still loads fine and works, only updated version reports disk problems.
In there any way to fix that from older version?

---

### Post by yancek on 2019-12-28
> I don't have Linux partitions, it's a virtual drive from NTFS (ubuntu was installed from windows).

Does that mean you have some unknown version of windows installed on this computer and that you then installed some virtualization sofware (VirtualBox, VMWare, etc.) and installed Ubuntu virtually?
If it is virtual software on which you have Ubuntu, it is using a Linux filesystem (most likely ext4) inside the virtual sofware so I'm not sure why you would be trying to run ntfsfix, especially since you said you used the windows software chkdsk and it found no problems.  If you did have problems with an ntfs filesystem you would be much more likely to resolve it with chkdsk as it is written on and for windows, ntfsfix on the other hand is extremely limited on what it can do.

Your post is a little confusing as you originally say "dual boot" and later say you are using virtualization.  Dual boot generally means installation directly on the hard ware of two operating systems.  If you are using a VM and can't boot the OS installed directly on the hardware, you can't boot the virtual OS.  If both are on hardware, you should be able to do it, especially with newer UEFI so some clarification on exactly what you are doing would be useful.

---

