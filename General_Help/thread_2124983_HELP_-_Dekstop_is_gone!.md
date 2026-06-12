---
title: "HELP - Dekstop is gone!"
date: 2013-03-12
forum: General Help
---

### Post by Dzanjin on 2013-03-12
Hello everyone,

I installed Lubuntu 12.10 about 2 weeks ago and love it. Didn't have a single problem with it! Was watching a bunch of videos I downloaded with the Gnome Player (Regular Show ftw), and after about 20+ episodes the audio stuttered out of nowhere, then the video, then the whole system hung. After a restart is when the real problem happens:
It asks to login like normal, and I can select either the Lubuntu, Lubuntu Netbook, or OpenBox. By default I have Lubuntu selected. After I log in, my entire desktop is gone! No taskbar, no icons, no wallpaper. If I right-click it gives me different options, such as terminal, chromium, system tools, file manager. I can use file manager and still watch my videos and they play normally again, but like I said: I have no desktop whatsovever!!
Please help. I've been searching for hours and can't find anything similar to my problem (I did find something about the video issue that I'm no longer having).
I tried logging into the OpenBox style and it's the same way. BUT if I log into the Lubuntu Netbook style, I get my taskbar back!

Anyone have any ideas? I'm completely lost here.

Thanks in advance!

-Dzanjin 

P.S. its an HP Pavillion Desktop a1410n with an amd64 athlon processor, and I think it's the amd 6150LE graphics card.

---

### Post by Dzanjin on 2013-03-12
Desperate BUMP


C'mon guys, none of you have ever heard of the desktop vanishing? or something going crazy with the desktop environment?? 

Please, somebody give me some input! :-(

---

### Post by ManamiVixen on 2013-03-12
Here, open a terminal and type in "lxde" and see what happens. report if it works or not and paste here the terminal's output from the command.

---

### Post by Dzanjin on 2013-03-12
> **ManamiVixen said:**
> Here, open a terminal and type in "lxde" and see what happens. report if it works or not and paste here the terminal's output from the command.

Thanks for your reply!

Here is the output: 

dzanjin@dzanjin:~$ lxde
No command 'lxde' found, did you mean:
 Command 'lxdm' from package 'lxdm' (universe)
lxde: command not found
dzanjin@dzanjin:~$


did a quick search and saw to try "startlxde", i did and it said it wasn't installed and to try sudo apt-get install lxde-common.....so I did.

But when I tried startlxde after I installed it, the screen went blank and suddenly I was logged out and had to log back in.

---

### Post by ManamiVixen on 2013-03-12
Odd... Sounds like a config file for lubuntu-desktop was corrupted or missing. Hence why it wouldn't load the main desktop. try "sudo apt-get install --reinstall lxdm lubuntu-desktop"

---

### Post by Dzanjin on 2013-03-12
will try it soon, followed an ubuntu tutorial for installing lxde and some other appearance mods and now have a working desktop :-)
So at least I found a fix for it, I'm still going to see if I can fix just the Lubuntu desktop as well. Thank you!

---

### Post by Yu Jin X5 on 2013-03-12
save important stuff re install that will fix it

---

### Post by Dzanjin on 2013-03-12
Alright tried the: [COLOR=#000000]sudo apt-get install --reinstall lxdm lubuntu-desktop

it asked what was my default display something either lightbox? or lxdm so I went with lxdm and then it finished and nothing has changed...guess I'll just stick with the lxde I just installed instead.[/COLOR]

---

### Post by Habitual on 2013-03-13
backups?

---

