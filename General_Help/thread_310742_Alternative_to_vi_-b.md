---
title: "Alternative to vi -b"
date: 2006-12-01
forum: General Help
---

### Post by jan-h on 2006-12-01
Hi,

I'm trying to follow various threads to get my wifi card working and come unstuck with commands like

vi -b /etc/Wireless/RT61STA/rt61sta.dat

Is it possible to edit these files in gedit or anything useable to a linux newbie, or is -b switch unique to vi? I've been googling vi and vim tutorials but finding it hard work - the arrows don't work, the mouse doesn't work, and the help seems to be broken. Once I get my computer to work I'll happily learn the arcanery of vi as a pennance, but right now I just want to use an editor I can manage while trying to get my head around the wireless driver setup.

Thanks for any help,

Regards
Ian

---

### Post by LLRNR on 2006-12-01
vi ? :lol: Who on this earth is so rude to instruct you to use **vi**?

Try **nano** instead of vi (and without the -b switch, too) - it's an intuitive text editor where you only have to know 2 things: Ctrl+O = Save & Ctrl+X = Exit.

Cheers,

LLRNR

EDIT - Sorry I didn't notice that : you can use GEdit, too: just hit Alt+F2 and type *gksudo gedit* (and the name of the file too with the full path if that's needed); or, if you're on KDE, type *kdesu kate*.

---

### Post by jan-h on 2006-12-01
Thanks. That's much nicer.

---

### Post by AndyCooll on 2006-12-01
And _yes_ you could type:
```
gksudo gedit /etc/Wireless/RT61STA/rt61sta.dat
```
and work with that instead.

:cool:

---

### Post by CatKiller on 2006-12-02
Wow, I never knew that. **man vi** says >        -b          Binary  mode.  A few options will be set that makes it pos&#8208;
                   sible to edit a binary or executable file.
 vi really is amazing. It's a shame mortals like us don't know how to use it.

---

