---
title: "Regaining Windows Partition."
date: 2019-05-03
forum: General Help
---

### Post by dchurch24 on 2019-05-03
Hi all,

I have a 1TB drive in my old laptop. I have Windows10 installed (as I figured I would need it for my Helix (Windows software only)) and Ubuntu Studio. I split the drive 50/50.

It turns out that installing Win10 in a VM is enough to be able to use the Line6 software - it's a little unstable, but perfectly usable for my needs.
As such, and with recording a lot more these days, I'm running out of space on my Linux partition(s) and I'd like to reclaim the Windows 10 partition.

I've tried using gParted, but whilst the option is there to resize the partitions, it won't actually let me do it, regardless of it the other partition is mounted or not.

Could someone please point me in the right direction? I could really do without reinstalling from scratch as I've set up the machine perfectly for recording and that takes quite some time :p

---

### Post by HermanAB on 2019-05-03
Note that resizing partitions is risky.  You can only do that if everything is unmounted, meaning that you must be booted off different media, such as an install disk.  The more you mess with your disk partitions, the greater the risk that you will lose all your data.

A less risky option is to leave the Windows partition alone and simply mount it on a point in /mnt, make sure the entry is in /etc/fstab and then clean and use that partition for your data. Alternatively, you could reformat the Windows partition with gparted to ext4 and then mount it.

---

### Post by dchurch24 on 2019-05-03
Fair enough. Thank you. I think I'll go with a complete re-install to be honest. I can back up the whole image to my NAS drive to retrieve things I might need. It's probably time in any case :p

---

