---
title: "No volume groups found after recovery"
date: 2016-01-25
forum: General Help
---

### Post by broken.stairs on 2016-01-25
I installed Ubuntu on a desktop and had the drive encrypted because why not?  Well, the machine isn't the fastest and I wanted to see if I could speed it up by removing the encryption.  So I followed the steps provided at [http://askubuntu.com/questions/245112/can-i-disable-full-disk-encryption](http://askubuntu.com/questions/245112/can-i-disable-full-disk-encryption).

The drive had 3 partitions on it and I can't remember but I believe I installed Ubuntu with LVM.  I backed up the biggest partition, thinking this is the main data partition, using dd to an external HD.  After following the steps and dd-ing the partition back into place without encryption, I cannot boot the machine.  At the moment I am getting the "No volume groups found" error and I cannot see that partition using fdisk; although I can see it with blkid.

What is causing this and can I fix it?  Does LVM have something do with this and can I fix it using LVM?  If not, can I reinstall Ubuntu without LVM to get it to see that partition?  In the worst case scenario, is there a way that I can install Linux based off of my backup sort of like how Apple and Windows can install based off of a Time Machine backup or system restore?

I love Ubuntu and am in the midst of a total conversion (I would even switch my MacBook Pro over if it wasn't for the Adobe overlords) but I think there needs to be more attention paid to disk recovery and installing OS alongside data.  For example, there are plenty of back-up tutorials online but restoring is neglected and still a hassle.  This would help noobs like me who were once able to reinstall Mac OS X and restore the data from a Time Machine, fixing all the driver issues he was experiencing.

I can provide more details if you ask.  Thanks for any and all help.

---

