---
title: "[SOLVED] Drive space, in use, still available?"
date: 2007-12-16
forum: General Help
---

### Post by foolios on 2007-12-16
How do you look at the details for how much available space is left on a drive?
Is it possible to view it by going to places? WHen I do, I tried to change the view to show details but under size it shows 3 dots...

Thanks in advance

---

### Post by benerivo on 2007-12-16
If you install Gparted, it will graphically show you your hard drive / partition information (including how much space is left on each).```
sudo apt-get install gparted
```

---

### Post by foolios on 2007-12-16
Is this already set up for gutsy gibbon on fresh install or do I still need to run the command?

---

### Post by foolios on 2007-12-16
I tried it anyways and it seemed to take ok. I went to system and ran partition editor. I was titled GParted once it ran. THing is, it keeps scanning and doesn't update with any details. 
I found system monitor to show me the drive info though. I wonder why Places > Computer still doesn't update the size of the drives even after GParted is installed. Must be a bug in the system...

---

### Post by foolios on 2007-12-16
There we go, GParted finally finished after a few more minutes. Places > Computer still not updating. This must not be affected by GParted. 

Thanks for the help.

---

### Post by mcduck on 2007-12-16
No need to install anything new.

Applications/Accessories/Disk Usage Analyzer.

Or from a terminal, run "df -h" :)

---

### Post by foolios on 2007-12-16
Awesome, Thank you both.

---

