---
title: "Truecrypt, GRUB &amp; MBR"
date: 2012-10-20
forum: General Help
---

### Post by Morrigan69 on 2012-10-20
Previous, normal situation:
Encrypted partition with Windows 7 installed on it so when turning on my computer I first had to enter TC password and then would "Windows Boot Manager" showed up so I could boot into Windows or Ubuntu (if this choice then again would GRUB appear)

Today I installed standard updates on Ubuntu and changed user interface to Cinnamon (all at the same time so not sure what damaged it).

Now when turning on it doesn't ask me for TC password, there is no WBM, only GRUB shows up without Windows option to boot.

I couldn't find the exact problem and don't want to try experimenting by myown since I have really important files on that Windows partition which I don't want to lose, so I am really hoping that you guys will help me. Thanks!

---

### Post by Morrigan69 on 2012-10-20
Ok, here is the update:
- I tried fixing MBR from Win LiveCD but getting error No Operating system (I guess because of TC..)
- Now trying to get GRUB back from Ubuntu CD and getting this:
sudo grub-install --root-directory=/mnt /dev/sda3
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.


Please guys help, Im really impatient since I have work to do...

---

### Post by nothingspecial on 2012-10-20
OP found his TC cd.

Closed.

---

