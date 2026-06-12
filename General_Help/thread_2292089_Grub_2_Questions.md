---
title: "Grub 2 Questions"
date: 2015-08-25
forum: General Help
---

### Post by zuto2 on 2015-08-25
What is the difference between Grub-PC and Grub Commons?

How can I install grub2 from a .Deb offline? I Back up and restore grub2 quite often with a Ubuntu Precise Live CD. 

How would I do it offline?

[https://launchpad.net/ubuntu/+source/grub2/1.99-21ubuntu3.18](https://launchpad.net/ubuntu/+source/grub2/1.99-21ubuntu3.18)

My grub version is:

:~$ grub-install -v

grub-install (GRUB) 1.99-21ubuntu3.18

**Edit:**
Come to think of it....doesn't the Live CD already have Grub on it?

grub-install /dev/sdX

grub-install --recheck /dev/sdX

update-grub

I don't actually download grub when restoring?

---

### Post by sudodus on 2015-08-25
Welcome to the Ubuntu Forums :-)

That's right, you don't actually download grub when restoring. You use the version of grub-install in the running system (unless you chroot into another system, that also is avaiable).

Unless you have an old computer, that needs old drivers for the hardware, I would suggest that you start using the new version with long time support, Ubuntu 14.04 LTS (and the flavours Kubuntu, Lubuntu, ... Xubuntu). There is a newer and improved version of grub, which can also install a bootloader for UEFI mode.

For example 14.04.2 LTS comes with

```
$ grub-install --version
grub-install (GRUB) 2.02-beta2-9ubuntu1
```

---

### Post by zuto2 on 2015-08-25
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

That's right, you don't actually download grub when restoring. You use the version of grub-install in the running system (unless you chroot into another system, that also is avaiable).

Unless you have an old computer, that needs old drivers for the hardware, I would suggest that you start using the new version with long time support, Ubuntu 14.04 LTS (and the flavours Kubuntu, Lubuntu, ... Xubuntu). There is a newer and improved version of grub, which can also install a bootloader for UEFI mode.

For example 14.04.2 LTS comes with

```
$ grub-install --version
grub-install (GRUB) 2.02-beta2-9ubuntu1
```

I am happy with Ubuntu 12.04 Percise LTS. I tried Ubuntu 14, but it was so buggy on my hardware that I went to Elementary OS Luna and now back to Ubuntu Precise because it works best for me. All my Windows and Linux programs are functioning great.

Today, I can Finally leave Windows. :D

After I convert my external harddrive Encryption to one capable with Linux which will be easy. I will only be using windows for some Development testing.

---

