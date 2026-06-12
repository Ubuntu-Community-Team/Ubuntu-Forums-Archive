---
title: "Nautilus troubles deleting files from Wastebasket off SMBFS share"
date: 2004-11-25
forum: General Help
---

### Post by GiLL on 2004-11-25
Hi all!

Got Ubuntu installed and lovin' it, but got a small issue that haven't been able to work around.

I have some SMBFS shares mounted that I can read/write to, but when I delete stuff it goes to the Wastebasket. Problem is, I can not empty the trash! When I try to empty the Wastebasket, I get an error saying that it can not do it because the folder is busy.

I installed KDE from Synaptic and under KDE I do NOT have this problem. Also, from Windows XP I don't have this issue, so I know the user/pass are good and the FSTAB entry is good.


I would rather have it like Windows where if I delete something from a network share it gets blown away. None of this moving to the trash stuff. I looked through the gConf editer and didn't see anything to change this behavior.

The SMBFS box is a Windows 2003 standard server. I was running Linux on it a few days earlier sharing stuff out via Samba, and Gnome on my Ubuntu box experienced the exact same behaviour.


Thoughts?

---

