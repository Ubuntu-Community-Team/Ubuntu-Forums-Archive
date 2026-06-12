---
title: "VMPlayer can't find GRUB boot list in Dual boot"
date: 2007-03-03
forum: General Help
---

### Post by jj9000 on 2007-03-03
Hi guys,

I have a dual boot setup with XP/Ubuntu. I followed this guide: [http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

to set up VMPlayer to run my XP install in windows. 

Problem is, I get to GRUB menu inside the VMWare window in Linux. After picking the windows partition, it stalls on "Starting up ..."

In this [http://ubuntuforums.org/showthread.php?t=345835&highlight=Dual+boot+VMplayer+Starting+up](http://ubuntuforums.org/showthread.php?t=345835&highlight=Dual+boot+VMplayer+Starting+up)
thread, post # 10
[http://ubuntuforums.org/showpost.php?p=2125367&postcount=10](http://ubuntuforums.org/showpost.php?p=2125367&postcount=10)

says that he had to make another vmdk file so GRUB could see its boot list (which was on another drive in his case). 

I just have one hard drive, so my GRUB stuff is presumably on my linux partition, on the same hd  as my windows.

What should I put in this new linux.vmdk boot file?

Thanks!

---

### Post by jj9000 on 2007-03-05
Anyone? Thanks in advance!

---

