---
title: "System hangs before login screen appears"
date: 2007-05-28
forum: General Help
---

### Post by eparion on 2007-05-28
A few minutes ago, I changed my login screen and then logged out to switch over to KDE - and all I got after Gnome logged out, was the "busy" cursor in front of a blank screen (I have used the same login theme in the past, with no problems). After restarting, I get the same thing - blank screen with "busy" cursor, without seeing the login interface.

Is there any way to fix this?

FYI, I am using Ubuntu Feisty.

---

### Post by Crafty Kisses on 2007-05-28
Possibly a driver issue, did you install any graphics drivers through Automatix?

---

### Post by eparion on 2007-05-28
Negative, the only setting I changed was to enable "accessibility", and I switched to a different login screen.

---

### Post by strabes on 2007-05-28
sudo dpkg-reconfigure gdm

---

### Post by eparion on 2007-05-29
Tried it, (booted into recovery mode, then entered Gnome in single-user mode) but I got this:

```
root@Hyperion:~# dpkg-reconfigure gdm
  *  Reloading GNOME Display Manager Configuration...
  *  Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.
```

---

### Post by YaroMan on 2007-05-29
I have same problem!! how can I fix it?

---

### Post by arnieboy on 2007-05-29
> **eparion said:**
> A few minutes ago, I changed my login screen and then logged out to switch over to KDE - and all I got after Gnome logged out, was the "busy" cursor in front of a blank screen (I have used the same login theme in the past, with no problems). After restarting, I get the same thing - blank screen with "busy" cursor, without seeing the login interface.

Is there any way to fix this?

FYI, I am using Ubuntu Feisty.
Do you remember upgrading your kernel from update-manager when you were logged in?

---

### Post by cosbear on 2007-05-31
Hey [B]eparion: 

I had what sounds like it may be the same problem.  I had to change a couple lines in the etc/gdm/gdm.conf file and was able to get back in on reboot.  Did you by any chance turn off automatic login just before this problem started?  If so, you might want to check this thread for my solution:

[http://ubuntuforums.org/showthread.php?t=459174](http://ubuntuforums.org/showthread.php?t=459174)

I'm not sure it will help, but I hope it does.  Good Luck,  cosbear
[/B]

---

