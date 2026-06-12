---
title: "I am looking to wipe my HDD"
date: 2014-01-04
forum: General Help
---

### Post by Brendan.M.Gordy on 2014-01-04
Hi,
I need to wipe my HDD but my laptop wont boot to the USB i have put in. Does anyone have any idea how I could wipe a drive i am booted to? I have tested the USB on my desktop and it booted fine with no problems whatsoever. Please Help!!!!!

Thanks,
Brendan

---

### Post by Mark Phelps on 2014-01-04
You can't wipe a drive you are booted to because that drive is "in use".  You have to boot from something else.

---

### Post by Brendan.M.Gordy on 2014-01-04
Any ideas on how to wipe the drive then?

---

### Post by r3dd on 2014-01-04
Does the laptop have a a cdrom?

 I use an ArchLinux cdrom to wipe drives:

This method simply covers all of the data with zeros making it empty again.
```

dd if=/dev/zero of=/dev/sda bs=1M

```

This method fills the drive with random data. It is generally used to increase encryption since an analyst can not look at the drive and see where the used portions of the drive are. If you choose this method, prepare to wait a few days depending on the size of your drive. The computer has to generate the random data before it can write it.
```

dd if=/dev/urandom of=/dev/sda

```

---

### Post by Brendan.M.Gordy on 2014-01-04
No CD-ROM and I seem unable to boot to any other device other than the HDD here is what i have done:

1. Put USB at top of boot order
2. Disabled Fast Boot (which skips looking for usbs to decrease boot time)
3. Disabled all boot options other than the USB (It shoots me straight to the BIOS On boot)

I feel almost as if the computer is not seeing the USB in time to boot from it... it is a laptop so maybe power is not reaching the USB until it is too late????

---

### Post by r3dd on 2014-01-04
Here is one option... take the hard drive out of the laptop, put it in an enclosure, and use another system to wipe it.

It will not do anything for your USB boot problem. In fact, if you wipe it and can't boot from USB you may just have a brick after you are done.

---

### Post by Dave_L on 2014-01-04
I've seen some articles about booting Ubuntu from RAM. Would that allow you to unmount the hard drive and wipe it? I've never tried that, but it could be worth investigating.

Are you wiping your hard drive because you're giving the laptop to someone else? A alternative would be to create a new minimal size partition, wipe that partition, install Ubuntu (or any other GNU/Linux distribution) on that partition, boot from the new partition, and then wipe the rest of the drive.

---

### Post by Dave_L on 2014-01-07
Here's a method that should work. I had forgotten about it. You can boot from an .iso. The boot partition is loaded into RAM, so you should be able to do whatever you want to the hard drive.

This example uses "ubuntu-12.04.2-desktop-i386.iso", but other versions should work the same way.

You'll need to do all of this using root, i.e., sudo.

1) Create the subdirectory /boot/iso and put a copy of ubuntu-12.04.2-desktop-i386.iso there. (The file could be located elsewhere; this is just a convenient place to put it.)

2) Add the following to the end of the file /etc/grub.d/40_custom:

(You may want to make a backup copy of this file first.)

```
menuentry "ubuntu-12.04.2-desktop-i386.iso" {
set isofile="/boot/iso/ubuntu-12.04.2-desktop-i386.iso"
loopback loop **(hd0,1)**$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
```

"(hd0,1)" identifies the hard drive, and the partition on that drive, where the .iso file is located. In this example, it's the first hard drive (0) and the first partition on the drive (1). Your configuration may differ.

If you haven't made any previous changes to that file, it should now look like this:

```
#!/bin/sh
**echo "Adding 40_custom." >&2**
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

[b]menuentry "ubuntu-12.04.2-desktop-i386.iso" {
set isofile="/boot/iso/ubuntu-12.04.2-desktop-i386.iso"
loopback loop **(hd0,1)**$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}[/b]
```

(I also added the "echo" command, but that's not essential.)

3) Run update-grub.

```
sudo update-grub
```

4) Reboot, and select the .iso entry from the grub menu when it appears.

---

