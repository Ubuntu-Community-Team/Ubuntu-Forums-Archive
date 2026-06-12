---
title: "Compressing a btrfs partition."
date: 2014-01-11
forum: General Help
---

### Post by cdysthe on 2014-01-11
Hi,

One one of my laptops I installed Ubuntu 13.10 on two btrfs partitions / and /home (in addition to swap). I boot from / and everything works just fine. I would like to try out compression on the /home partition  The entry added by the Ubuntu installer in /etc/fstab looked like this:

UUID=9628e01f-3da0-46b1-8386-8b8161b3bda9 /home     btrfs   defaults,subvol=@home    0     2

I enabled compression, or at least I think I did by changing it to:

UUID=9628e01f-3da0-46b1-8386-8b8161b3bda9 /home           btrfs   defaults,compress=lzo,subvol=@home   0   2

To compress existing files I have tried to do 'sudo btrfs filesystem defragment -f -v -clzo /home' but not much happens. The disk spins for a second or so and then I'm back to the prompt. Not much seems to have happened and nothing seems to have been compressed

My questions are: Have I enabled compression correctly? If so, why am I not getting the existing files compressed? Is the command I use wrong?

---

### Post by cdysthe on 2014-01-12
I am going to answer myself. After a lot of Googling around I finally found that the command to run is:

sudo find /home -xdev -type f -exec btrfs filesystem defragment -v -clzo -- {} +

This command defragments my home parition and compresses existing files. Obviously my compression statement in fstab is working.

---

### Post by clickwir2 on 2014-01-14
I believe running a balance would also accomplish mostly the same thing. btrfs fi balance /mountpoint

---

