---
title: "Internal HDD read only"
date: 2015-04-05
forum: General Help
---

### Post by clericbob on 2015-04-05
Hello, thank you for your time in reading this.
I'm having some trouble with my install of Ubuntu 14.04.  The specific machine it has been installed on has worked almost nonstop for several months before now.  The issue is that it sees the internal HDD as read-only, and thus cannot do darn near anything.  It cannot access or modify the temp-files, making usage impossible.  And due to Ubuntu's handling of external drives, it does not recognise or allow external drives at all, making backup/recovery impossible from within Ubuntu.
On reboot, it goes into some sort of diagnostic mode, giving an error that "errors were found when checking the disk for /"
It is possible to ignore these errors, allowing you to boot up properly.  However, it only works for roughly a half-hour, before becoming unusable.  This is likely due to RAM limitations, as it is incapible of writing to disk for tempfiles.
**Previous threads with this issue were either unhelpful or had a solution that was not applicable. ** The computer in question is a Toshiba Satellite laptop, any attempts to find hard drive model from within the system have failed.
Unless I recieve assistence, my course of action will be to wipe the drive and hope it isn't broken.
Any assistance would be appreciated, thank you for your time.

---

### Post by Impavidus on 2015-04-06
The file system is remounted read only when there is an input/output error. In my experience, this means a hardware error. The system does a lot of things in the background, some of them involving disk writes. This may trigger the I/O error and ro remounting of the file system. This has nothing to do with RAM limitations.

When you plug in a usb drive, it should be recognised and mounted automatically. If not, you can mount one manually using```
sudo mount /dev/partition-on-your-usb-drive /wherever/you/want/it/mounted
```

---

### Post by Mark Phelps on 2015-04-06
> It is possible to ignore these errors, allowing you to boot up properly. BAD idea... You appear to have a corrupted filesystem and allowing the fsck to run will attempt to repair it.  If you keep getting those errors on boot up, that means your drive is failing and you need to replace it before it goes out completely.

---

### Post by clericbob on 2015-04-06
> When you plug in a usb drive, it should be recognised and mounted automatically. If not, you can mount one manually using:

The stated reason the disk would not mount is not that it didn't see or recognise the disk, rather that it couldn't create the necessary links in /media/[my name] in order to mount.  I am unsure whether this is the actual reason, it is just the one that was told to me by the system.  It attempted to mount the drive immediately, before throwing up an error.  And I believe you misconstrued my comment on RAM limitations as being the cause of the error; what I meant was that it was a possible cause of things not locking up until a certain point, as the computer could, theoretically, store changes to the HDD in RAM until they were able to enact.  Too many stored changes, due to being unable to enact them, and it becomes unusable.  I'm not an expert, however, and this is just conjecture, so feel free to correct me if I'm completely out of my mind.

I have managed to use an external boot disk to chmod the entire contents of the disk to a usable state, however I do not think it will last forever.  I'm in the process of backing up my important files, but several things are reporting back with an input/output error.  I just got this computer last October, and having hard-drive failiure already is most vexing.  Before I try to trash the HDD, should I attempt a clean Ubuntu install to see if it fixes things?  Perhaps format the drive to a clean slate?  If there's any way to potentially save the drive, I need to try it; I haven't the money currently to replace it with one of a similar size.

Thank you both for your assistence and time.

---

