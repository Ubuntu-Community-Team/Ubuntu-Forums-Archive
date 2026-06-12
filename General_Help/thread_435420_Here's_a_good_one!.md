---
title: "Here's a good one!"
date: 2007-05-06
forum: General Help
---

### Post by dpar on 2007-05-06
OK, here's what I did. I have feisty installed on hdd1. I reformatted Hdd6, which was my experimental partition, in order to install Mint. I screwed up somewhere with the mint install as far as grub is concerned and it didn't install grub to the Mint partition, which is what I wanted. Mint install exited. Now when I try to start Feisty, I get.....


fsck.ext3:unable to resolve 'uuid=586900e4-2343-4827-a51a-88baf261c872'
fsck died with exit status 8

if I then type reboot, it will load Feisty.


HELP!!!!! My wife is going to kill me!!!

How can I get Feisty to boot normally????:(

---

### Post by phidia on 2007-05-06
The partition with the uuid you posted isn't being recognized by ubuntu.
If you open /etc/fstab sudo gedit or whatever text editor you like, you can comment out (place a # symbol in front of that partition uuid)  Save, reboot and check to see if it worked

---

### Post by dpar on 2007-05-07
I managed to save myself......I logged on to the partition, copied all important files etc., then wiped the drive and reinstalled feisty. All is well for now.:oops:

---

