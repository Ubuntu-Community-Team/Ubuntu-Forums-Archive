---
title: "why won't my screenlets stay where its told?"
date: 2008-05-22
forum: General Help
---

### Post by agim on 2008-05-22
I am using the sysmonitor screenlet from screenlets-manager. I have changed the properties so it doesn't allow override options. I have in fact played with many of the options and something seems to work.
This may be one of those cases where frustration is clouding my thinking, but I cannot get it to stay where I want it. Every restart it moves and changes my options.
Please help! This should be simple but its driving me nuts.

Here are the options that I have enabled

Stick to desktop
Treat as widget
lock position
keep below
skip pager
skip taskbar
ask on override

On the screenlets-manager window itself, when you click on the sysmonitor, I have these options enabled.

Start/Stop
autostart on login

Thanks


Edit: I shouldn't have used the plural in the title, but now I don't know how to change it.
Don't want anybody thinking I'm illiterate :)
This is what happens to my brain when it gets frustrated. lol

---

### Post by agim on 2008-05-23
bump

---

### Post by prshah on 2008-05-25
> **agim said:**
> I am using the sysmonitor screenlet from screenlets-manager. I have in fact played with many of the options and something seems to work.

I had the same problem with this particular screenlet, so I stopped using it. It would not "remember" any of the settings I gave it across a restart. (Most) of the other screenlets work fine, so I just assumed there is something wrong with this _particular_ screenlet.

---

### Post by Normi on 2008-10-09
I had this problem, but I fixed it by editing the 'x' value in the ~/.config/Screenlets/Sysmonitor/default/Sysmonitor1.ini file. Mine was set to 'x=941'. I changed it to 'x=1420', which placed it right against the right-hand border of the screen where I wanted it to be.

---

### Post by cggaret on 2008-10-11
I fixed this problem by installing the latest version of screenlets from [here]("http://www.gnome-look.org/content/show.php/Screenlets+0.1.2?content=82586").  You need to completely remove your screenlets package and delete all traces of screenlets in your home folder, which are found in ~/.config/screenlets and ~/.screenlets.  Those two folders are hidden ctrl-h will show them in nautilus.  Then just delete the two folders.  Then download the new deb, double click it, and ignore the warning about an older version being in the repositories.  That did it for me.  Hope it helps.

---

