---
title: "New to Ubuntu"
date: 2006-12-17
forum: General Help
---

### Post by waynecarsen on 2006-12-17
I have been having a blast playing around with this OS, and love what it can do.

My question is Can I boot off a USB drive?

When I load it off the CD, I get the USB drive to show, and even the two partitions will show, I can see the contents, and open files, the Drive how ever is read only, I would like to install the software on there and boot off it.

I tried making the drive read and write and so on, but the drive can not be changed in any way even rename. I formated the partition Linux, and that did not work. Because the drive is read only I can't partition in Ubuntu.

Any Ideas would be a great help, if this is even possible.

I thank you in advance for your help. Happy Holidays.

Wayne

---

### Post by lamego on 2006-12-17
Install Ubuntu into a bootable USB device is not a simple task, read how to do it:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by maxamillion on 2006-12-17
I believe that booting from a usb pen drive will be subject to the capabilities of your motherboard than anything to do with ubuntu or its quite possible I am not understanding your question fully

---

### Post by meng on 2006-12-17
Yes you need to have a BIOS which is capable of booting from USB. Check your BIOS settings to see if this is an option.

---

### Post by waynecarsen on 2006-12-17
Thank you for your help so far.

The Drive is a USB hard drive 80GB, I believe I can boot off it if I could install the software.

But I can not write to the drive that's my problem. Changing the preferance will not work as it's a "read only" status drive, that is being locked out bu something, it works fine under windows?

Thanks again

---

### Post by maxamillion on 2006-12-17
sudo chmod +r /path/to/mount_point

that command should allow you to write to the drive

---

