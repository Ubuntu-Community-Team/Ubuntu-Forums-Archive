---
title: "Unstable Network Settings?"
date: 2007-11-19
forum: General Help
---

### Post by Akira Mishima on 2007-11-19
I was happy yesterday when I could successfully have one of my Windows XPs PC access Ubuntu through the LAN router on a PC where both Ubuntu and Windows XP are installed.

Basically, in this PC I have Ubuntu installed in dual-boot along side Windows XP on the same HD; the two OSs share the same NTFS file partition, called FILE, where my working file reside. After installing Samba I could successfully set permission for this FILE partition to be read/written by a different Windows PC in the LAN.

This morning however the other Windows PCs of the LAN were not able the access the FILE partition through Ubuntu. The when I looked into System -> Administration -> Shared Folders I couldn't find anymore the FILE folder that I had set yesterday for permission; in its place the /home/user folder was set for permission. Moreover, sometimes it happens that when I try to set permission for a folder in the FILE partition Ubuntu doesn't comply with the instruction, and simply select /home/user. Is this a sort of bug?

Is there a way, possibly through the Terminal, to have the network permission settings stay in place.

Many thanks in advance

---

