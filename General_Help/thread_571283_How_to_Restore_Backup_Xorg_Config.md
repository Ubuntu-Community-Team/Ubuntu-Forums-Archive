---
title: "How to Restore Backup Xorg Config?"
date: 2007-10-09
forum: General Help
---

### Post by lucid on 2007-10-09
Hi, 

I have a new widescreen monitor. I looked around the forums for a way to change resolution and ran the xorg config module. Unfortunately there were a number of questions to get through which I know little about before I could get to the part where I select the new resolution 1440 x 900. 

Now my screen is discoloured with artifacts whenever I boot Ubuntu (I duel boot, am on win side now). I backed up my xorg config file before trying this. Can I restore the backup file before logging into Ubunutu? I'm leery of breaking my new monitor!

---

### Post by rahimveron on 2007-10-09
If you able to boot in GUI, press ```
ctrl+alt+f1
``` , this will give you a black terminal prompt.
Login with your user and password.
If you had backed up your xorg.conf file, as you have done :), you can surely restore it. You need root privilege for it(Sudo)
Just use this command in Terminal```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
Explanation.
I have assumed that you have backed up the xorg.conf file in /etc/X11/ directory with the name xorg.conf.backup. Change it accordingly.
If not, navigate to directory where you saved your xorg.conf file then enter this command in the Terminal```
sudo cp xorg.conf.backup /etc/X11/xorg.conf
```

this will restore your xorg.conf.backup file in /etc/X11/ directory.

---

### Post by lucid on 2007-10-09
Thanks, that restored me to square one. :)

Now to find a way to change my resolution without breaking my monitor. With Gutsy around the corner might be best just to go back to windows and see if the next Ubuntu flavour will have a better fix.

---

### Post by rahimveron on 2007-10-09
I am sure someone will help you on this forum. Its not hard, just need some patience. I dont have a widescreen, so i wont be able to help you on that resolution problem. But believe me, someone in UF will surely answer your question:)
Dont give up so soon. Once configured you will love The Brown Freind.

---

