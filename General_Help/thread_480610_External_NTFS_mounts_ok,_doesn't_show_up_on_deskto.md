---
title: "External NTFS mounts ok, doesn't show up on desktop or &quot;computer&quot;"
date: 2007-06-21
forum: General Help
---

### Post by dansued on 2007-06-21
My external NTFS drive had been working fine. I had added it to /etc/fstab and it would mount and I could read/write to it. However after today when I put my computer on standby and then came back, the drive doesn't show up on the desktop or in the "Computer" section in Nautilus. It still shows up in /media where I mounted it.

Please help, Thanks!

---

### Post by AlexThomson_NZ on 2007-06-21
Did it appear on the desktop before going on standby?

If not and is perminantely mounted, just right-click on the desktop and select "Create launcher" and go from there (post back if you want more instruction for this).

Also, might want to check gconf-editor, and go into apps->nautilus->desktop and make sure "volumes visible" is checked.

HTH

---

### Post by dansued on 2007-06-21
yes, it appeared on the desktop before and in gconf, volumes visible is already checked.

I think the problem is more than just a missing icon on the desktop because it also doesn't appear in the Places menu or sidebar.

EDIT: I removed the drive from /etc/fstab, umounted it, unplugged the drive and plugged it back in, and it works now. Pretty strange what's going on. I have both ntfs-config and ntfs-3g installed. Is this creating conflicts?

---

### Post by AlexThomson_NZ on 2007-06-21
> **dansued said:**
> I think the problem is more than just a missing icon on the desktop because it also doesn't appear in the Places menu or sidebar.
Ahh that's what you meant when you said it wasn't in "My Computer"

> **dansued said:**
> EDIT: I removed the drive from /etc/fstab, umounted it, unplugged the drive and plugged it back in, and it works now. Pretty strange what's going on. I have both ntfs-config and ntfs-3g installed. Is this creating conflicts?
Does the same thing happen when suspend is resumed?  Might pay to see if this bug has been logged already

---

