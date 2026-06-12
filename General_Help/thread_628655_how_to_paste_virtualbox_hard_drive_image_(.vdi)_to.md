---
title: "how to paste virtualbox hard drive image (.vdi) to an empty partition?"
date: 2007-12-01
forum: General Help
---

### Post by ski309 on 2007-12-01
Hi all.  Here's my story:

I bought a Dell E1405 laptop a year and a half ago, with Windows XP Home installed.  I eventually converted it to 100% Ubuntu laptop.

My friend just bought me a PC video game for my birthday, so I now have a reason to reinstall Windows on the system, but when I tried to install my old XP Pro CD, I got the blue screen of death from the file pci.sys.

I've had a VirtualBox installation of XP Pro for a long time, and I was thinking:  would it be possible to paste the .vdi file that contains Windows into an empty partition, and edit my GRUB file to show the choice of that partition?

If not, any other suggestions?

---

### Post by spupy on 2007-12-01
I had a similar problem - i wanted to move a Windows install from a virtual machine to a partition. So i "pasted" the image from the VM on the partition. Of course it didn't work. The problem is that the .vdi image is not formatted the same way as a normal partition - that is, it has some file headers, since its a file, and some other stuff specific to the virtual machine. The only virtual machine whose image might work in my knowledge is Qemu, because it uses raw disk images. VirtualBox and VMware don't use such raw images.

---

### Post by Craigus on 2007-12-01
> when I tried to install my old XP Pro CD, I got the blue screen of death from the file pci.sys.

The question is - why did this happen ?

Is the CD badly scratched or dirty ? If so, you might be able to clean it up and / or make a usable copy with another machine.

Bluescreening on XP install can be due to flaky RAM also - have you run memtest86 ?

---

### Post by ski309 on 2007-12-01
> **Craigus said:**
> The question is - why did this happen ?

Is the CD badly scratched or dirty ? If so, you might be able to clean it up and / or make a usable copy with another machine.

Bluescreening on XP install can be due to flaky RAM also - have you run memtest86 ?
There's nothing wrong with the CD, I can read it fine, and it ran perfectly for my VirtualBox installation.

I'm trying to make a Slipstreamed XP install CD, perhaps a more recent driver will help, but I'm having trouble finding something on Linux that will create a bootable CD.

I'll run memtest86 later.

---

### Post by Craigus on 2007-12-01
What is the actual error message that displays when you see the BSoD ?

---

