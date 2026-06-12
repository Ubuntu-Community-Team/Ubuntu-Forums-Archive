---
title: "Getting system booting after Operating System failure"
date: 2014-10-03
forum: General Help
---

### Post by WanderingAlbatross on 2014-10-03
Hello All,
Just dealt with an extremely challenging situation for which I searched the internet for advice and found nothing.  Since I muddled my way through it, I thought I would post so that it may be of help to others.

Situation: Given laptop (mother-in-law's) to fix from unknown disaster that caused system not to boot to Ubuntu.  She does not access the internet, so the error was not caused by updates.  Boot would fail with a failure to mount /sys at /root/sys, /proc at /root/proc, and one more I can't remember right now.  The point is that there had been a hard drive failure.  I believe caused by not shutting down correctly, or possibly running out of power on the battery.  All sources on the internet were suggesting boot with a recovery CD, which would be good except this computer's CD laser stopped working before we gave her the machine, and it also is too old to boot from USB.  So what could I do?

Solution: So here is a way to boot an operating system manually from grub on a crashed system.  This computer has the classic MBR on it, not EFI.  So, I don't know if it will work for everyone, but it worked for me:

Hold shift to access the grub menu before it tries to boot. (If your grub is not automatic it brings you here anyway.)
Hit C to bring you to the grub command line.
```
insmod ext2
```
(or what ever filesystem type it is.)
```
set root=(hd0,1)
```
To let grub know where root is.
```
linux (hd0,1)/boot/vmli
```
At this point I hit tab, and grub autocompletes as far as it can.  It will usually show you several linux kernels.  Add, to the same line after you complete:
```
root=/dev/sda1 break=init nomodeset
```
This is assuming root is on the first partition.  The break command causes boot to stop at this stage in the boot process.  Don't add nomodeset unless the computer had this in it's grub boot commands.
```
initrd (hd0,1)/boot/init
```
At this point I tab again to let it finish as much as it can on it's own.  This let's it know the initial ram disk, an important component to get the early system running around the kernel.

Hopefully hitting enter will get you somewhere.  It stopped on me where I expected, at the init stage.  It will give a prompt with (initramfs).  I looked around a bit, but didn't honestly do much of anything there.  Then I typed:
```
exit
```
and it continued with boot.  At this point we are somewhere in the operating system.  I toggled ctrl-v to watch some of the messages.  It looked like what had caused the error was a the filesystem had been stopped in the middle of doing something because it complained about a temp file in the /Temp directory, and that the system needed me to manually run a fschk.  How happy I was when I saw the normal Ubuntu Gui come up, and heard the log in sound.  Success!

---

