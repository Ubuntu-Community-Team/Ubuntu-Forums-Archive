---
title: "gam_server, what is the point???"
date: 2005-04-30
forum: General Help
---

### Post by paul cooke on 2005-04-30
what does it do apart from hogging cpu, what does it really do and can I safely run Ubuntu without it?

I can't kill it as it just respawns... I can't delete the package as it wants to remove too many other packages... so can I just safely rename the binary gam_server to something else and kill it???

---

### Post by Professor X on 2005-04-30
[http://www.gnome.org/~veillard/gamin/](http://www.gnome.org/~veillard/gamin/)

---

### Post by paul cooke on 2005-04-30
[QUOTE=Professor X][http://www.gnome.org/~veillard/gamin/](http://www.gnome.org/~veillard/gamin/)[/QUOTE]

thanks for the link, but it doesn't tell me why it exists or if I really need it or if I will suffer ill effects if I get rid of it...

---

### Post by Leif on 2005-04-30
I get it every once in a while too, but a killall does the trick for me. Does your system not get back to normal after this ?

---

### Post by ssam on 2005-04-30
it monitors disks for changes, so that for example, when you save a file it shows up in nautilus straight away.

the alternative is that nautilus checks for changes every 5 seconds, but that takes even more resources, unless you set the time to maybe a minute, and then you have to wait for ages for the change.

---

### Post by paul cooke on 2005-05-01
[QUOTE=ssam]it monitors disks for changes, so that for example, when you save a file it shows up in nautilus straight away.

the alternative is that nautilus checks for changes every 5 seconds, but that takes even more resources, unless you set the time to maybe a minute, and then you have to wait for ages for the change.[/QUOTE]

I don't use Nautilus at all. I spend all my time logged in to XFCE, Icewm, Enlightenment or KDE, not Gnome.

---

### Post by 23meg on 2005-05-10
i think it has some weird interference issue with firefox. sometimes when firefox is running it suddenly makes my cpu usage peak to 80%; when i kill it and it respawns, things get back to normal. (but folders aren't updated...)

---

