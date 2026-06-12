---
title: "Hard drive shut down with 'pop' sound"
date: 2008-02-27
forum: General Help
---

### Post by clb_illk on 2008-02-27
I tried to search the problem.
I found this thread:[http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503)
But it doesn't work.
When I found this thread:[http://ubuntuforums.org/archive/index.php/t-569711.html](http://ubuntuforums.org/archive/index.php/t-569711.html)
The guy had the same problem as mine. But I cant open the link [http://ubuntuforums.org/archive/index.php/t-569711.html](http://ubuntuforums.org/archive/index.php/t-569711.html)
which may work for me.
Any idea? Thanks at advanced

---

### Post by nick_h on 2008-02-27
There was a long thread on this (now locked) called [Ubuntu is killing your hdd!](http://ubuntuforums.org/showthread.php?t=508576).

The first thing to do is install the smartmontools package:
```
sudo apt-get install smartmontools
```

Then check the power-off retract count.
```
sudo smartctl --device=ata --attributes /dev/sda
```

This assumes your drive is /dev/sda.  Does it increase each time you reboot?

---

### Post by clb_illk on 2008-02-27
192 Power-Off_Retract_Count 0x0022   100   100   000    Old_age   Always       -       672

Yea, it increases each time I reboot.
Hard drive is sata 160g
I really don't want to give up Ubuntu. But I love my laptop more.

---

### Post by nick_h on 2008-02-28
For me this was only a problem with Feisty - it was fixed in Gutsy.  You could try the fix suggested in the thread, or perhaps someone else will have a suggestion.

---

### Post by clb_illk on 2008-02-29
I tried, but failed. My laptop is hp dv6500. Maybe the laptop and the system are not compatible. Anyway, I deleted it and run it by vmware on xp. When I find a new version which I can run on my laptop, I will be back. lol
Thanks all the same.

---

