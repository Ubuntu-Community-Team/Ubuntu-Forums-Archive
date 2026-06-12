---
title: "amsn on kubuntu 8.04 upgrade"
date: 2008-05-12
forum: General Help
---

### Post by lmc on 2008-05-12
Hi I was wondering if anyone had tried to use amsn after upgrading to kubuntu 8.04?

I installed the 8.04 LTS via adept-updater.  I can open amsn, but when I try and log in the screen goes blank and it freezes.

It has also started to freeze when shutting down (niiice), but I think I have fixed this by following another thread to add code to /etc/init.d/halt.
(ETA that didn't work, so I have to now shutdown/restart using "sudo shutdown -h(or -r) now")

anyways, any help would be appreciate, I wish I had just stayed with 7.10 ! :???:

---

### Post by Zorael on 2008-05-12
I can't say for sure if this'll help you on this one issue (never heard of it before), but the blanket fix-all workaround would be to **completely remove** the aMSN packages in Synaptic and then reinstall it. Make sure you have disabled any extra repositories in Software Sources before doing this.

Terminal way would be:
```
$ sudo aptitude purge amsn
$ sudo aptitude install amsn
```

Failing that, you could (temporarily) remove your own personal aMSN settings by renaming the [FONT="Courier New"].amsn[/FONT] directory in your home dir. All directories prefixed with a dot are hidden, so it may not appear as if it's there. (It *should* be named .amsn, but pidgin, for instance, saves stuff under .purple, so I may be wrong.)
```
$ mv ~/.amsn ~/amsn-backup
```

---

### Post by lmc on 2008-05-13
hmm how embarrassing. It works okay now I am at home. I think it was just to do with the firewall/university proxy. thank you for your help! :)

---

