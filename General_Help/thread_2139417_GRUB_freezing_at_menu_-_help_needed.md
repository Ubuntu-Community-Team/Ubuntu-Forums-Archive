---
title: "GRUB freezing at menu - help needed"
date: 2013-04-26
forum: General Help
---

### Post by ukjb on 2013-04-26
Hello,

I mistakenly switched off my computer at the GRUB menu, and now the computer always freezes at that point. I'm using an Intel Mac, which boots into rEFIt- that process works fine to boot into the linux partition, but once I get to the full GRUB menu, the keyboard becomes unresponsive, and booting does not proceed. I'm running Lubuntu 12.04. 

Could something help me with what process I need to go through to diagnose what the problem is, and see whether there's a solution? I have LiveCDs for 13.04 and 12.04 available.

Thankyou in advance.

---

### Post by Hugh Mulqueen on 2013-04-26
Get out your Live CD and chroot into your hard-drive and reinstall grub using these commands:

1. fdisk -l

2. sudo mount /dev/sda

3. mkdir /mnt

4. chroot /dev/sda1 /mnt

5. sudo grub install /dev/sda1

---

