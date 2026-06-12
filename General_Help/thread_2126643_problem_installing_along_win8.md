---
title: "problem installing along win8"
date: 2013-03-17
forum: General Help
---

### Post by rich81 on 2013-03-17
I know i have well over 100gb of space , but disk management will not let me shrink the c drive partition to create a partition for the ubuntu installtion, microsoft tech support would gladly help for 100$,just wondering if anyone here can help instead.

---

### Post by GameX2 on 2013-03-17
You can't shrink the Windows partition inside Windows, because it's currently in use.

I would suggest booting with a LiveCD of a partition editor.  GParted, maybe - someone might confirm this.

---

### Post by oldfred on 2013-03-17
Windows Disk Cleanup tool to houseclean
defrag at least twice
#Partitioning generally better
Windows Vista - partition your hard drive using Disk Management, if XP use Gparted
25GB at an absolute minimum 
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

Older on Vista, but many of the same issues.
Some of the Windows third party tools may work. Gparted also may work but a few have had issues. 
After any NTFS partition size change it needs to reboot and run chkdsk and make other fixes.

Do you also have the 4 primary partition limit issue?

---

