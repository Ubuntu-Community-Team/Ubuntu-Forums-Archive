---
title: "Dual Boot Ubuntu and Foresight Linux?"
date: 2008-05-22
forum: General Help
---

### Post by pjpeter on 2008-05-22
Hello Guys and Girls,

I am a newbie to Linux have only just converted from windows 2 weeks ago.

I've got Ubuntu installed on one hard drive and I want to install Foresight (or any other flavor for that matter) on my second but when I've tried installing the latter I can no longer see or get into ubuntu in booting up.

Basically I want to know how I can get another linux distro to show up in existing grub?

Thanks

---

### Post by shifty_powers on 2008-05-22
all it is, is that the second flavour of linux is being naughty and overwriting grub.

just do a fourm search on reinstall grub ;)

---

### Post by Patb on 2008-05-22
See Catlett's "How to restore Grub from a live Ubuntu cd":

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Cheers, Pat

---

### Post by OMA2k on 2008-12-09
I had the same issue (installed Foresight AFTER Ubuntu, losing the ability to boot into Ubuntu), but the post you're pointing to talks about recovering Grub after a Windows install, not another Linux distro.

Fortunately I could fix it by editing /boot/grub/grub.conf (Foresight's GRUB config file) and adding the appropriate lines from /boot/grub/menu.lst (Ubuntu's GRUB config file). This second /boot/grub directory was really in a different filesystem/partition, which I mounted in a directory called /ubuntu so it was really /ubuntu/boot/grub/menu.lst

The Foresight Linux installer seems to be pretty poor. It doesn't include GPartEd (only allows creating and deleting partitions, but not resizing, so I had to use a Ubuntu LiveCD to resize the partitions before installing Foresight), and then, it replaces Ubuntu's GRUB with its own GRUB when installing, so you can't boot into Ubuntu anymore unless you tinker with the config files...

---

