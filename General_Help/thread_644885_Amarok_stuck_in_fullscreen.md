---
title: "Amarok stuck in fullscreen?"
date: 2007-12-19
forum: General Help
---

### Post by skinind95 on 2007-12-19
Hello,

This should be simple, but i'm fairly new to linux and i'm still learning.

Somehow i've got Amarok to take up my entire screen and i cant get it off.  There is no containing window, no exit/minimize/maximize buttons, and it covers my panels.

I think i may have hit a button that either toggled fullscreen in Amarok, or had my window manager remove it's window.  I've looked through all the options in Amarok and turned off desktop effects.  Still nothing.

I also tried to reinstall it, but it kept its settings and its music database.  Is there a way to start completely over without any of the previous settings getting carried over?

Thank you very much for your help,
Travis


Edit -- I am running Ubuntu Gutsy

---

### Post by forestpixie on 2007-12-19
wait around for another help - you might get out of fullscreen, cos I can't remember :)

if you don't and you want reinstall from scratch and lose the config - open nautilus, do - view show hidden files and navigate to

/.kde/share/apps - delete the amarok folder and reinstall

---

### Post by vallis on 2007-12-19
Hi,
if you're using KDE then you can press alt+f3 to get the window options menu, under advanced there is a toggle fullscreen option.
not sure how to do this in gnome but i'm sure there must be similar keyboard shortcuts.

---

### Post by skinind95 on 2007-12-19
Vallis -- I'm using Gnome.  Sorry I didnt specify that. =)

ForestPixie -- Thank you for that, It did reset all of my settings in Amarok.  But, unfortunately, it is still fullscreen.  This might be a problem with the window manager?

Another thing i noticed -- It doesn't seem to be "double buffering" the graphics (thats what i would call it, i dont know if thats the term though).  When things change it will show glitchy black squares over things, and the list graphics refresh in a wiping down motion.

---

### Post by skinind95 on 2007-12-19
Hm, with Amarok open, and Alt+Tabbing to bring up the effect menu, i have lost ALL window decorations. Here are some pics.

[img]http://farm3.static.flickr.com/2124/2122770127_147ac724c1_b.jpg[/img]


[img]http://farm3.static.flickr.com/2044/2122770131_fbc1b8b06a_b.jpg[/img]


Does Amarok use some kind of kde->gnome thing that i need to reinstall?

---

### Post by asmiller-ke6seh on 2007-12-19
Are you using COMPIZ FUSION?

---

### Post by skinind95 on 2007-12-19
I'm not sure, it's just what came with Gutsy (Well, its actually Linux Mint 4.0, but its Gutsy based).  It was working fine for a while, until firefox froze up my computer and i started pressing keys.  I must have hit a combo that did something.

---

### Post by tzd on 2007-12-24
EDIT: Please see below for a solution that worked for me.

I'm having the same issue. I am using compiz fusion. 
Amarok was working flawlessly on my Kubuntu Gutsy gibbon until today when it started up without the "upper panel" with the maximize and minimize buttons etc. My theme works though. 
Another issue that also appeared today at the same time was that my autorun programs didn't run at all. I've right clicked them when they were in system tray and choosen to have them automatically started via 3rd party software that enabled programs to autostart and also start minimized.... it was either called "kDocklets" or "alltray". 

Would love to get some help with the issue with Amarok (love it way too much ;)). The autostart issue is solved via adding links to the autostart folder in .kde folder.

Thanks in advance :)

EDIT: 5 minutes later I've right clicked on my amarok icon in the kicker and chose "Advanced" and then "Fullscreen". This solved my issue and perhaps yours as well Skinind95?

---

### Post by dlegend on 2007-12-24
Have you tried pressing F10? I have my full screen toggle key at that... Don't remember if that is default or not.

---

### Post by skinind95 on 2007-12-25
tzd -- Thank you for this information.  I'm not using KDE and dont have the kicker menu's but i'm sure someone who is having this problem will find it useful.

dlegend --  F10 must not be a default fullscreen key, because it didn't work UNTIL i went into keyboard shortcuts under Window Management -> Toggle Fullscreen Mode and set it to F10.  Opened up Amarok hit F10 and all is back to normal! Thank you so much, and thank you everyone for your help. =)

So if anyone is having this problem, add Toggle Fullscreen Mode as a keyboard shortcut, and then hit it in the window.  Alt+F4 would minimize Amarok to the tray, but for other applications stuck in fullscreen it will probably close them.


Thank you all,
Travis

---

