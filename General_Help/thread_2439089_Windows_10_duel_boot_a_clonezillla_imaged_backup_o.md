---
title: "Windows 10 duel boot a clonezillla imaged backup of Kubuntu?"
date: 2020-03-22
forum: General Help
---

### Post by kgoerbig-gmail on 2020-03-22
I currently have Kubuntu 19.10 running on my machine. I want to duel boot Windows 10, but I do not want to go through the hassle of reinstalling Kubuntu from scratch. If I do a clean install of Windows 10, re-partition, and restore my Kubuntu image (clonezilla) onto that new partition, is it then possible to configure to duelboot after that? Or is only doing a clean install of both the only option?

---

### Post by freebird54 on 2020-03-23
I am not an expert on this situation, but I do know that I wouldn't attempt to answer without more information. Such as - is the machine you wish to do this on UEFI capable? Was the Kubuntu install you cloned done in UEFI mode?

The first thought I have is that given a yes on these questions, it SHOULD be possible, but am not convinced that the effort would be less than the re-install you mention :) It could be, though. Some research on booting alternatives **might** be required though - for instance I would use *rEFInd* to boot with - and the research involved might take more time than the 1/2 hour to re-install - as might the playing with partition sizes that could arise no matter how you intend to boot...

Just thoughts for the moment, but let us know what you're actually working with - including available drives and partitions  and their sizes -  and what your ultimate aim will be.

Freebird54

---

### Post by dragonfly41 on 2020-03-23
+1 to try rEFInd .. and also take time studying the options in /boot/efi/EFI/refind/refind.conf after installation of rEFInd.
You can define custom menuentry snippets.
Examples are given and snippets with "disabled" set are just ignored.
You can also customise the menu theme if you wish.

---

### Post by HermanAB on 2020-03-23
The reality of the matter is that while anything is possible with Linux, it is probably less hassle and much less time consuming to re-install it the normal way.

If it was me, it would probably take me a week to research how to do it, vs 20 minutes to re-install.  The week of research won't be wasted though - one would learn a lot.

---

### Post by yancek on 2020-03-23
You can install windows 10 on a computer which currently has another OS such as Kubuntu and there is no need to create an image of Kubuntu with clonezilla or other software.  You would need to create unallocated space on your drive on which to install windows and use the 'Custom' install option with windows to create a partition or partitions on which to install windows.  Is Kubuntu UEFI or Legacy as both systems need to be the same or booting will be problematic.  If you are familiar with the installation procedure of windows, it should not be much of a problem.  If you have an older Legacy/MBR system, windows of course will overwrite the boot code in the MBR without asking if you want this and without informing you that it will be done so you will need your Kubuntu install media to repair Grub.

So basically, it's possible but without more detailed information you will only get general answers.

---

### Post by oldfred on 2020-03-23
I always promote the new clean install. And that often is quicker.
But it requires you to have good backups which you should have anyway.

If you have good backups, you can restore /home, list of installed apps & perhaps some settings in /etc. Unless running server apps that would also be in / (root) that is about all you need. You can install Ubuntu in 10 to 15 minutes unless to flash drive which can be a lot longer. And reinstalling apps depends on Internet speed but also can be very quick. Only if you have huge amounts of data may it take a bit to copy that back, but then that data should perhaps be better organized into separate partition.

---

