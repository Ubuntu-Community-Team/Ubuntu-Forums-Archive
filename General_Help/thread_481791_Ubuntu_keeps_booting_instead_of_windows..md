---
title: "Ubuntu keeps booting instead of windows."
date: 2007-06-22
forum: General Help
---

### Post by NJNETSFAN on 2007-06-22
I have ubuntu 6.06 on a 10GB partition on my hdd. I have windows vista also on the same hdd. I wanted to dual boot, so I installed ubuntu, but instead of giving me a choice of what OS to boot from, it automatically boots into linux. can some1 please help me asap on how to fix this. I'm a complete noob so please explain the best you can.

---

### Post by cyrusrayne on 2007-06-22
It's ok to be a noob, we all are at some point :)  When your computer first starts, you should look closely for a prompt that says something like

GRUB <insert version info>
Press esc to enter menu <countdown>

You usually only have three seconds to do this, so it's recommended to pay close attention, or you could repeatedly press escape as many people do (I've used a similar method to even access my bios).  If it has an option to boot into Vista in the menu for GRUB, then you could select that or if it gives you a choice, allow you to view the boot menu when your PC turns on.

If Vista does not show up in this menu (which is of course not the best scenario when you're getting started, I'm also doubtful that this happened), then it's possible your install of Vista is dead.  Again, this one is absolute worst case scenario.

Just remember to try and press escape when it gives you a countdown for GRUB and see if it's possible to let it allow you to choose the OS that boots instead of just booting to Ubuntu.

Good luck :)  If you need more help there's always somebody on that could help you :)

---

### Post by NJNETSFAN on 2007-06-22
ok, well I'll try that and post back what happens. ok, ofcourse vista isn't in the list. These are the choices I get: Ubunutu, kernel 2.6.15-26-386, then another option is the same thing except recovery mode and then there is a third option named Ubuntu, memtest86+

---

### Post by NJNETSFAN on 2007-06-23
can anyone help? I've been working with someone on another message board and I have gotten to the vista loading screen and it just stands there, anybody know how to get this fixed?

---

### Post by vexorian on 2007-06-23
well those are good news, it means your vista is alive, but the thing is that vista is not too friendly with ubuntu's default  grub Config.

Try adding rootnoverify (hdx,x) to the vista entry like

```

title=Winbugs MalaVista
rootnoverify (hdx,x)
chainloader +1
makeactive
```

replaCe (hdx,x) with vista's partition...

--
If nothing works you probably Can restore a windows-friendly MBR from windows vista's (and lose ubuntu)

---

### Post by NJNETSFAN on 2007-06-23
ok well here's what I'm running right now to get vista to even load > 
title Windows Vista
rootnoverify (hd0,0)
makeactive
chainloader +1maybe that'll help before I change anything.

---

### Post by vexorian on 2007-06-23
i onCe had windows XP staying freezing during logo.

ideas:
- make sure there are no CDs in the drive (It made XP freeze for no reason)
- try CheCking if you Can run safe mode on Vista.
- try swapping Chainloader +1 and makeaCtive

---

### Post by NJNETSFAN on 2007-06-23
ok well I changed what you said, and I started vista into repair mode, and i went through a screen saying windows is loading files, to the vista loading screen, and now I'm at a completly black screen(went through this before and it just stayed on the black screen for over 20 minutes. here is a link to my other thread on another website to show you what I've done so far [http://www.computerforum.com/88596-new-linux-need-help-installing-4.html](http://www.computerforum.com/88596-new-linux-need-help-installing-4.html)

---

### Post by NJNETSFAN on 2007-06-23
i missed your last post vexorian, but I tried booting up vista holding the f8 key, and the menu for safe mode won't pop up.

---

