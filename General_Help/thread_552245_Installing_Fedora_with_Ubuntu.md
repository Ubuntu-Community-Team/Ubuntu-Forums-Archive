---
title: "Installing Fedora with Ubuntu"
date: 2007-09-16
forum: General Help
---

### Post by gamingx2005 on 2007-09-16
Hello guys,
          I have Windows XP installed and also I have Ubuntu Feisty Fawn installed, but now my brother wants to install Fedora 7. How do I go about doing it. Can someone help or am I posting in the wrong section?

---

### Post by CptPicard on 2007-09-16
Provided you've got the disk space, you can install it on the side of the rest, grub can boot them all, and Fedora's installation probably is able to configure the triple-boot.

If you don't have the space, you have to resize partitions, which can tough at times...

An interesting solution in this kind of a situation is, btw, to keep /home on its own partition and just install the OS-specific bits on their own partitions. Then you just mount /home to each distribution from the *same* partition, that way you can access your data from both (you may want to copy over /etc/passwd though and edit /etc/group so they match).

On the other hand, I would never bother running two separate distros on the same box... they are so much the same anyway. :)

---

### Post by gamingx2005 on 2007-09-16
Even, I wouldn't want to install another distro, but my elder brother is adamant that I install Fedora even If I have to remove Ubuntu.....So, I am in a mess, now I have to install Fedora but I wouldn't bother synchronising the passwords, settings etc since Fedora will be used only by my brother....

---

