---
title: "Grsync error messages"
date: 2008-03-08
forum: General Help
---

### Post by malel on 2008-03-08
I have been trying to run Grsync from my main computer running Kubuntu 7.10 to an external HDD. It has been formatted as 'ext3; but I keep getting the following error messages.

rsync: opendir "/home/mal/.gnupg" failed: Permission denied (13)
rsync: send_files failed to open "/home/mal/.kde/share/config/adept_batchrc": Permission denied (13)
rsync: send_files failed to open "/home/mal/.kde/share/config/adept_managerrc": Permission denied (13)
rsync: send_files failed to open "/home/mal/.kde/share/config/adept_updaterrc": Permission denied (13)
rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]

When I was running Ubuntu 7.04 I did not have any of these problems. I ran 'QTparted' to fromat the ext HDD but it won't or can't do it. The ext HDD is 320Gb.

Can someone please make some sense out of these error messages for me.

Many thanks

---

### Post by wieman01 on 2008-03-10
This is a permission issue. Please try to run 'rsync' with 'sudo', e.g.:
> sudo rsync xxx

---

### Post by malel on 2008-03-10
Thank you Weiman01 . That did the trick ..

---

