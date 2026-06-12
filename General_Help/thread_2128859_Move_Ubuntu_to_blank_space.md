---
title: "Move Ubuntu to blank space"
date: 2013-03-24
forum: General Help
---

### Post by chazdg24 on 2013-03-24
I have Ubuntu 12.10 installed on a second hard drive (sdb). I had a windows ntfs partition before that for storage but have subsequently purchased an external hard drive and transferred those files to it. I then deleted the ntfs partition leaving blank space before Ubuntu.
Question - is there a fast way to move 12.10 over without hosing my system? I really would prefer not to use Gparted as it is painfully slow. I want to do this so when 13.04 comes out, I can install it next to 12.10. I have never tried this so if you could be specific as possible with any advice. Thanks everyone.

---

### Post by Impavidus on 2013-03-24
Gparted is slow because it has to copy every bit on your ubuntu partition to a new location when you move the partition. This happens with every tool. But if you want to dual boot with 13.04, why not install 13.04 in the free part, instead of moving 12.10 there and then installing 13.04 where your 12.10 is now?

---

### Post by chazdg24 on 2013-03-24
> **Impavidus said:**
> Gparted is slow because it has to copy every bit on your ubuntu partition to a new location when you move the partition. This happens with every tool. But if you want to dual boot with 13.04, why not install 13.04 in the free part, instead of moving 12.10 there and then installing 13.04 where your 12.10 is now?
So that would work?  I know that I would need to update grub in 12.10 for 13.04 to show in Grub.

---

### Post by Impavidus on 2013-03-24
I'm not such a specialist in partitioning, but I don't think it really matters in which order the different Ubuntu root partitions are located on the disk. Grub has to be updated from the Ubuntu version that installed it in the MBR (in GPT partitioning things may be different, I've no idea), which is usually the last one installed.

---

