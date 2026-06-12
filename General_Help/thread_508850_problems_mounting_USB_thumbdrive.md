---
title: "problems mounting USB thumbdrive"
date: 2007-07-24
forum: General Help
---

### Post by whereareyoutakingme on 2007-07-24
i have a 2gb USB thumbdrive made my kensington.  when i insert it into my usb port on the front of my tower nothing happens.  i'm sure the ports work because i have used my USB mouse from those ports several times.  i have searched all afternoon through several threads and found several people posting answers to the questions posed in those threads however my USB device still won't mount.  at one point it was visible in "Computer" but no icon appeared on my desktop, and when i clicked on the icon in "Computer" all it did was display an error that "Unable to mount device.  There is probably no media in the drive." <--something along those lines.  but now there is nothing, the only evidence that exists to prove that Ubuntu knows about the USB drive is in the device manager where is shows it as /dev/sdc.

I have tried modifying the fstab and i have tried using pmount.  Modifying fstab doesn't seem to have any affect and when i type: sudo pmount /dev/sdc UsbStick........i get the following error:

mount: wrong fs type, bad option, bad superblock on /dev/sdc,

       missing codepage or other error

       In some cases useful info is found in syslog - try

       dmesg | tail  or so



mount: wrong fs type, bad option, bad superblock on /dev/sdc,

       missing codepage or other error

       In some cases useful info is found in syslog - try

       dmesg | tail  or so

On a side note: when i insert the USB drive into my WindowsXP machine, it recognizes it but says it isn't formatted and asks me to format it, I have not done that yet as I would very much like to save the data that exists on the USB drive.  I should also point out that the drive functioned perfectly before I started trying to use it in Ubuntu.

That being said, how do i get it to mount, and furthermore, auto-mount when i insert it into the front panel ports?

---

### Post by ddrichardson on 2007-07-24
Sorry the drive has become corrupted. You may need to search google for data recovery tools.

---

### Post by 56seeker on 2007-07-24
One thing I've found when using a USB drive on both Windows and Linus is that Linux is very fussy about the way tou remove the drive from Windows.

On a Windows box I'm used to just pulling out the USB drive from the windows box, but if you do do that Linux probably won't accept it.

I've found I have to right click on the USB drive in windows explorer and choose "eject" (or clicl on the USB icon in the task bar and stop the device)

If I neglect to do that I can't use the USB drive in Linux. And the same goes for Linux: never just remove the drive but right click on it in nautilus and unmount it properly.

---

### Post by benx009 on 2007-07-24
> **whereareyoutakingme said:**
> On a side note: when i insert the USB drive into my WindowsXP machine, it recognizes it but says it isn't formatted and asks me to format it, I have not done that yet as I would very much like to save the data that exists on the USB drive.  I should also point out that the drive functioned perfectly before I started trying to use it in Ubuntu.

That being said, how do i get it to mount, and furthermore, auto-mount when i insert it into the front panel ports?

sorry, but you will have to format your drive.  if Windows XP says to do so and you cannot mount it in linux, then the data on has gone bad.  you can try using various disk recovery programs to recover your valuable data, but you would want to reformat the drive after that asap if you don't want to run into further troubles.

---

### Post by kathmary on 2007-08-02
For what it is worth, I have the same problem.  I have found that Ubuntu Feisty does not recognize my usb 2.0 drive in the  1.1 front.   If your front usb is 1.1, you might try plugging it into a 2.0 usb connection.  Mine are on the back of the computer.  When I do this the drive works correctly.  Also, you might try plugging the drive in your front usb before you boot ubuntu.   Although this did not work on my machine, it might work on yours.

---

### Post by ddrichardson on 2007-08-03
I had a similar problem, quite seom time ago. What happened was I dragged a file onto the USB pen drive's icon on the desktop and for some reason it altered its partition table. Windows asked to format it then failed. I had to use kanotix to re-partition it, then re-format it.

---

### Post by strabes on 2007-08-03
Assuming your flash drive's /dev location is /dev/sdb1, run this to format it and re-create the fat16 filesystem. "UbuntuUSB" is the drive's name. Change it to your liking.

```
sudo mkfs.vfat -F 16 -n UbuntuUSB /dev/sdb1
```

Warning: This will erase all data on your flash drive.

---

