---
title: "moved the .vdi file, now Virtualbox won't run"
date: 2007-10-27
forum: General Help
---

### Post by reswob on 2007-10-27
Hi, I haven't found the answer to this question yet. I left this post on the Virtualbox forums, but I haven't gotten an answer yet so I thought I'd try here.  Virtualbox was running fine, but during the upgrade to Ubuntu 7.10, the location where I had the vdi file stopped working. When I tried to run virtualbox, I got the error below:

"Invalid image file path '/media/New Volume/VirtualBox/XPPro.vdi' (VERR_ACCESS_DENIED)."

That location in fstab was: "/dev/sdb4 /media/New\\ Volume\" (without the quotes, and with the proper variables after) and wasn't being mapped. So I changed the location in fstab to "/dev/sdb4 /media/Disk1". The drive now maps fine and shows up on my desktop still named "New Volume" and, after logging out and back in, I have read/write privileges.

However, when I try and run Virtualbox, I once again get

"Invalid image file path '/media/New Volume/VirtualBox/XPPro.vdi' (VERR_ACCESS_DENIED)."

Any suggestions? Thanks.

Craig

---

### Post by mdurham on 2007-10-27
You can change the 'Hard Disks' setting to the new .vdi address, there is a 'browse' button for this purpose.
Hope that helps, Mike

---

### Post by reswob on 2007-10-27
problem is that error message is the first thing I see after I click the icon.  No change to change the hard disk setting.

---

### Post by mdurham on 2007-10-28
> **reswob said:**
> problem is that error message is the first thing I see after I click the icon.  No change to change the hard disk setting.

which icon?

---

### Post by reswob on 2007-10-28
The icon to run VirtualBox.  I go to Applications -> System Tools -> innotek VirtualBox and immediately get that error box.

---

