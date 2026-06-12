---
title: "Can't change icon/nautilus problem"
date: 2008-03-06
forum: General Help
---

### Post by mikeize on 2008-03-06
I originally posted this in "Desktop Effects & Customization", but didn't get any hits, so I'm trying here...

I have a shortcut on my desktop that points to a shell script, which launches a game. The icon is ugly, so I right-click>properties... and nautilus messes up: It gives me the properties box, but everything is blank except for a solitary textbox with the name of the file in it. If I do the same in Thunar, it works, but the icon is "unclickable", and I can't change it. Someone suggested that I open the file with gedit, and add an "Icon=<filepath>" entry, but that didn't work either. Also I tried reinstalling nautilus, but that didn't help. I feel like the problem is somehow with nautilus, but otherwise it seems to work fine. However, I really want some way to change this ugly icon which clashes with my desktop! Help!

-mike

---

### Post by mikeize on 2008-03-06
*bump*

---

### Post by mikeize on 2008-03-07
feel guilty bumping, but someone must be able to help me with this.  I've looked all around this forum and google, even tried to get help on the ubuntu irc.  Is this a bug I should report?

---

### Post by mikeize on 2008-03-08
so i ran nautilus from terminal, and was able to change icons, though nautilus "greyed out" and took about 30 seconds before i could do so.  strangely, thunar still "sees" the old icon, and is still unable to change icons of any files.  even though i've fixed my problem (with help from a kind soul on irc://quakenet/ubuntu), there is still something funny going on and i won't mark this thread as solved.

---

### Post by kesman on 2008-03-08
This was an interesting problem, since neither nautilus or thunar produced any error messages. Nautilus loaded the properties window for a loooong time, and thunar didn't even open it. Maybe someone has had similar problems? Note that mp3-files opened their properties just fine.

---

### Post by mikeize on 2008-03-08
just to clarify:  thunar DOES open the properties dialog, but the icon is "unclickable", ie, there's no "box" around it to indicate that you can click to change the icon.

also, i run compiz, so i tried all this in metacity (metacity --replace), and was back to the same old problems (blanked out properties dialog, and frozen nautilus), whether or not i ran nautilus from terminal, and still no error messages.

so i went back to compiz (compiz --replace), and things were back to the level of previous 'solution'.  ie, nautilus opens properties dialog but immediately freezes for 30 seconds or so, and thunar works fast, but is unable to change icons.

---

