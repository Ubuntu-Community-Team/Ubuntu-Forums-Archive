---
title: "Switch from recovery to regular mode"
date: 2019-01-18
forum: General Help
---

### Post by spookybathtub on 2019-01-18
When I have booted into recovery mode to fix a problem, is there some way to switch to regular mode without rebooting the whole computer?  It would just be nice to save time.  systemctl list-jobs shows that friendly-recovery is currently running.  If I try to stop it, it won't let me because this transaction is destructive.

---

### Post by TheFu on 2019-01-18
You mean like the old runlevels used to handle before systemd?
[https://askubuntu.com/questions/788323/how-do-i-change-the-runlevel-on-systemd](https://askubuntu.com/questions/788323/how-do-i-change-the-runlevel-on-systemd) has a table.

But depending on how recovery mode was entered, this might in inadvisable.  I generally use recovery mode from a live-boot using alternate media, so the running kernel is often 6-18 months old and missing many security updates.

---

### Post by spookybathtub on 2019-01-18
I think I figured it out. You just type exit then escape out to the menu and resume boot. I was fixing something in fstab so I think this should be safe without a reboot.

---

### Post by TheFu on 2019-01-19
exit and <cntl-d> will close any shell, assuming default keyboard mappings.

Please mark the thread as "solved" using the thread tools button near the top. This helps the community.

---

