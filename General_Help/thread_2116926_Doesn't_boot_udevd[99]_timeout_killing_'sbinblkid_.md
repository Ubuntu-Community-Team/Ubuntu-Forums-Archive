---
title: "Doesn't boot: udevd[99]: timeout: killing '/sbin/blkid -o udev -p /dev/loop4' [144]"
date: 2013-02-17
forum: General Help
---

### Post by Myst1234 on 2013-02-17
Hello all,

So I tried a few security and quality tips from a known and trusted Ubuntu/Linux blog you can check it out [HERE]("https://sites.google.com/site/easylinuxtipsproject/Home") and upon reboot of my system it went STRAIGHT to the GNU Grub Menu where it offered up 4 options

1. Ubuntu, with Linux 3.2.0-37-generic
2. Ubuntu, with Linux 3.2.0-37-generic (recovery mode)
3. Memory test (memtest86+)
4. Memory test (memtest86+, serial console 115200)

I of course picked the first option which did an odd old DOS-like read out and then continuously gave me a udevd timeout of a couple things.

I then tried recovery mode which gave ne the same read out at first and then a few things like above but then kept repeating -  udevd[99] : timeout: killing '/sbin/blkid -o udev -p /dev/loop4' [144]

Can anyone help me sort this out? I have some precious files on the computer in question, and I cannot stand the thought of losing it all with a fresh install. 

HELP!!

Thanks in advance

---

### Post by Myst1234 on 2013-02-17
Any help at all would be reallllllyyyy helpful. Anyone have any idea what;s going on? Anyone?

---

### Post by Myst1234 on 2013-02-17
Update-

I've done the memory test and it found no errors.

I'm now doing a hard disk self test, will post results

---

### Post by Myst1234 on 2013-02-17
All hard disk tests passed.

So there's no lost or corrupt memory, there's not lost or corrupt disk...

What the hell is going on?!

---

### Post by Myst1234 on 2013-02-17
I'm able to access the grub command line, can I try anything from there?

---

### Post by gordintoronto on 2013-02-18
I don't have any suggestions about how to fix your computer. It might help if you said what you did to it.

However, you should be able to boot from CD/DVD/USB, and copy your precious files to DVD/USB/the cloud.

---

