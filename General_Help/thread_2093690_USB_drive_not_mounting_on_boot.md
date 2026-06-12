---
title: "USB drive not mounting on boot"
date: 2012-12-11
forum: General Help
---

### Post by sploiz on 2012-12-11
i am using xubuntu 12.04 and it is a live cd i'm working on which boots from a usb stick. and i don't have too much experience with linux, i was blindly tossed into the project.

when i have the system booted and plug in another usb drive it will mount it in /media with the name of the drive. when i boot with the extra usb drive attached it does not mount the usb drive until i click on the drive in the left menu in thunar. after i click on it, it will get mounted as if i just inserted it.

now i have done a lot of searches for this issue and usually it is solved by an entry to the fstab, but it not always going to be the same drive that gets used. i was hoping that i could add something to the startup that could mount the drive. 

i hope this is clear, it can be difficult to describe what i don't understand.

---

### Post by LewisTM on 2012-12-11
One way to always mount a USB drive at login is to use USB paths. As long as you always plug the drive in the same port, you should be fine.

First, find the USB path to your device. 
1) Unplug  the device
2) Open a terminal and [FONT="Courier New"]cd[/FONT] to /dev/disk/by-path
3) Type [FONT="Courier New"]ls -al[/FONT]
You will get a list of paths like this
> lrwxrwxrwx 1 root root  10 Dec 11 08:44 pci-0000:00:1f.2-scsi-0:0:0:0-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 Dec 11 08:44 pci-0000:00:1f.2-scsi-0:0:0:0-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 Dec 11 08:44 pci-0000:00:1f.2-scsi-0:0:0:0-part4 -> ../../sda4

4) Plug in the device and execute another [FONT="Courier New"]ls -al[/FONT]. Write down the new path that has appeared, which might look like 
> pci-0000:00:1d.0-usb-0:1.5:1.0-scsi-0:0:0:0-part1
It's a new symlink leading to ../../sdX1 where X is a letter.
5) Now you have your USB path. If you plug in a new device in this port, it may create a different sdX1 for Linux but the path will remain the same. Let's use that.
6) In your Startup Applications, add this new entry
bash -c "gvfs-mount -d `readlink -f /dev/disk/by-path/<path_to_your_USB_port>`"

That's it! Cheers!

---

### Post by sploiz on 2012-12-13
thank you for your response. that did the trick! i didn't know about the /dev/disk options or the mount command. so much to learn.

---

