---
title: "Help with games"
date: 2007-08-06
forum: General Help
---

### Post by thekingof7 on 2007-08-06
So heres my tale of woe, I bought a second-hand laptop, a Dell inspiron 600m, I had read reviews that most distros had a nice time with it, including ubuntu. So I repartitioned my hd and set aside some space for Kubuntu (I prefer KDE) so I am am currently dual-booting XP and Kubuntu Fiesty Fawn. My only problem with Fiesty is that I cannot play any FPS on it. Even though the same ones run perfectly on XP. I have tried for about a month now to get the correct drivers configured but nothing works. I am sick of reconfiguring my Xorg ever day. I will upload my configuration. Please have a look.

---

### Post by roncrump on 2007-08-06
> **thekingof7 said:**
> My only problem with Fiesty is that I cannot play any FPS on it. Even though the same ones run perfectly on XP.

Sorry to ask a silly question but what is an FPS?

One of the multitude of things I came up with on google was First Person Shooter.

If so, are you trying to run a game written for windows XP in Feisty?

This would require emulation - wine might do the job - or virtualisation (running XP within Ubuntu).

Ron.

---

### Post by thekingof7 on 2007-08-06
Well as crazy as this may seem, if you had done a bit more reading you would've found out that FPS (and thats first person shooters) are somtimes open source, and quite frequently when something is open source it is multi-platform. So no I am not trying to run a windows game in Linux, I think I would have encountered some more serious problems other than poor graphics performance, if I tried to run a windows game.

---

### Post by Mblackwell on 2007-08-06
Be nice.

Also, are you running Compiz?

---

### Post by thekingof7 on 2007-08-06
Sorry about that, its kinda late. And no I am not running compiz, in fact I'm pretty sure I couldn't run compiz that well, in my current graphics state.

---

### Post by thekingof7 on 2007-08-06
any theories?

---

### Post by bodhi.zazen on 2007-08-06
Pleas use a more descriptive term for your threads.

[http://gaming.gwos.org/news.php](http://gaming.gwos.org/news.php)

---

### Post by PendragonUK on 2007-08-06
This is what I have managed to get going... and more to the point how.

Valve's Steam. That means Half Life with all of the regular mods like Counter Strike, Day of Defeat, all of the Half Life One games. Also Half Life 2 and all of it's addon's Counter Strike Source, Day of Defeat Source. In other words the whole Valve back catalog. 

I'm not great with the command line so I never bothered with trying to get Win Games to run on ubuntu but when I found WineDoors everything changed.

WineDoors allows you to install things really easily.

More to the point what do you expect to get running on a laptop??? I mean my gaming rig runs HL2 very nicely but with 2G of RAM and an nVidia 7900 it should do. You would be hard pushed to run HL2 on a laptop wouldn't you???

Anyhow there are a couple of good Linux games that you can run. Also several Win Games that can run on Linux natively. Doom III UnrealT and the up and coming ET:Quake Wars but that won't run on a laptop either...

---

### Post by thekingof7 on 2007-08-06
Listen I know its not a hardware issue, its a graphics issue, and I'm not doing any emulation. The game I am really trying to play is Urban Terror, which runs fine on the same machine running windows. The game is written for both platforms. In fact I;m pretty sure Linux was the original system it was coded for. :guitar::guitar::guitar::guitar::guitar::guitar::guitar::popcorn:

---

### Post by thekingof7 on 2007-08-06
Bump

---

### Post by soxs on 2007-08-07
plx post the output of the comand:
```
fglrxinfo
``` & ```
glxinfo|grep rendering
```
What graphics accelerator do you use?
What did you do so far?

Edit: i had a look at your xorg.conf (it should be xorg.conf and not Xorg.doc), and it seems that you simply did not install any graphics driver or something went wrong while installing.
So, plx tell us, what ati mobility does your laptop have?

---

### Post by thekingof7 on 2007-08-07
fglrxinfo

display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.2

glxinfo|grep rendering

direct rendering: No

It is an ati mobiblty 9000 (R250 I'm pretty sure)

---

### Post by Frak on 2007-08-07
You can't run most 3D games without direct rendering.
You may need to install the Proprietary ATi driver from the restricted driver manager. (System->Administration->Restricted Drivers Manager)

Oh and Wine is a compatability layer, not emulation, there is a HUGE difference.

---

### Post by soxs on 2007-08-07
Do as Frak said and try installing the ati-xorg-driver via "System->Administration->Restricted Drivers Manager"

If this failes more than 2 times(do not forget to reboot and check via fglrxinfo / glxinfo... if your driver is installed correctly), read this wiki/howto:
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

---

### Post by dragonwings on 2007-08-07
to get he latest driver 

sudo aptitude install nvidia-glx-new

---

### Post by thekingof7 on 2007-08-07
Im not really sure, how to access the "Restricted Drivers Maanger" due to the fact that I am using Kubuntu (KDE) instead of just GNOME. Any thoughts? And btw can people please stop detracting from the thread by mentioning WINE or other forms of gaming, I am just referring to my graphics issue, and I thought I would give everyone a point of reference by mentioning one of my goals. Everyone get off the subject of gaming and emulation/compatibility layering .

---

### Post by Frak on 2007-08-07
I'm sorry, instead you could use either the command above by dragonwings, or you could use envy scripts. Both work just fine.

---

### Post by thekingof7 on 2007-08-07
sudo aptitude install nvidia-glx-new????

i believe I have an ATI card.

---

### Post by Frak on 2007-08-07
My bad, didn't see that.
```
sudo aptitude install xorg-driver-fglrx
```
And after its installed, press Ctrl+Alt+Backspace, and it should work.

---

### Post by thekingof7 on 2007-08-07
According to Aptitude and Apt-get "xorg-driver-fglrx" has already been installed. This isnt being very easy is it?

---

### Post by thekingof7 on 2007-08-07
cmon guys I know there are knowledgeable people here. Would one of them please give me some help.

---

### Post by Frak on 2007-08-07
You could try [envy]("http://albertomilone.com/nvidia_scripts1.html") scripts.
[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu6_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu6_all.deb)
The install may fail, if it does just run in the terminal:
```
sudo apt-get -f install
```
And then goto
K->System (Could be utilities)->envy
And choose to install ATi drivers.
Also, if you boot up and it says X is broken.
Boot into safe mode and type
envy -t
and tell it to install ATi drivers. (which is option 3)
If it asks you to automatically configure X server, click yes, in the terminal, hit y
And if it asks you to reboot, reboot.

---

### Post by thekingof7 on 2007-08-07
Again no, good, keeps giving me crap about missing drivers. So I keep having to reconfigure the xserver.

---

### Post by Frak on 2007-08-07
Did you reinstall the drivers via the commandline?

---

### Post by thekingof7 on 2007-08-07
Explain?

---

### Post by Frak on 2007-08-07
when to booted, did it say drivers were not found and X was broken.
If it did, run
```
envy -t
```

---

### Post by PendragonUK on 2007-08-08
Grrr no delete option on this forum... Please disregard. 

Moderator please delete this post, thank you.

---

### Post by EXCiD3 on 2007-08-08
> **Frak said:**
> when to booted, did it say drivers were not found and X was broken.
If it did, run
```
envy -t
```

You may have to install the drivers through the "manual" section of envy, sometimes i have had to install the driver 3 times before it would work correctly.

---

### Post by thekingof7 on 2007-08-08
Yeah, the envy script are not working sadly. Same error each time, I am at my wirs end trying to find a solution.

---

### Post by Frak on 2007-08-08
Would you please post the error?

---

### Post by thekingof7 on 2007-08-08
told me that "EE No drivers found"

---

### Post by thekingof7 on 2007-08-09
Well I just used the open source ATI driver method, it has improved my graphics performance, but apparently the card that I have (radeon 9000) has a bug that doesn't allow for correct 3d rendering with any of the current drivers. this issue is supposedly being addressed right now. So I guess I'll just have to wait. 
Thanks for the help.

---

### Post by Frak on 2007-08-09
Unfortunately, the Open Source, community driven, drivers are better than the ATi drivers.
Thats just sorry of ATi.

---

