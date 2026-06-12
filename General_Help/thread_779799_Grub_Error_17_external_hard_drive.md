---
title: "Grub Error 17: external hard drive"
date: 2008-05-03
forum: General Help
---

### Post by Mchl923 on 2008-05-03
I thought I was getting Grub Error 17 randomly, but I have narrowed the cause down: whenever my NTFS external hard drive is attached, I get the error also when either of my FAT16 flash drives.  Is there a way to fix this?

---

### Post by Aearenda on 2008-05-03
So with external drives attached, they somehow displace your internal drive from being booted - weird! Maybe try changing the BIOS boot order so that external drives come last. I've seen this reorder the drives on one system.

---

### Post by mooglinux on 2008-05-03
i have a very similar problem. i have an extra ahrd drive i wish to connect, but whenever it is plugged into my system (internal hdd) everything explodes. no amount of rearranging the boot order, fiddling with super grub disk, or trying to install grub from the live cd will fix it. as soon as i disconnect the device everything runs beautifully.

my guess is that plugging it in changes what drive is hd0 hd1 and so on, so grub tries to boot to a different disk than it did before. but i have no idea how to fix it. i would venture a guess that this is the same problem you are having

---

### Post by Mchl923 on 2008-05-03
> **Aearenda said:**
> So with external drives attached, they somehow displace your internal drive from being booted - weird! Maybe try changing the BIOS boot order so that external drives come last. I've seen this reorder the drives on one system.
Thats the first thing I tried: didn't help.

---

### Post by Aearenda on 2008-05-03
How about reinstalling grub with the external drive present? But I guess then it will fail without the external drive :-(

---

### Post by Mchl923 on 2008-05-03
sorry for the delay, I've been real busy lately.  I have attempted a reinstall of grub before this issue, but I never really figured out how to do it.  Can you use the super grub disk?  I eventually had to recover windows which restored MBR and then I installed ubuntu again which reinstalled grub and salved the problem at hand.  Can I avoid all this?

---

### Post by Aearenda on 2008-05-04
Best way to reinstall Grub is to boot off an alternate installation CD and choose the repair option there. Tell it which partition the /boot folder is in, and to reinstall Grub. 

However, before you do that, I've just come across this thread [http://ubuntuforums.org/showthread.php?t=676909](http://ubuntuforums.org/showthread.php?t=676909) which outlines a possible solution to this problem using LILO. Is it possible to turn ACPI off in your BIOS as a way of testing whether this workaround is appropriate? If so, what I would do is this:

1. Shutdown the computer and unplug the external drive.
2. Enter BIOS setup and disable ACPI.
3. Start up and see if everything works - it should.
4. Shutdown the computer and plug the external drive back in.
5. Start up again and see if everything works - this is the actual test!
6. Shutdown the computer and unplug the external drive.
7. Enter BIOS setup and enable ACPI.
8. Start up and see if everything works - it should.
9. Shutdown the computer and plug the external drive back in.
10.Start up again and see if everything works - it probably won't, and this verifies the test.
11.Shutdown the computer and unplug the external drive.
12.Restart, test finished.

Please let us know what happens!

---

### Post by Mchl923 on 2008-05-04
thanks, I'll try that.

---

