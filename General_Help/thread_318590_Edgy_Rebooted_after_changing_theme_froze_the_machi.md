---
title: "Edgy: Rebooted after changing theme froze the machine. Now it freeze after login"
date: 2006-12-14
forum: General Help
---

### Post by nelius on 2006-12-14
Hi,

I upgraded from dapper to edgy and the transition went smoothly. While checking out the new version I decided to install gnome-art and change my theme. After downloading some themes and changing it to see how it looked, the machine froze while changing theme.

After a cold reboot I find myself not beeing able to get past that window after login where all those small icons show up to make the user know what's starting up. (Right before you can use the machine.. don't know the name for this phase and/or window).

I have automatic login, and I can restart X to get to the normal login-window, but it still freeze at the same place when I login.

Please tell if I should post some information about the enviroment, or the output of some files on the system. (I can boot into recovery mode, but don't know what I'm looking for)

It's an old machine. P2 800mhz, 512 mb ram and GF4.

Thanks!

---

### Post by nelius on 2006-12-14
Shameless bump

---

### Post by seku on 2006-12-16
I'm having the exact same problem, although i don't know if it's because of changing theme. 

Please someone who could know something.. Help!

---

### Post by rlx01 on 2006-12-16
Do you have a recent ATI card?  Are you using the radeon driver?  If so you will likely get lockups under certain circumstances (esp when using GL type graphics output).  Not sure what specifically is causing *your* problem, but could it be an app trying to start and produce GL output?  You could try logging in under another windowmanager.  Or if you can work put what program is causing it just rename that to something else after logging in on a console (CTRL-ALT-F1) before logging into X.

---

