---
title: "boots through splash screen, then seems to be GNOME terminal, with nothing"
date: 2008-03-02
forum: General Help
---

### Post by ll0Adonis0ll on 2008-03-02
i am pretty new to ubunutu/linux and have just tried my first install to some old (made in 2000) computer and after a day and a half of battling boot sequences, installation problems and just plain software stubbornness, i think im very close. i tried installing directly from the live CD and everyhting would work(slowly) except for the whole installing thing, it would just sit there with a blank window. finally i used a newer motherboard with the same CD and HDD and got it installed easily, now i bring it back, and boot up
it goes to the ubuntu splash and load screen fine, then goes through anf gives me this
```

*Starting anac(h)ronistic cron anacron                          [ok]
*Starting deferred execution scheduler atd                  [ok] 
*Starting periodic command scheduler crond                [ok]
*Checking battery state...                                           [ok]
*Running local boot Scripts (/etc/rc.local)                    [ok]

```

then gives me a blinking cursor, if i type something, itll either be jiberish or the letter i typed
if i hit enter, itll just go to the next line, no comments or anything

if i tap the off button on the box, it says 
```

Stopping GNOME display Manager.....
```
and does nothing

i tried using booting into recovery mode and get to bash with everything looking fine, then tried the ```
startx
``` iv found on other threads but get a big long list of stuff that basically says error, with things including something about no display detected. using bash i manuver to the Examples folder and try to run ```
gimp logo-ubuntu.png
``` and get a no display detected

apparently software and i dont get along

from the live CD i love Ubuntu, great job, truly, any help would be greatly appreciated

---

### Post by oakgrove on 2008-03-03
A (fairly) easy way to see if GNOME Display Manager is causing your problem is to log into the recovery console again and when you get to your bash prompt after logging in, navigate to the /etc/rc2.d/ directory.  Do an ls command to get a directory listing so you can see what you have there.  Those are all of the scripts that run various daemons and programs when you start into Ubuntu normally.  You should notice one that says S30gdm.  If it isn't S30gdm, it'll be S something gdm.  That is the script that starts your Gnome Display Manager.  Type sudo mv S30gdm D30gdm.  This changes the scripts name from (S)tart to (D)isabled.  Do an ls again to see the difference.  

At this point, you can type "sudo shutdown -r now" to reboot your computer.  Boot it up normally and you eventually will get dropped off to a terminal prompt (since we have disabled gdm) where you will have to log in.  Once you do that, type "startx".  This starts x and bypasses gdm.  To fix gdm back, just do what you just did and change the D to an S on D30gdm.

---

### Post by ll0Adonis0ll on 2008-03-04
thanks for your reply

i did everyhting you desribed successfully, but when i execute the "startx" command, it gives me some version info and an error messege from X. i cant recall the exact error mesege other than being identifid as 104, i think. ill get that this evening. from this, im fairly sure ill need to find a driver for the video card, which has a DVI output, (I'm using a DVI-VGA plug for the monitor would this cause problems? expecially after Ubuntu being installed on a different motherboard?) and ill need to install it using bash, will a good set of instructions come with the driver or is there a standard for installation that i should follow.

what confuses me still is that the splash/loading screen for Ubunutu still displays fine in good resolution. any help with this please?

---

### Post by unutbu on 2008-03-04
At what resolution do you wish to run your monitor?

Since you get a good looking splash screen, I'm going to assume it isn't a video card driver that you need. I'm guessing then that the most likely culprit is that your xorg.conf file needs to be tweaked. (Perhaps your requested resolution is too high, or Modeline, HorizSync or VertRefresh is wrong...)

Please post
```

cat /etc/X11/xorg.conf

```

---

### Post by unutbu on 2008-03-04
Please also post

```

cat /etc/usplash.conf

```

That will show the resolution of the splash page... the resolution that is working for you.

---

### Post by danwood76 on 2008-03-04
> **unutbu said:**
> 
Since you get a good looking splash screen, I'm going to assume it isn't a video card driver that you need. 

The splash screen doesnt have anything to do with X as such so it is possibly a graphics driver problem.

What graphics card is in the machine?
And as unutbu said post your xorg.conf.

---

### Post by unutbu on 2008-03-04
danwood76, thanks for the information.
If the graphics driver is not needed to display the splash screen, what is?

---

### Post by danwood76 on 2008-03-05
It uses either the linux framebuffer or direct vesa access so the graphics driver set in X will have no effect on it.

To the OP:
Can you post the output of the following commands (they check if there are errors or warnings in your xorg logs)
```

cat /var/log/Xorg.0.log | grep '(WW)'
cat /var/log/Xorg.0.log | grep '(EE)'

```

regards,
Danny

---

### Post by ll0Adonis0ll on 2008-03-05
well, i hate to disappoint and would love to find the nitty gritty details of the system, but after just a quick glance at the .conf files,(even without screen scrolling, so i dont know exactly how much i didnt read) i found that the way something was set up was that it was looking for Intel integrated graphics controller instead of going through the PCI controller to the card, i re-installed from the live CD, which worked now, no idea why, and got everything working fine. very good job to the writers by the way. everything works fine and i plan on spreading the word. 

an a tip for anybody having trouble partitioning to the HDD from setup, try switching the jumper on the hdd to master, if thats a backed fix, it worked for me. jus another hit for searches.

---

