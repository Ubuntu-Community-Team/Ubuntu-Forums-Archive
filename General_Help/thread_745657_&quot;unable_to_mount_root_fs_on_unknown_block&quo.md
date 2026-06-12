---
title: "&quot;unable to mount root fs on unknown block&quot;"
date: 2008-04-04
forum: General Help
---

### Post by ruidc on 2008-04-04
I thought i would post this up here as it fixed my problem and it may help someone else...

thx to user: stdin from the #kubuntu IRC channel...

i'd tried changing my GRUB menu.lst root entry from a UUID to a /dev/hda1 ... and tried several other things suggested on the forums... this is what worked.

1. make sure you have a livecd (and with integrity tested) for your architecture (amd64 for me)

2. in a terminal window:
sudo mount /dev/hda1 /mnt

3. then in same window:
sudo -i

4. then in same window:
chroot /mnt

5. then in same window:
dpkg --configure -a
(if prompted, answering Y worked for me - also got a path not found warning...but continued)

6. then finally, in same window: 
update-initramfs -k 2.6.22-14-generic -u

(also got a path not found warning...but continued)

7. reboot - error went away!
good luck all, and remember if you have a problem and find a solution, share it so that everyone else can benefit.

---

