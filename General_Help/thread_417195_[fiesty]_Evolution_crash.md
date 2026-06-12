---
title: "[fiesty] Evolution crash"
date: 2007-04-21
forum: General Help
---

### Post by drolyk on 2007-04-21
Hi All!

I`ve got the same problem with evolution. When I`m trying to start evolution it crashes everytime:

$ LANG="C" evolution
CalDAV Eplugin starting up ...

(evolution-2.10:9233): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.10:9233): e-utils-WARNING **: Plugin 'Spamassassin junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'
** (evolution-2.10:9233): DEBUG: mailto URL command: evolution %s
** (evolution-2.10:9233): DEBUG: mailto URL program: evolution
Segmentation fault (core dumped)

Is there any solution ?

Thanks

---

### Post by config on 2007-04-23
You can try starting it without plugins with command: "evolution --disable-eplugin". It will start most probably.
The problem here is in CalDAV plugin...

Solved it by starting first without plugins and than disabling CalDAV in evolution. Now it works smooth.

---

### Post by mopok on 2007-04-25
Hi, All!
I've experienced the same problem with Evolution after installing Fiesty Fawn.
The solvation was in disabling org-gnome-evolution-startup-wizard plugin.
I've just renamed org-gnome-evolution-startup-wizard.eplug file and then removed it. And everyting works fine after that, exept of the absense of welcome wizard when you start evolution for the first time. I think it is some kind of a bug and hope it would be fixed soon :)

---

