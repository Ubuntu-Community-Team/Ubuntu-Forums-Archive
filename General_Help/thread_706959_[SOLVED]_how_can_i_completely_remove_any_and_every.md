---
title: "[SOLVED] how can i completely remove any and every trace of a uninstalled program?"
date: 2008-02-24
forum: General Help
---

### Post by noremacyug on 2008-02-24
title mostly says it, i'm having an issue getting cedega to reinstall and feel like its due to some leftover file(s) somewhere.  or perhaps an altered .cfg file.

i've tried 

```
sudo aptitude purge cedega
sudo aptitude purge cedega-small
sudo aptitude purge transgaming
```

---

### Post by PurposeOfReason on 2008-02-24
Do a 
whereis cedaga
locate cedaga

Just to see if it comes up anywhere with a nice and easy way. I'd imagine purge would have gotten it. Also check you're home directory for a hidden file, possibly in .config.

---

### Post by mkzimms on 2008-02-24
you could try running

```
sudo find / | grep -i cedega | less
```

that will find anything... files or folders with cedega in the name and display them in a scrollable list.  the -i will make grep ignore the case.

you'd then need to navigate to those files or folders and remove them.

---

### Post by noremacyug on 2008-02-24
awesome, i'll give those a try and report back.  much appreciated.

---

### Post by noremacyug on 2008-02-24
ok, did as you guys suggested and neither returned any trace of it.  i dunno what the deal is.  the first time i installed it, it asked me to point it to the engine and whatnot and then proceeded perfectly.  now, it doesn't do that at all.

(edit) -  i take that back.  it did return /home/guy/.local/share/applications/Cedega.desktop

(second edit) -  you guys are awesome!!! i deleted that one silly little file and reinstalled cedega.  it works perfectly and everything is back to normal!  what is the best method to uninstall programs so that they will be completely removed?  thanks again!  i'm a recent windoz convert and thus far i'm loving ubuntu!

---

