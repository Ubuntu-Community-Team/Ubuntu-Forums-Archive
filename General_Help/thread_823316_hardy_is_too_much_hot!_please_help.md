---
title: "hardy is too much hot! please help"
date: 2008-06-09
forum: General Help
---

### Post by Futureking on 2008-06-09
hi

I am using ubuntu hardy with wubi install. My CPU usasge seems to be always high. therefore cpu temperature incresese. I have windows xp. but in windows xp this does not happens. after checking system monitor I found that...
it is using only 33% of RAM and 4KB (0%) OF SWAP and forcing all work on CPU.

In windows XP RAM usage and virtual memory usage always high but it don't force CPU to do all work. Temperature monitor shows temperature normal.

How can I force ubuntu to use swap space and free CPU.

Sometimes my cpu temperature becomes 60C+. Please help

see this screenshot:
  [FONT=Arial, Helvetica, sans-serif][[IMG]http://img196.imagevenue.com/loc406/th_97618_Screenshot_122_406lo.jpg[/IMG]]("http://img196.imagevenue.com/img.php?image=97618_Screenshot_122_406lo.jpg")[/FONT]

I have P4 machine with 1 GB RAM.

---

### Post by wdaniels on 2008-06-09
> **Futureking said:**
> How can I force ubuntu to use swap space and free CPU.

Lower RAM usage does not come at the expense of higher CPU usage - these are completely different things and entirely unrelated in that sense. Linux uses less RAM than Windows because it is more efficient, that's all.

What processes are using the most CPU time?

---

### Post by Futureking on 2008-06-09
if I open firefox then it uses more cpu. If I open appearance dialog box then it uses about 100% of cpu. 

mostly I open both program.

If I am watching online(like this screen shot shows)and if I make that windows big it uses more cpu and if I make it small then it uses less cpu.

---

### Post by jrharvey on 2008-06-09
What speed is your pentium 4? Sometimes Firefox can use alot of CPU. This is actually not that shocking to me since you are running a single core P4.

---

### Post by wdaniels on 2008-06-09
I didn't notice before that you were watching a flash movie - Adobe's Linux plugins are notoriously poor quality, and problems with very high CPU usage are common. The best I can suggest is that you try out the new flash 10 beta, which many have said is an improvement.

[Markus Thielmann]("https://launchpad.net/~thielmann/+archive") has published a package for this in his PPA, which you can use as follows:

Go to System->Administration->Software Sources and click on the "Third-Party Software" tab. Press the button "Add..." and paste in the following line when prompted:

```
deb http://ppa.launchpad.net/thielmann/ubuntu hardy main
```

Now close that (it should update the software index automatically) then open a terminal and run:

```
sudo apt-get install flashplugin-nonfreebeta
```

Press "y" when it asks you to confirm about installing an unauthenticated package.

Restart firefox and type in the address **[noparse]about:plugins[/noparse]**. You should see a page called "Installed Plugins" where the first entry is something like:

```
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 b218
```

If the version here reads "10.0 b218" then you are now using the new flash 10 beta. Please report back whether this helps with the CPU usage. You will probably find that the usage is still quite high, but hopefully it will be better enough to stop your CPU getting that hot.

---

### Post by /etc/init.d/ on 2008-06-09
Watching a Flash movie in Linux will easily commandeer most of the CPU.  Flash is ridiculously resource-intensive in Linux.  Besides you are only on a P4, hardly a powerhouse and notorious for running hot.

---

### Post by Futureking on 2008-06-09
THIS not only happens with firefox but also with appearance preferences. with firefox cpu problem happens sometime. with appearance preferences cpu problem occurs everytime.

  [FONT=Arial, Helvetica, sans-serif][[IMG]http://img157.imagevenue.com/loc612/th_42368_ss_122_612lo.jpg[/IMG]]("http://img157.imagevenue.com/img.php?image=42368_ss_122_612lo.jpg")[/FONT]

---

### Post by jrincon87 on 2008-06-09
Thanks wdaniels, that was a definite solution to the same problem I had in Firefox. First I tried downgrading to Firefox 2, but it didn't help at all. 
PD: You should put it as a How-To, it might help a lot of people.

---

