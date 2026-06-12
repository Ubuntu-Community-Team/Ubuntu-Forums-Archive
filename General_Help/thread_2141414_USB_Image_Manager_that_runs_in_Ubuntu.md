---
title: "USB Image Manager that runs in Ubuntu"
date: 2013-05-02
forum: General Help
---

### Post by Locane on 2013-05-02
Hi.  I work with a lot of different flash drives every day, and I'm looking for a USB image management utility that will do the following:

- Read an image from a usb drive to file while preserving its boot capability
- Write an image from file to a usb drive while preserving its boot capability
- Capable of making a bootable DOS usb drive

I haven't found any linux utilities that do this yet, and I was hoping to reach out to the community here to see if there's something out there I haven't found.  I've been all over Google and the major utilities, but they won't read a flash drive image and preserve the boot capabilities of it.

I'd be willing to pay for software that did this cleanly and easily, too.  It doesn't necessarily have to be free.

Thanks in advance!

--Locane

---

### Post by Cheesemill on 2013-05-02
The first 2 can easily be accomplished with the dd command.

Read an image...
```
dd if=/dev/sdX of=filename.img
```

Write an image...
```
sudo dd if=filename.img of=/dev/sdX
```
Where /dev/sdX is your USB device and filename.img is your image file.

You can use [Unetbootin]("apt://unetbootin") to create a bootable USB stick with FreeDOS on it.

---

