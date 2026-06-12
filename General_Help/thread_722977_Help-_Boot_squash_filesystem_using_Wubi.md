---
title: "Help- Boot squash filesystem using Wubi"
date: 2008-03-13
forum: General Help
---

### Post by mburris on 2008-03-13
I have installed Hardy Kubuntu KDE4 via wubi on my vista NTFS partition all works great.  

For a project I'm working on, I'd like to boot the system into a casper / Live CD environment from a Squash File System (filesystem.squashfs) that I customized based on Ubuntu 7.10.

Here is what I've done so far:
Edited the menu.lst found in the folder C:\ubuntu\disks\boot\grub with the following:
```
title		Start SquashFS
root		(hd0,1)/ubuntu/disks
kernel		/boot/vmlinuz boot=casper ramdisk_size=1048576 root=/dev/ram rw quiet splash --
initrd		/boot/initrd.gz
```

now I have put the required "filesystem.squahfs" "initrd" and "vmlinux" files that are referenced in the menu.lst code above into the folder: C:\ubuntu\disks\boot.

So when I restart the PC it normal Vista boot screen appears, and I can select the Kubuntu KDE entry that Wubi setup.  After that Grub loads, if I press escape I view my boot options from the menu.lst file.  When I select "Start SquashFS" it does start to load.  I get the custom Usplash but then it fails and reverts back to the initram prompt.  When I CAT the Casper.log file, i can isolate the error message:
something like "can't find and squash filesystem files"

Will this even work?  Do i need to edit a casper script to allow it to find the filesystem.squashfs file i have placed inside "C:\ubuntu\disks\boot"?

---

### Post by ago on 2008-03-13
The system is setup so that it will look for an ISO on HD (if you pass it as a boot parameter), but that does not extend to a squashfs file.

If you want to do that you will have to generate a custom initrd that can take an optional squashfs argument and overrides the scripts/casper settings.

That said I provided hooks for overriding files on the existing ISO...

Any file in /ubuntu/install/custom-installation/iso-override

will be copied on top of the mounted ISO before the system pivotroots

---

### Post by mburris on 2008-03-13
> 
If you want to do that you will have to generate a custom initrd that can take an optional squashfs argument and overrides the scripts/casper settings.

I am familure with extracting and editing the script files that reiside in the initrd.gz file, however I'm not sure exactly what to change in the /scripts/casper script file.  

Is this problem due to the host filesystem being NTFS?

I think getting this working would be useful because it could allow an Ubuntu Live enviroment to be previewed without burning a CD...

Any specific help would be greatly appreciated

I was able to find this article: [http://www.sysresccd.org/Sysresccd-manual-en_Easy_install_SystemRescueCd_on_harddisk]("http://www.sysresccd.org/Sysresccd-manual-en_Easy_install_SystemRescueCd_on_harddisk")
it shows how to exactly what I want to do, but it is using the "System Rescue CD" which is not based on debian, but maybe it could offer some pointers.

---

### Post by mburris on 2008-03-13
I found this:
[https://bugs.launchpad.net/ubuntu/+bug/135029]("https://bugs.launchpad.net/ubuntu/+bug/135029")
I followed the instructions, but still fails with the following error:
```
mount: Mounting /dev/sda2 on /cdrom failed: Success
Unable to find a medium containing a live file system
```

when it kicks me back out to the initramfs prompt, i can cd into the cdrom directory... when i do an "ls" it is the content of my NTFS drive... so my NTFS drive is infact now being mounted by the casper script.... but why can't it load the /cdrom/casper/filesystem.squashfs file??

---

### Post by ago on 2008-03-13
> **mburris said:**
> I think getting this working would be useful because it could allow an Ubuntu Live enviroment to be previewed without burning a CD...


Ah that's easy

Wubi had a mode for that but it has been disabled in 8.04 (see read-only mode in wubi 7.10).

In 8.04, simply run wubi, then remove automatic-ubiquity and ubiquity-debug from /ubuntu/install/boot/grub/menu.lst. When you reboot you should be in a live environment.

The above requires a full ISO, but no need to burn anything.

---

### Post by mburris on 2008-03-15
I was actually able to get this working... so now I can use Grub4dos to boot into a LiveCD's squashfs file residing in a folder named "casper" in the root of an NTFS windows (2000 XP Vista) partition!

---

### Post by Shifter952 on 2008-11-11
What was the final solution to this issue?  I am attempting the same thing.

---

### Post by mburris on 2008-12-21
> **Shifter952 said:**
> What was the final solution to this issue?  I am attempting the same thing.

I had to include the .disk folder that you can find on the root of the live CD.

Just place it in the root of your NTFS partition

---

