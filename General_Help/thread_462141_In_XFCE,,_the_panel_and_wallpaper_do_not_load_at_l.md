---
title: "In XFCE,, the panel and wallpaper do not load at login"
date: 2007-06-02
forum: General Help
---

### Post by wersdaluv on 2007-06-02
After I logged in XFCE, the panel and the wallpaper (and maybe some other apps) did not start.

I already done this
```
mv ~/.config ~/.config.old
mv ~/.xfce ~/.xfce.old
```
expecting that it will make my XFCE back to normal but it did not.

Also, I found out that the .xfce folder does not exist.

What do I do?

---

### Post by x1a4 on 2007-06-02
Hi,

Try this: 

Login and run (use Alt+F2) **xfce4-panel**

Run the Settings manager: **xfce-setting-show**
Click desktop, and tick 'Allow Xfce to manage the desktop' and click 'Close' then 'Close' again

Logout.  When logging out tick 'Save session for future logins'. 

Log back in.

---

### Post by wersdaluv on 2007-06-02
Thanks! 

It worked!

---

