---
title: "Changed screen resolution / can't log in"
date: 2006-12-21
forum: General Help
---

### Post by zweiundzwei on 2006-12-21
So I updated dapper to edgy, screwed up in the middle, got help, finished installation and was stuck with 1024x768 instead of 1280x1024. 

I found a thread here that explained how to get the right resolution with editing the xorg.conf file and adding some lines to the screen & monitor section. 
So I did that and got to the right resolution once I restarted, but I can't log in anymore. Or rather, it just keeps sending me back to the log in screen (without password wrong message or anything) once I've entered username and password.

Searching the forum it seems like I'm not the only one who has that problem, but I couldn't find a step-by-step for idiots guide on how to get this working again anywhere. 

Could someone please help me? 
I'm definitely sick of using XP by now. ](*,)

---

### Post by jhenager on 2006-12-21
On the login screen, you will see a dropdown on the lower left that lets you Change Session. You can log into the terminal instead of the GUI. From there, you just rename your current xorg.conf file to xorg.conf.bad, and rename your old.xorg.conf to xorg.conf, and log out and back in.
...
...
...
What? You didn't save your xorg.conf file before editing it? Well, you are in trouble. Maybe you could get someone with the same video card to post theirs, back up your current one, and create a new xorg.conf with that. Good luck.

---

### Post by zweiundzwei on 2006-12-21
sweet, thanks, i couldn't find the terminal option.

it works again, i just need to figure out how to change the screen resolution without screwing up everything else in the process... :D

---

### Post by PWill on 2006-12-21
Try running ```
sudo dpkg-reconfigure xserver-xorg
```
It will automatically backup your xorg.conf file, and autodetect everything, too.

---

### Post by zweiundzwei on 2006-12-21
I did that and it changed some things, too, but the screen resolution won't change. It seems to have problems with detecting my video card.

---

