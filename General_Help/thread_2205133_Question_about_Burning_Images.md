---
title: "Question about Burning Images"
date: 2014-02-12
forum: General Help
---

### Post by nemesis045 on 2014-02-12
Hi all,

I am trying to make bootable discs for Ubuntu 13.10 64-bit (925 MB ISO) and Hiren's Boot CD (624 MB ISO). I have the ISO's for both. I have a few questions:

1. I just installed K3B v2.0.2. How do I make a bootable disc. I see two options:
    a) Project -> Edit Boot Images, when inside a 'New Data Project'
    b) Tools -> Burn Image
Can I use either? I need each ISO to be bootable on the disc. What's the difference between these two options?

2. I was wondering if I could burn both these images onto a single DVD and when booting through the DVD, choose which image to boot. Is this possible? If so, how can I pull this off in K3B? I ask this because I would end up using two DVD's for the purpose (or a DVD and CD), otherwise. Plus, it's a learning process in what's possible with CD burning in general.

3. The Hiren's file came as a zip file which contains the ISO with a few other files. If someone's done this with Hiren's Boot CD, do you know if I should burn the other files as well or only the provided ISO?

Really appreciate any input here

Thanks,
Ian

---

### Post by The Cog on 2014-02-12
1: For ISO images, you need to use the Tools->Burn Image option.
ISO images are complete images of a CD including the bootable code. Making a data CD will simply put files on the CD.

2: I don't think you can. Each ISO image is a complete CD/DVD image. You would need to create new boot code to offer a choice of where to go next.

3: I don't know what the other files are, but once again, the .ISO is an image of a complete CD. You can't add files to that without it being a different CD.

---

### Post by sudodus on 2014-02-12
1. Use Burn Image!

It burns the iso image to the device (which is different from a 'data project', where you do something like high level copying files between mounted partitions)

2. It is possible but very complicated. You might be able to remaster a system on a DVD, which can boot from iso files in two steps, but that is for gurus.

3. I don't know about Hiren's boot CD, but normally you burn one ISO file (and nothing else) to each CD or DVD disk. The other files are probably documents describing the system, and you can keep them on a HDD.

-0-

It is also possible to boot directly from many (not all) iso files via grub. Today one of the most common methods is to make a ***USB*** boot pendrive from the iso file. See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

There are several methods to make multi-boot USB drives, but I think it is easier to succeed, if you store the iso files on a hard disk drive, and use the USB pendrive as a temporary device by flashing the iso you need 'right now' (flash alias burn alias 'low level copy to the device' or install with some special tool).

---

### Post by nemesis045 on 2014-02-13
Thanks for the replies, sudodus & The Cog!

Do you know where I could set the Volume ID for the final DVD? K3B automatically sets this and I can't seem to edit it.

---

### Post by sudodus on 2014-02-13
I think you are right about that. When you make an audio CD or a data CD/DVD, you can set the volume id, but burning an ISO is to copy it without changing anything, simply cloning it.

---

### Post by mastablasta on 2014-02-13
you can however create multiboot USB using for example Yumi. a 16 GB usb stick can hold multiple OS.

booting from USB is an issue on older mashicnes. for those you can use plop boot manager (can even boot the OS on USB form a floppy disk).

---

