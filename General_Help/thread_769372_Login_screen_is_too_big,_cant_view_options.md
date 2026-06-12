---
title: "Login screen is too big, cant view options"
date: 2008-04-26
forum: General Help
---

### Post by DMBoricua on 2008-04-26
I have upgraded to Ubuntu 8.04 hardy, and my login screen is bigger than it normally is. I had this kind of problem when I had previous versions of Ubuntu installed, but I could fix it by going to Screens and Graphics I think was the application I used to identify my monitor brand and resolution and such. The new version of Ubuntu doesnt seem to have this program, although the Screen Resolution panel supports widescreen resolutions, theres no way of identifying my monitor and model and such like I did with the previous version of Ubuntu.

When I get to the login screen, I see the screen zoomed at the top left corner of the screen, and I cant view the options button and the time that you would normally see on the bottom of the login screen. Does anyone know how to fix this?

---

### Post by JimmyHopkins on 2008-04-26
Have you tried running System -> Preferences -> Screen Resolution?

---

### Post by DMBoricua on 2008-04-26
Yes, Screen Resolution has the correct resolution for my monitor which is 1680x1050. However, it seems that on the login screen, the resolution changes.

---

### Post by JimmyHopkins on 2008-04-26
Try the first reply to this thread ([http://ubuntuforums.org/archive/index.php/t-192515.html](http://ubuntuforums.org/archive/index.php/t-192515.html)) I dug up. Perhaps it will help?

confused57 said:
"sudo gedit /etc/X11/xorg.conf

Near the end of the file, you'll see the default display resolution settings for default 24. Make "1280 x 1024" the first resolution on this line.

I had the same problem & this worked for me."

---

