---
title: "Samba share disk size"
date: 2005-08-05
forum: General Help
---

### Post by waffles on 2005-08-05
I'm a rather inexperienced user and I'm hoping someone can help me out. After successfully struggling to get Samba running and properly configured (I think), I found that my 160GB drive seemed to have shrunk to about 15GB. If someone could clarify the matter so I can learn whether I've done something wrong, or if perhaps what I'm trying to do is not possible, I'd appreciate it.

What I'd like to do load up all my files to the 160GB SATA drive on my Ubuntu box which I would serve using Samba and then mount it as a network drive on my windows laptop. The root of the Ubuntu system is on an old 20GB IDE drive and the 160GB is hooked through a PCI sata card. Following instructions I googled, I mounted the 160 into /mnt/sda1 and was able to share this, then map the share as a drive in windows. That's when I saw that windows measured a capacity of only 15GB remaining, which dismayed me given the 160GB I expected to see and which I could see in Ubuntu when I mounted the drive via fstab.

Now, it's clear to me that the apparent 15GB size of the drive comes from the fact that this happens to be the amount of remaining space on the IDE drive. I can see how this makes sense since it is mounted at /mnt on that 20GB drive, but I suspect that it isn't possible that this limit should be real. I mean, I have a 160 GB drive onto which I am loading my files, right? Is the apparent 15GB size just an appearance that won't actually limit my capacity? Is the 15GB limit real, but there's some way for me to get around it that I'm just unaware of? Did I do something incorrectly? Any help would be most appreciated.

---

### Post by sooqing on 2005-08-05
i suppose its most likely u configured samba to share ur primary hdd..

---

### Post by waffles on 2005-08-05
iirc, my samba share path = /mnt/sda1 because that is where the 160GB SATA drive was mounted when I followed those instructions. Would what I want to achieve be acomplished by setting the samba share "path = /dev/sda1" instead?

---

