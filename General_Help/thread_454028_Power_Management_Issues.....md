---
title: "Power Management Issues...."
date: 2007-05-25
forum: General Help
---

### Post by rivinius on 2007-05-25
After spending quite a bit of time, I finally have my ubuntu system suspending and waking on lan cleanly, but now I'm stuck on 2 new problems:

1.  It will only timeout and suspend when logged into gnome... I would also like it to timeout/suspend from the login screen.  It seems like this would make sense seeing as no one is logged in at the time.

2.  I would like to have it monitor process activity when deciding to sleep... for example if another system is connected to a samba file share, I don't want the linux system to suspend.  Right now it will suspend in the middle of an active file transfer.  

I've been searching around like crazy trying to find anything relating to these 2 pieces of functionality with no luck.... any ideas?

Right now the best solution I can think of is to put together some sort of monitor that both prevents gnome from sleeping when certain processes (such as smbd) are active and also kicks off the /etc/acpi/sleep.sh script when no one is logged into gnome and nothing is active.

thanks!

---

