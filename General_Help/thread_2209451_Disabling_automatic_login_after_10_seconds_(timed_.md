---
title: "Disabling automatic login after 10 seconds (timed login)"
date: 2014-03-05
forum: General Help
---

### Post by yagolf on 2014-03-05
Hi everyone!

This is a short tutorial on enabling/disabling 'timed login' in Ubuntu Gnome 13.04

In essence, the issue is that after disabling 'automatic login' on User Accounts, the default user would still  log in after 10 seconds of the login screen showing--known as 'timed login'--, which to me is a privacy issue as it allows anybody with access to the computer to log in as such default user.  For some weird reason the option to disable this is not present in the User Accounts GUI even though it'd just be adding a checkbox (it wouldn't alter the design or anything)...

One possible workaround would be to create another user with no sensitive data and make that the default, but this is not ideal, at least in my case, so I figured I'd share here the simplest solution I've found in case it helps anyone out there.

All we need to do is edit as superuser the file *custom.conf* that is located in */etc/gdm* with our text editor of choice. In my case, I used *nano* (a nifty terminal-based text editor):
```
sudo nano /etc/gdm/custom.conf
```
Find the line that says '*TimedLoginEnable=true*' and change it to '*TimedLoginEnable=False*', save the changes and reboot the machine, you should be good to go.

Hope this helps!

---

