---
title: "how to remove kubuntu"
date: 2007-11-11
forum: General Help
---

### Post by dafunkmon on 2007-11-11
currently i have kubuntu 7.10 installed fully onto my only hard drive, i tried to reinstall windows xp onto my hard drive but once the actual installation was supposed to begin i got a blue screen telling me to scan for viruse, or remove any new hard drives, or configure and terminate the hard drive. so now i want to remove ubuntu completely and wipe my entire hard drive how would i do those things?

---

### Post by justin_guerin on 2007-11-11
The windows installer program will take care of removing kubuntu from your hard drive.  However, it seems the installer program is having trouble with your drive configuration.

First off, how many hard drives do you have in your computer?  Windows requires it be installed on the first hard drive.

Also, if you have more than one hard drive, make sure they're properly configured.  Only one drive can be the master on the IDE bus, and the other must be the slave.  Either that, or both drives must be configured for "cable select".

Finally, make sure the disk you are using to install Windows XP is an actual install disk.  Computers shipped with Windows pre-installed commonly ship with only a system restore disk, and that disk cannot be used to install windows from scratch because they rely on a system restore partition that's hidden by default.  If your hard drive no longer has that system restore partition, you'll need a full install disk.  Some vendors will provide you with an actual install disk, if you request it.

Good luck,
Justin

---

### Post by dafunkmon on 2007-11-11
i have one hard drive, and im trying to install with the full cd installer not a restoration cd

---

### Post by justin_guerin on 2007-11-11
In that case, you can try using the Ubuntu installer to format your hard drive with an NTFS file system, then install using the Windows installer.  But the windows installer should give you the option of formatting the drive.

To partition with the Ubuntu installer, boot from the installer, and run the System -> Administration -> Partition Editor program.  Once you format, reboot with the Windows install disk in the CD ROM.

Hope that helps,
Justin

---

### Post by NerdTv on 2007-11-11
I dont know if this helps but I had problems going from ubuntu (or any linux distro) back to windows... Installation from a retail cd failed.  I had to erase the mbr.(Still dont know why)  Window's fixmbr did not work. I had to boot from a linux live cd and run this to erase the mbr
```
dd if=/dev/zero of=/dev/hda bs=512 count=1
```

**BE CAREFUL THIS WILL ERASE YOUR MBR!**  Then reinstall windows. I hope this helps.

---

### Post by dafunkmon on 2007-11-11
alrite but do i do that in the ubuntu splash screen or while on the ubuntu desktop?

---

### Post by NerdTv on 2007-11-11
Oh sorry... boot up with ubuntu live cd after completely booted up go to     Application -> Accessories -> Terminal then type

```
sudo dd if=/dev/zero of=/dev/hda bs=512 count=1
```

Thats it. Shutdown and try to reinstall windows.

---

### Post by dafunkmon on 2007-11-11
nope didnt work, still get a blue screen that says:
a problem has been detected and windows has been shut down to prevent damage to your computer.

if this is the first time youve seen this stop error screen, restart your computer. if this screen appears again, follow these steps:

check for viruses on your computer. remove any newly installed hard drives or hard drive controllers. check your hard drvie to make sure it is properly configured and terminated. run chkdsk /F to check for hard drive corruption, and then restart your computer.

technical information:

***stop: 0x00000007B (ocf78d2524, 0xc00000034, 0x00000000,0x00000000)

and that is what happens right after i put the cd in and its says at the very bottom, after preparing installation, starting windows installation and then this happens.

---

