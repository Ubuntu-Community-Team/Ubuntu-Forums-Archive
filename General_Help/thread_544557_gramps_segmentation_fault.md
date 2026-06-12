---
title: "gramps segmentation fault"
date: 2007-09-06
forum: General Help
---

### Post by zorkerz on 2007-09-06
Hey there
I would like to mess around with gramps.
I have installed the program from the repositories.
I get this error when attempting to run it.
> ~$ gramps
Segmentation fault (core dumped)
Anyone know what I can do about this?
Or if not are there any other similar apps?
thanks

---

### Post by areteichi on 2007-10-05
I have the same problem in Debian Lenny.

Does anyone have a solution?

---

### Post by rsambuca on 2007-10-05
Try re-installing.  I have been using the version from the repos for quite a while and never had a problem.

---

### Post by Daveth on 2007-10-05
so have I and it installed just fine and took over my Gedcom file from another program without hitch.

---

### Post by areteichi on 2007-10-05
I actually fixed it by editing /usr/share/gramps/Spell.py
I followed the procedure indicated by the following links:

[http://bugs.gramps-project.org/view.php?id=1272#bugnotes]("http://bugs.gramps-project.org/view.php?id=1272#bugnotes")
[https://bugs.edge.launchpad.net/ubuntu/+source/gtkspell/+bug/120569]("https://bugs.edge.launchpad.net/ubuntu/+source/gtkspell/+bug/120569")
[http://launchpadlibrarian.net/9503542/gramps_2.2.8-1ubuntu1_2.2.8-1ubuntu2.debdiff]("http://launchpadlibrarian.net/9503542/gramps_2.2.8-1ubuntu1_2.2.8-1ubuntu2.debdiff")

and the part of my Spell.py looks like,

[PHP]    else:
#        gtkspell.Spell(gtk.TextView()).set_language(lang)
        tv = gtk.TextView()
        gtkspell.Spell(tv).set_language(lang)
        success = True[/PHP]

I apologize for questioning before doing my own research. I hope this solution will help anyone who may encounter this problem.

---

### Post by zorkerz on 2007-10-06
I did the same thing as byagietera and it worked here as well. I also filed a bug in launchpad and with the gramps developers and it has been marked as fixed so its possibly this fix will be unnecessary soon.
cheers

---

