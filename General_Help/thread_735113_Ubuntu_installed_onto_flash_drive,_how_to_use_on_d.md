---
title: "Ubuntu installed onto flash drive, how to use on different laptops?"
date: 2008-03-25
forum: General Help
---

### Post by mlapaglia on 2008-03-25
Hello, I've installed Ubuntu Gutsy onto an 8gb flash drive, and have it succesfully booting from the computer it was installed onto. I have a MBR on my laptop's hard drive, and a MBR on the flash drive, so when I tell the computer to boot from the flash drive, i see a grub that only has booting options for it, and not the hard drive, so it is completely independent.

How can I get a regular Ubuntu installation to act like a livecd, in which it would detect the different hardware and load accordingly. I am using this to demonstrate to other people how ubuntu runs on their laptop, and giving them a test run so they can decide for themselves. 

I can't use a regular livecd on my flash drive because I need something that will save thunderbird changes, extra programs installed apart from synaptic, and customizations I have to make to get Ubuntu working with my school's network.

As far as i know a livecd with casper-rw on it can only save changes that are made in certain circumstances. is this true?

Thanks for your help!

---

### Post by cdenley on 2008-03-25
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
I believe you can change whatever you want, it's just that unless your casper partition is writable, the changes will be lost when you reboot.

---

