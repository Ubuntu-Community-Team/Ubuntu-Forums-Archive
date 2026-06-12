---
title: "Help me bring an old laptop back to life!"
date: 2007-04-23
forum: General Help
---

### Post by raul_ on 2007-04-23
He is already breathing, so the hard part is done :)

We're talking about a Toshiba Satellite 4060CDT, 64MB RAM, 333Mhz, 4.3GB

I installed Feisty Server. and E17 on top, but i was very disappointed to see that E17 was really sluggish here (Yes. i'm typing from the laptop), so I tried Fluxbox. Right now the speed is acceptable (not slower than a normal Windows installation) but there are some details to fix, and I hope you guys can help.

The most annoying thing, is that the display is in a square, in the middle of the screen, i.e, it doesn't fill the monitor. I tried xorg reconfigure many many times, but nothing, so i suppose i'll have to find a hack.

I also need a really good fluxbox configurator guide (background, menus etc). Right now i'm using the Vista Black theme, and it's pretty neat :) I don't know why i don't have a background, but i'll figure it out.

If I remember some more things, i'll post

I'm really counting with you guys :)

EDIT: I now remember that the reason why E17 was slow, may be GDM. I'm not using a login manager right now (removed it) but i can't start X from the terminal with E17 because X calls "enlightenment" instead of "enlightenment_start". How can I specify what WM to call from the terminal?

Also, with fluxbox, the changes i make to X (styles for example) are not saved. I think it's because it can't access some files, but i can't do a "sudo startx" because it hangs. Any ideas? :)

---

### Post by RedSquirrel on 2007-04-23
[Here]("http://ubuntuforums.org/showpost.php?p=2417065&postcount=39")'s a post about the backgrounds. In fact, that thread had some pretty good ideas about lots of things, including menus.

[Here]("http://ubuntuforums.org/showthread.php?p=454217")'s a guide that might help with your display issues. Of course, you'll need appropriate drivers too.

The "wiki" link in my sig is a pretty good source of info. So are these ubuntuforums. Lots of good posts about Fluxbox here.

---

### Post by raul_ on 2007-04-23
Hey. I got my styles from your signature, even before you posted the reply! I guess it serves it's purpose :) i'm now trying E17 again. i managed to start it with "startx /usr/bin/enlightenment_start". It's still sluggish though. I'm now trying to find lightweight applications, since Kazehakase and Gaim aren't light enough. 'll check the links you gave me, thanks :)

---

### Post by john_spiral on 2007-04-23
Hi Paul,

This may sound like heresy but have you thought of loading a lighter distro like Elive? 

If you have some spare disc floating around would love to hear which runs faster:

Feisty Server & E17

or 

Elive

?

John

---

### Post by raul_ on 2007-04-23
> **john_spiral said:**
> Hi Paul,

This may sound like heresy but have you thought of loading a lighter distro like Elive? 

If you have some spare disc floating around would love to hear which runs faster:

Feisty Server & E17

or 

Elive

?

John

Hey =) it's Raul, but that's ok. Actually I tried Elivecd but it was just impossible to do anything. The installer took ages to open and from one step to another, at least 5 min pass..now imagine that for a whole system install. Feisty Server installs in about half hour, then you have to grab the packages yourself (aptitude install xorg, for a start) and it runs ok. I would be happy with fluxbox if it wasn't for this annoying display issue :(

---

### Post by raul_ on 2007-04-23
I think I screwed up with xvidtune =\ now my monitor is "fine" except for a pink bar at the bottom, and i don't know how to solve that...

EDIT: just a scare. Changing default depth solved it

---

