---
title: "xubuntu 12.10 gparted and thunar problem"
date: 2013-01-21
forum: General Help
---

### Post by ubume2 on 2013-01-21
I currently have Xubuntu 12.10 x86 installed.  I am having problems
with gparted. On a boot into Xubuntu and opening gparted (through the menu or through command line), it opens up a thunar for each partition( NTFS,FAT,Linux) on the HD. 
Also in gparted it shows them as mounted.

I also have Xubuntu 12.04.1 installed on a separate partition, and it
acts normally.


Help would be appreciated in stoppping this annoying behavior.

---

### Post by The Cog on 2013-01-21
The problem is that gparted briefly tries to mount every drive in order to measure percentage used. Thunar is detecting this and preventing gparted from un-mounting them again.

In Thunar, menu Edit / Preferences / Advanced, and click the blue link to configure volume management. Un-check the top item "Mount removable drives when hot-plugged".

---

### Post by ubume2 on 2013-01-21
@TheCogg

That took care of it.  Thanks :)

---

