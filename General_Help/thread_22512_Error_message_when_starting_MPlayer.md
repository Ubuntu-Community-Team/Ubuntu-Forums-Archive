---
title: "Error message when starting MPlayer"
date: 2005-03-28
forum: General Help
---

### Post by MrFunster on 2005-03-28
I have installed MPlayer using various howtos - the most recent being Rastamahata's

In each case when I start it I get a window with an error message:

New_Face failed. Maybe the font path is wrong. Please supply the text font file (~/.mplayer/subfont.ttf).

Anyone seen this before?

---

### Post by ubuntu-geek on 2005-03-28
Make sure you have the mplayer-fonts package installed that could possibly be the problem.

sudo apt-get install mplayer-fonts

---

### Post by blackkrusty on 2005-03-28
HI,

i have a problem too while installing mplayer on a warty ( 4.10). I took
the lastest tar.gz file, but when doing ./configure the configure script complain
about X11 support.

When trying to install it with "apt-get install xlibs-dev", apt tell me some messages like that :

The following packages have unmet dependencies:
Depends: libdps1-dbg but it is not going to be installed
Depends: libice-dev but it is not going to be installed
....
..
.

it is the same pb as here 
[http://ubuntuforums.org/archive/index.php/t-1562.html](http://ubuntuforums.org/archive/index.php/t-1562.html)

I'm new in ubuntu, can somebody tell me what i should do ?
Many thanks in advance !

---

### Post by MrFunster on 2005-03-28
[QUOTE=ubuntu-geek]Make sure you have the mplayer-fonts package installed that could possibly be the problem.

sudo apt-get install mplayer-fonts[/QUOTE]

Thanks, I'll give that a whirl next time I fire up my ubuntu box

---

### Post by MrFunster on 2005-03-28
Yep - that's done the trick.
Thanks for that.

---

### Post by lorap on 2005-03-28
hi!
don't create a wheel friend!
you've to go to the Computer-->Computer Management-->Synaptic Package Manager.once you've the synaptic window open go to the Settings-->Repositories.
once you've a new small window open mark all possible checkboxes ignoring the worning messages after what press Ok button.the window closes and you're back again to the main synaptic window.press Reload button and wait until the process completes.after the process's completed press the Search button and in the search window write in VLC then press Ok button.once the synaptic picks it up for you mark the VLC whose remarks're "for gtk+" but not for the gnome.that one for the gnome has a bug.after you mark it for installation press Apply button.that's all.
have a nice day friend!
pavel

---

