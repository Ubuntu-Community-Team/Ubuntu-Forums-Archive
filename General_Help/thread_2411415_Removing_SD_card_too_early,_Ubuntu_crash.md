---
title: "Removing SD card too early, Ubuntu crash"
date: 2019-01-30
forum: General Help
---

### Post by fwhisky on 2019-01-30
Hi everyone 

I've done this a few times where I have removed an SD card too early and when I push the eject button, the eject button disapears but the drive does not. And apon reseting or shutting down the laptop, Ubuntu will get to the purple load screen with the Ubuntu logo and crash. Sometimes turning off the laptop fixed things, but not this time.

I can still access safe mode and everything looks normal, even the SD card drive has disapeared. 

Can someone please help? 

Thanks

---

### Post by TheFu on 2019-01-31
It is bad to disrupt an open file system, ever.  That means pulling the storage out before the system is either shutdown or before the file system is unmounted using the "umount" command.  An actively use file system cannot be dis-mounted.

A corrupted file system needs to be corrected. Normally, this is handled automatically.  If not, using the safe mode, run **fsck** against the file systems that are Linux native (not fat-whatever or NTFS). If it can be fixed, that command will.

But SD cards do wear out and they do fail.  Running an OS off one causes many more cycles than they were designed to handle.  If the file system is mostly full, the risks are greater.

If you are afraid to run the fsck command, figuring out exact options on your own, run **sudo fdisk -l** and post the output.
**df -hT** would be helpful too.

---

