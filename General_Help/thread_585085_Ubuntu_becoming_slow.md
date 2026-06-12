---
title: "Ubuntu becoming slow"
date: 2007-10-21
forum: General Help
---

### Post by mk04 on 2007-10-21
Few days ago I had to do a reinstall to Windows. This is when I realized how slow Ubuntu was. I know it won't last too long after the viruses come back. My question is in Windows there is a "disk cleanup feature" to delete temporary files, recycle bin, etc... Is there a similar feature in Ubuntu. I guess my goal is to make Ubuntu faster. Everything is very slow. When I run Firefox, OpenOffice, AWN, XGL, Metacity, Terminal, applets, etc.... Once in a while everything stalls for a minute and goes back to "normal". My computer specs are in my signature. I have a ATI Radeon 345M card

---

### Post by atlfalcons866 on 2007-10-21
i dont think 512mb ram is enough to run all those

---

### Post by science4sail on 2007-10-21
try [this]("http://rudd-o.com/archives/2007/10/02/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that/")

---

### Post by mk04 on 2007-10-21
Results from "top"
```
 4791 mutazk04  15   0  142m  50m 7340 S  7.7 11.5  26:23.06 Xgl                
   10 root      10  -5     0    0    0 S  0.3  0.0   0:34.64 kacpid             
 4820 mutazk04  15   0 15528 7708 5992 S  0.3  1.7   0:27.92 metacity           
 4827 mutazk04  15   0  108m  15m  11m S  0.3  3.6   0:05.51 nautilus           
 6281 mutazk04  15   0  269m  76m  20m S  0.3 17.4   4:51.81 firefox-bin        
14330 mutazk04  15   0 84492  14m 9848 S  0.3  3.3   0:00.99 gnome-terminal
```

Gnome System Monitor says I'm using about 60% of my memory (270/440MB) and about 10% of my swap (10MB/1.3GB). So I'm not maxed out on my memory.

Another note, I also am running Kubuntu alongside Ubuntu. There was a decrease in performance when I did this. So there are some KDE programs running. I plan on erasing Kubuntu and installing Gusty (KDE) on a separate partition in next week.

---

### Post by mk04 on 2007-10-21
Okay, I decide to remove KDE and emptied my Trash (over 1GB). The system does seem to perform better. Where are the temporary files located and is it safe to delete.

EDIT: According to System Monitor my memory is about 44% and swap is at 11%. So that is a drop of about 20% in user memory.

---

### Post by malangaman on 2007-10-21
When you say you have Kubuntu running alongside Ubuntu, what do you mean, exactly?

---

### Post by silentb on 2007-10-21
My computer specs are exactly the same as yours and I experience no slowness though I tend to run several programs in parallel (e. g. Kile, Acrobat, Gnuplot, Netbeans (a heavyweight), IPython, Inkscape while typing texts for university). Maybe you have a program which takes up or leaks memory from time to time? Run "top" longer and see if you discover something...

---

### Post by RandySavage on 2007-10-21
I find Gutsy slow too.  Real slow.  I figure its just about the slowest Linux distro I've tried, even slower than Opensuse.

I don't know what its doing in there, but its doing something.  Sometimes it'll access my drive for 10 minutes straight even if I'm running nothing and its just sitting there after a fresh boot.

---

### Post by HermanAB on 2007-10-21
Run 'top' and kill the stuff that is wasting resources.  They will be at the top of the list - that is what 'top' does.

---

### Post by kelbizzle on 2007-10-21
I have a 1.8 Ghz P4 with 768 MB of ram. With an old nvidia card. Gutsy runs well for me along with compiz I run gimp, firefox, pidgin, rhythmbox, and evolution and it doesn't seem slow. I could still open a pdf from the net faster than the core duo's at work running xp.

---

### Post by Ninjaraffe on 2007-10-24
Gutsy comes with "tracker" pre-installed for indexing. Indexing eats up resources and basically constantly accesses the hard drive, especially right after boot up. Try changing the performance settings in tracker or disabling indexing all together.

---

### Post by ssc351 on 2007-11-20
> **science4sail said:**
> try [this]("http://rudd-o.com/archives/2007/10/02/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that/")


Scienceforsail...this link works awesome!  I was getting really dissappointed in Gusty speeds when compared to Fiesty...now I can't say I really notice a difference!

Thanks!

---

### Post by BigHairyTroll on 2007-11-26
Well, I experience the same - a shame: I just reinstalled from scratch (a week ago) to clean up after having had Ubuntu7.10, Kubunto7.10 and 6.6LTS in multiboot working fine.
Maybe I overdid it a little with the Firefox extensions?

I just installed Samba and set up my stuff as a file server with automatic reconnection to Windows shares for auto backup at night.
To boost performance a little when my screen/keyboard/mouse are switched to my Windows PC, I have the habit of stopping the GDM.
Could this have an effect?
(Network activity is very low between these computers - or it should be at least - how do I monitor that?)

Thanks

---

