---
title: "NTFS defragment and misc questions"
date: 2008-06-08
forum: General Help
---

### Post by maninalift on 2008-06-08
I have an external USB hard-drive that is NTFS formatted and I'd like to defrag it. Is there a way to do this in Linux. I doubt it matters but I am running 64bit Kubuntu 8.04.

Before you lay in to me, yes, when it is convenient I will reformat it but for the moment it is the largest hard-drive I have (my only computer is a laptop) and I don't really feel like backing up to 100 DVDs ;).

Also, I've noticed that 8.04 now auto-mounts NTFS. Just out of interest I wondered whether this still based on FUSE or whether NTFS support has been integrated into the kernel (at least the ubuntu patched kernel) or something else.

---

### Post by hal8000 on 2008-06-08
> **maninalift said:**
> I have an external USB hard-drive that is NTFS formatted and I'd like to defrag it. Is there a way to do this in Linux. I doubt it matters but I am running 64bit Kubuntu 8.04.

Before you lay in to me, yes, when it is convenient I will reformat it but for the moment it is the largest hard-drive I have (my only computer is a laptop) and I don't really feel like backing up to 100 DVDs ;).

Also, I've noticed that 8.04 now auto-mounts NTFS. Just out of interest I wondered whether this still based on FUSE or whether NTFS support has been integrated into the kernel (at least the ubuntu patched kernel) or something else.



ntfsdefrag under linux was planned as part of the ntfsprogs package, but development did not start because of lack of interest and the amount of tools available for defrag under windows

[http://www.linux-ntfs.org/doku.php?id=ntfsdefrag](http://www.linux-ntfs.org/doku.php?id=ntfsdefrag)

If you open a terminal and type:
df -hT

you will see how your filesystems are mounted.
root@orac:/home/anc# df -hT
Filesystem    Type    Size  Used Avail Use% Mounted on
--snip--
/dev/sda1  fuseblk     59G   50G  8.8G  86% /media/winxp


As you can see NTFS mounts still use fuseblk, but kernel support is built as a module and not compiled into the Ubuntu kernel. 

lsmod | grep fuse
lsmod | grep ntfs

will list the modules in use for you, hope that helps.

---

### Post by maninalift on 2008-06-08
Thanks for your very clear and informative answer. 

No defrag. I'll just have to live with the knowledge that my auxiliary hard-drive is as mixed up as a 7-year-old's paint pallet. :(

---

