---
title: "cannot resize partition"
date: 2022-02-28
forum: General Help
---

### Post by alias5 on 2022-02-28
I'm dual booting Windows 10 and Ubuntu.  I need more room for Ubuntu.  So, I tried using Gparted and Gnome Disks to resize the Windows partition.  Neither will resize the partition because they say (sorry not at home so can't get this word for word) something about hibernation or not shut down cleanly.  So, I rebooted to Windows and verified that fastboot was disabled.  Any ideas on what else can I try?  Is there a flag I need to change or hiberfil.sys that I can delete?  I already checked Control Panel Power options and powercfg /H off.

---

### Post by ActionParsnip on 2022-02-28
Resize the NTFS in Windows. You may want to run a full chkdsk in Windows first. You should also shutdown the system rather than "restart" and do a cold boot to the install media

---

### Post by dragonfly41 on 2022-02-28
Are you using Gparted in a LiveUSB "Try Ubuntu" since you cannot resize an active mounted partition.

---

### Post by alias5 on 2022-02-28
Okay.  I will try resizing from within windows.  I did run chkdsk.  It came back without errors.  I'll post back this evening (few hours for me).

---

### Post by alias5 on 2022-02-28
I first used Ubuntu, which is installed on the same drive.  Then, I rebooted to Tails.  I ran into problems both ways.  I will post back this evening after giving @ActionParsnip's suggestion a try.

---

### Post by alias5 on 2022-02-28
> **ActionParsnip said:**
> Resize the NTFS in Windows. You may want to run a full chkdsk in Windows first. You should also shutdown the system rather than "restart" and do a cold boot to the install media

I was able to resize with Windows.  Unfortunately, I can't move partitions in Windows.  I hope when I reboot, Gparted or Gnome Disks will be able to handle that.

Thanks.

---

### Post by MAFoElffen on 2022-02-28
"Move" partitions? You can shrink or grow Windows partitions from within Windows Storage Management. If you tried to do that with GParted... Well, some file are "fixed: where they were written in Windows. Only Windows can move them to keep track of where they are. Other problems are that if Windows isn't the one that shrunk it, the indexes are toast and will have to rebuilt.

You can shift left or right with GParted... You can not skip over a partition, to move it to another part of the disk, in a move... I have not been able to do that without a lot of magic.

---

### Post by alias5 on 2022-03-01
> **MAFoElffen said:**
> "Move" partitions? You can shrink or grow Windows partitions from within Windows Storage Management. If you tried to do that with GParted... Well, some file are "fixed: where they were written in Windows. Only Windows can move them to keep track of where they are. Other problems are that if Windows isn't the one that shrunk it, the indexes are toast and will have to rebuilt.

You can shift left or right with GParted... You can not skip over a partition, to move it to another part of the disk, in a move... I have not been able to do that without a lot of magic.

Right, like the second option in the menu [in this screenshot]("https://gparted.org/screens/gparted_7_big.png").  I wasn't trying to skip over a partition, just move a couple to the left to fill the void left by shrinking the Windows partition.  I've repartitioned a million times.  I've just never had Windows make a partition immovable in Linux.  I think this might have been the first time I tried on Windows 10. I had been having trouble applying a Windows update, too.  So, I thought that might have been blocking me.  

So, maybe this is the new way to do what I needed to do.  Anyway, thanks, it's done now.

---

