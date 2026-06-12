---
title: "Hangs on Reboot with USB HDD"
date: 2007-02-24
forum: General Help
---

### Post by eangulus on 2007-02-24
Hi all.

Noob here with linux but willing to learn....

Got a fresh install of Ubuntu Server 6.10

Boots and reboots fine.

Bit if I have my USB 2.5" HDD plugged in it boots but hangs on a reboot.

THe drive is detected but I havn't mounted it yet.

What could be the issue.

---

### Post by tgalati4 on 2007-02-24
Sounds like a drive mapping issue.
When booted into Ubuntu server what is the output of:
more /boot/grub/device.map

Boot with the live CD and the USB drive.  
Once again examine the device.map to see how the drive mapping has changed with the USB drive plugged in.

Also check your BIOS, perhaps you have USB boot enabled but you don't have a valid boot image on the external disk.

Keep the faith.  We'll get if figured out.

---

### Post by eangulus on 2007-02-25
I could be wrong but I think you have misunderstood.

Ubuntu is installed on a 20Gb internal HDD. The 80Gb USB drive will hopefully be used for file serving using SAMBA later.

As I had said before I have a clean install on the 20Gb Internal.
If I have the USB drive plugged in it hangs on reboot and on shutdown -r now

If I unplug the drive it works perfectly.

I have notice that when shutting down the USB drive light blinks then it all stops. I think it has trouble letting go of it.

Also just a side note too. I did say I was a noob. So what was suggested before is fine but please give me explicite instructions on how to check things...
Hopefully I then might learn something..

oh and an advanced thanks to anyone tryig to help.

---

### Post by eangulus on 2007-02-25
Can anyone help me at all?

I am starting to think this may be a bug, as I can't find an answer to this anywhere.

---

### Post by tgalati4 on 2007-02-25
My fault.  Yes it looks like a BIOS issue.  On cold start the USB drive works and shutdown continues normally.

On reboot, (warm start) the USB drive refuses to let go.

Can you manually unmount it then reboot?

```
sudo umount /media/myUSBdrivethatisdrivingmenuts
```

If you can then you need to add a line to your reboot script to always unmount the drive before shutdown.

---

### Post by eangulus on 2007-02-25
ok I tried the unmount things and it still didn't work.

---

### Post by tgalati4 on 2007-02-25
It could be a cheap USB drive enclosure.  Do you have a brand-name enclosure like LaCie that you can test.  It is possible that the USB driver in the enclosure is not compliant or the port in the laptop is not compliant, or some other subtle conflict.  You could also try swapping USB cables.  Is the drive connected to a USB multiport?

Also, external drives need POWER.  Is this drive running off of USB power or is there an external power source?  It's possible that during an unmount that the drive spins up drawing a lot of power and causing the controller to hang.

I'm reaching here folks.  Any other ideas?

---

### Post by tgalati4 on 2007-02-25
Has the 80 gb USB drive been formatted yet?  If not, try sudo cfdisk /dev/sda
and put some partitions on it.  Then format using sudo mkfs -t ext3 /dev/sda1

It is possible that if the drive is not formatted, then that puts the hardware in an indeterminant state.

What is the output of 

more /boot/grub/device.map

---

### Post by eangulus on 2007-02-26
The drive is formatted.
 
It runs on USB power.
 
I have tried another External USB drive. It is externally powered and does the same thing.
 
I think we should go back to the computer itself as I have just installed ubuntu on another box and both HDD attached and it is working sweet.
 
Here is the specs on the box thats giving the troubles.
 
[http://www.motium.com.au/products/mpc/mpc/index.html](http://www.motium.com.au/products/mpc/mpc/index.html)
 
Hopefully that may shed some light.

---

### Post by tgalati4 on 2007-02-26
That's a slick little machine.  Does the external power supply get extra hot?

So you determined that either a USB-powered drive or externally powered USB drive has trouble unmounting.

As you know during shutdown or reboot, all of running processes are stopped and mounted file systems are unmounted.  If a file system (USB Drive in this case) refuses to let go then shutdown will not continue to system halt.

So your reboot problem is really an unmount problem with USB drives connected to an ultra-small-form-factor PC.  Is there a firmware update available for the machine?  Have you contacted the manufacturer about this problem?

It sounds like a hardware/firmware problem, not an Ubuntu problem.  If you can't unmount the drive with a sudo umount /dev/sda1 (or whatever your drive is registered as (check df -h)) then there is little you can do about it.

Now you can yank the USB cord, but this is dangerous if the drive is mounted and there is a possibility of a disk write.

Try a USB memory stick.  Can you manually unmount that?  It's really just a small disk drive.  Try as many memory sticks and external devices as possible.  Borrow drives or CD/DVD readers from friends and try to manually unmount them.  If you still have problems with all of these devices, then I would conclude that it is a BIOS/hardware problem.

Are there any settings in the BIOS that relate to USB?  Power management stuff?  Try flipping BIOS switches to see if there is a change in behavior.

---

