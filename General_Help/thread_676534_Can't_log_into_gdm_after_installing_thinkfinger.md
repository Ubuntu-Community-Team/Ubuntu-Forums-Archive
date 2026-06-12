---
title: "Can't log into gdm after installing thinkfinger"
date: 2008-01-23
forum: General Help
---

### Post by Jamezracer on 2008-01-23
I recently installed thinkfinger 0.3 via a wiki (it worked fine with the tf-tool test) and now I can not log in with either my fingerprint or password, it just get a message saying "not authenticated, login failed." I also tried booting in recovery mode to the command line, still says "login failed" before even asking for my password, leading me to believe that my user account might have been destroyed somehow. I also tried dpkg-reconfigure gdm but I get an error message before it even starts. This is with ubuntu 7.10 on a dell m1330 which has been stable untill now. any help is appreciated!

---

### Post by mssever on 2008-01-24
> **Jamezracer said:**
> I recently installed thinkfinger 0.3 via a wiki (it worked fine with the tf-tool test) and now I can not log in with either my fingerprint or password, it just get a message saying "not authenticated, login failed." I also tried booting in recovery mode to the command line, still says "login failed" before even asking for my password, leading me to believe that my user account might have been destroyed somehow. I also tried dpkg-reconfigure gdm but I get an error message before it even starts. This is with ubuntu 7.10 on a dell m1330 which has been stable untill now. any help is appreciated!
If you can't login in recovery mode, then GDM has nothing to do with your problem since recovery mode doesn't run X and therefore GDM can't run at all. The first thing would be to verify that /etc/passwd and /etc/shadow aren't corrupt. Failing that, you'll probably need to find out what files thinkfinger touches (either by examining the source code or by asking at some appropriate place) and make sure those files are OK.

---

### Post by Jamezracer on 2008-01-24
Thanks for the help! neither of the files seem to be corrupted, and i think it might be faster just to re-install ubuntu than attempt to restore it at this point. who knows what other damage I might have done even if I was able to fix it. I'll hold off till tomorrow night to wipe the drive. has anyone else out there had a similar problem? I haven't read it on the forums yet. thanks again!

---

### Post by p_quarles on 2008-01-24
One thing that stands out here: Recovery Mode doesn't ask for a password. Are you sure you weren't using the "Failsafe Terminal" option from the GDM login manager?

To get to the real Recovery Mode, you need to select that option from the boot menu. If you don't normally see a boot menu, you can access it by pressing the escape key just after the BIOS passes to the OS.

---

### Post by Jamezracer on 2008-01-24
> **p_quarles said:**
> One thing that stands out here: Recovery Mode doesn't ask for a password. Are you sure you weren't using the "Failsafe Terminal" option from the GDM login manager?

To get to the real Recovery Mode, you need to select that option from the boot menu. If you don't normally see a boot menu, you can access it by pressing the escape key just after the BIOS passes to the OS.

yes, I'm using the recovery mode that you get to in grub. oh well, I'm going to do a fresh install. thanks for the help guys!

---

