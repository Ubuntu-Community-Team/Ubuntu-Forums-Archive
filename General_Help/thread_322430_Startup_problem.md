---
title: "Startup problem"
date: 2006-12-20
forum: General Help
---

### Post by Kata on 2006-12-20
Hello,
when I was starting up my computer today, it just wouldn't start. After the login screen , the "box" which displays what components/applications/whatever have been initiated didn't get past the very first step (the window manager). (Hmm, I hope that was understandable, English isn't my native language.) 

I tried rebooting several times, with no result. I also tried choosing "recovery mode" where you choose which OS to boot, but that didn't work either. I finally managed to start it by choosing "failsafe gnome" in the session-menu in the login screen, but this doesn't feel like a good permanent solution. Does anyone know what might cause this, and how to solve it? I'm pretty much a Linux newbie...

I don't know if it has any relevance, but when I shut down the computer yesterday I checked the "save settings" checkbox in the shutdown dialog. I don't usually do that but have done it before without any problems. Otherwise, I can't think of any recently made changes. Oh yes, I installed Firefox 2.0 about a week ago or so.

I am using the release "breezy badger"/v.5.10.

Thankful for any help.
/Kata

---

### Post by nsleiman on 2006-12-20
try to go to the console and remove all sessions related to your gnome. i think its hidden means starts with a ´.´ 
to see all files type ´ls -a´ 
after this try ´sudo shutdown -r now´

hope it will work

---

### Post by Kata on 2006-12-20
Ok, but where in the file system are the sessions stored? And what kind of names do they have?

---

### Post by hal10000 on 2006-12-20
I don't know where your gnome sessions are stored, but you may try to remove all your files in /tmp directory. Do this as normal user, not with sudo:
[COLOR="Red"]rm -r /tmp/*[/COLOR] .Say yes to all questions and don't hesitate if it refuses to do on some files (they are write protected and shall remain so).
Then reboot and log on again.
Hope it helps, good luck.

---

### Post by Kata on 2006-12-20
> **hal10000 said:**
> I don't know where your gnome sessions are stored, but you may try to remove all your files in /tmp directory. Do this as normal user, not with sudo:
[COLOR="Red"]rm -r /tmp/*[/COLOR] .Say yes to all questions and don't hesitate if it refuses to do on some files (they are write protected and shall remain so).
Then reboot and log on again.
Hope it helps, good luck.
It didn't work, still the same problem.
But when I was rebooting the computer, it wouldn't shut down. All desktop icons and the two menubars dissappeared, but then it froze and I had to reboot by pressing the reset button. I guess this is probably related to the startup problem.

---

### Post by marcantonio on 2006-12-20
Everything that Gnome starts is in ~/.gnome2/session.  You can try editing out certain things from a terminal (ctl+alt+f2) and then starting Gnome.  Please make sure you backup that file though.

Marc

---

