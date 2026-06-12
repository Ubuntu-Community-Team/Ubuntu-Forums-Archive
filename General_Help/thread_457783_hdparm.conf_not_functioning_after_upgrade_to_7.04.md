---
title: "hdparm.conf not functioning after upgrade to 7.04"
date: 2007-05-29
forum: General Help
---

### Post by jazzgossen on 2007-05-29
After I upgraded my 6.06 installation to 7.04 (through 6.10), it seems that my hdparm.conf is no longer read. I have specified that one of my hard drives should spin down in hdparm.conf, like this:

```
/dev/hda {
#       mult_sect_io = 16
#       write_cache = off
#       dma = on
        spindown_time = 1
#       standby
}

```

That used to make the drive spin down after a few minutes, but now, it just keeps spinning until I do a "sudo hdparm -y /dev/hda".

Any ideas why?

---

### Post by kuja on 2007-05-29
Personally, I always found the conf file and the init script to be overly complicated. 

What I usually do is rm /etc/init.d/hdparm and just remake that script with whatever commands I want it to do, as in, just regular hdparm commands, like you'd do in a terminal. Give that a try if you want to :)

---

### Post by olafbooij on 2008-03-21
Hi,

I just ran into this problem with Gutsy Gibon. Seems like Gutsy (and probably also Fiesty) does not automatically run /etc/init.d/hdparm and thus, the changes to /etc/hdparm.conf have no effect. You can check this by running:
```
ls -l /etc/rc*|grep hdparm
``` 
in a terminal. If it does not return anything then there is no link to hdparm script.

The best way to solve this is to create such links:
```
sudo update-rc.d hdparm start 7 S . stop 75 0 6 .
```

(I guess this is a bit late for jazzgossen, but just in case somebody else reads this thread.)

Olaf

---

