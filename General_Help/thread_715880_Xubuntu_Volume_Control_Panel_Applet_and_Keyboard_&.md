---
title: "Xubuntu Volume Control Panel Applet and Keyboard &quot;Super&quot; Key Problem"
date: 2008-03-05
forum: General Help
---

### Post by KenBW2 on 2008-03-05
Hi

I have two minor problems with my (eee)Xubuntu install.

My first and most annoying is that I can no longer add the Volume Control applet to the Panel. I had this problem previously and simply reinstalled xfce4-mixer and it worked again. But a few days later my computer crashed (unrelated) and I did a hard restart. At startup it complained about file system corruption or some such, and had to delete and fix a few files.Since then when I go to Add new Item > Volume Control it just shows a black line for a moment and then nothing... 

My other problem is with my Super (and I suspect my alt key). I had a play around with my Screens and Graphics settings while trying to get an external monitor working, and failed miserably. This resulted in my main screen being the wrong resolution and I went through [FONT="Courier New"]sudo dpkg-reconfigure xserver-xorg[/FONT] - which didn't fix the problem. Anyway, the problem has since been fied but I'm left with a keyboard that doesn't detect the Super key when in UK layout. When I have it in US layout it works (but then I have the obvious problem of the wrong keys). Also, alt+Back in Firefox no longer works, but Ctrl+Alt+Up for Desktop Cube does still work. I have attached my xorg.conf file for reference.

Any help much appreciated :)

---

