---
title: "Unable To Write To Partition"
date: 2007-04-14
forum: General Help
---

### Post by Miniberger on 2007-04-14
I store my data on a fat32 partition (shared with XP). Normally, it works fine. But today, when I booted, all of the directories in the entire partition act as read-only, give errors if I try to copy or delete, applications give errors because they can't write to the partition etc...

I own all of the directories and have create/delete permissions (other users have access only). I am, of, course, running under my user as always.

Could this be a corrupt partition? I can't see how this is a permissions problem.

Does anyone have any ideas?

---

### Post by x1a4 on 2007-04-14
Hi,

I've had this problem when xp crashed and after rebooting I went straight to Xubuntu.  Try booting to windows, shut down normally, then boot to Ubnuntu.  Doing this always solved it for me.

---

### Post by rmemm on 2007-04-14
You might want to run scandisk on it from the Windows system just to check for any repairs needed.  I think I have seen some linux distros mount things ro when there's some question about integrety.  Don't know if this is the case here.

Also -- I think FAT permissions are controlled at mount time -- I can't quite remember for certain.  You might want to read through your fstab and see what it says for this partition.

You could also try manually un-mounting and then re-remounting with the appropraite options just to see.  I'd also check the log files in /var/log to see what the kernel or standard message logger says.  If there was a mount problem during boot -- it should show in one of the logs.

Rob

---

### Post by Miniberger on 2007-04-14
Alright, so I went into Windows which automatically wanted to check the fat32 for some reason, so I let it. It found a corrupt movie file I'd been having some trouble with, which I deleted.

Then I rebooted Ubuntu and it's working fine. I'm still not sure why this happened in the first place though.

---

