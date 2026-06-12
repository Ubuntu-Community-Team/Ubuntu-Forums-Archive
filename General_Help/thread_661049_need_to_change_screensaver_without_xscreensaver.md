---
title: "need to change screensaver without xscreensaver"
date: 2008-01-07
forum: General Help
---

### Post by dragon-architect on 2008-01-07
I have Gutsy Ubntu v. 7.10 and I followed the HOWTO here to change gnome-screensaver to xscreensaver. That worked fine for a while until stupid, naive me decided to go through all the screensavers I had. Big mistake. Now, xscreensaver is set on a screensaver that totally locks up my system and I can't start the daemon lest I wanna suffer a total system lockup.

I did a search of the forums here and I tried to search some of the directories that I saw were suggested, but nothing worked. I can't find the config file they say I need to alter, so I have a question. Can the screensaver in xscreensaver be changed via the command line?

I tried searching through /usr/share/xscreensaver, /home/<myusername>/.config, and I even attempted to browse to /home/<myusername>/.xscreensaver, but THAT directory doesn't even EXIST on my computer. O_o; Any help here please? I seem to be one of those people that computers just don't like to work 100% normally around me.

---

### Post by dragon-architect on 2008-01-14
*bumps thread after waiting several days for a reply*

---

### Post by Anduu on 2008-01-15
Show hidden files in your home folder.

Find the file .xscreensaver and open it with your favorite editor or just "gedit ~/.xscreensaver" in a terminal.

Find the entries  that look something like:

```
mode:		one
selected:	200
```

Change the number of selected to something else.Save and run xscreensaver-demo.

BTW 200 specifies the Flying Toasters screensaver so if that one works ok for you you're all set.If not try random numbers till you can get in.

---

### Post by dragon-architect on 2008-01-15
How do I show hidden files in my home folder?

<EDIT> Nevermind. Just found it.

---

