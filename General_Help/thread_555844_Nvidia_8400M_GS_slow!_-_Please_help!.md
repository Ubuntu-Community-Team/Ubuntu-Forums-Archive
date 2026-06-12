---
title: "Nvidia 8400M GS slow! - Please help!"
date: 2007-09-20
forum: General Help
---

### Post by meuge on 2007-09-20
Hi

After trying to get the 8400M GS working on my friend's Dell 1520, I finally used Envy, which successfully installed the nvidia binary drivers. 

However... now the entire desktop experience is PAINFULLY slow - it takes >1 second to switch between tabs in Firefox... or 2-3s to minimize a window. This is partially remedied when I use Metacity as opposed to Beryl or Compiz, but it's still slower than when using the Vesa driver. 

Please help!

---

### Post by meuge on 2007-09-20
*bump

please help - getting pretty desperate here...

---

### Post by GnarusLeo on 2007-09-24
I can confirm this. Nvidia 8400m GS on a Acer Aspire 5720ZG. 

Compiz is deffinatly so slow, I can even use it. Are we missing something? Please re-post if you have a sollution. Anyone to help?

---

### Post by jmccarthy14 on 2007-09-24
I'm running m1330 with santa rosa 2ghz core 2, 2gb ram, 7200rpm hd, yet with the 8400m compiz runs slower on my machine than a friend who just bought a 300$$ laptop with an ATI.  what gives?

---

### Post by syxbit on 2007-09-24
i have a Lenovo Thinkpad T61 with a Quadro 140M (the same as a GeForce 8400.
performance isn't great, but it's not as bad as you're claiming (as least with the latest nVidia driver) 
btw. i'm running gutsy, so this might be fixed for you all when you upgrade next month.

---

### Post by syxbit on 2007-09-24
run this in the terminal
```
cat /etc/X11/xorg.conf |grep Driver

```
it should show which driver you're using at the bottom (hopefully nVidia)

---

### Post by jmccarthy14 on 2007-09-24
mine isn't slow, but if i do somet hings like 'show desktop' the window slides very slowly/laggily across to the corner, and if i dont move the cube for a minute or so, when i go to move it it lags the first time.  then once i let go and re-grab the cube, everything is as fast as i could want, but the first time it slows down.  wabbly windows seem kindof slower too so i'm wondering why its the rendering of these windows

i am using nvidia10xxxxx i use gentoo now but used to use ubuntu and this forumn is the only one that had a geforce 8400m related compiz problem

again not slow but somet hings are choppy.  why? on a nice graphics card.

i have only triplebuffer enabled, allowglxwithcomposite(or add, i forget), and renderaccel

---

### Post by jmccarthy14 on 2007-10-02
Alright.  Switching tabs in firefox is still kindof slow, but minimizing/general window use and compiz has sped up to more than usable with the settings attached in my xorg.conf, and Also a major improvement when you turn off 'detect refresh rate' and then set the refresh rate very high manually within compiz.  Also, if this doesn't help there are a few tweaks to the actual nvidia driver that can be made, but these should do the most aid.
(you can uncomment render and allowglx if you wish, i've just gotten the best results with this setup, but they may help you).

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1280x800 +0+0; 800x600 +0+0; 640x480 +0+0"
    Option         "RenderAccel" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
#    Option         "AllowGLXWithComposite" "True"
    Option	   "TripleBuffer" "True"
    Option	   "NvAGP" "0"
Option "DamageEvents" "True"
Option "BackingStore" "True" 
#Option "UseEvents" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
Option "DAMAGE" "Enable"
Option "Composite" "True"
#Option "RENDER" "Enable"
EndSection

---

### Post by taqtikat on 2007-10-05
> **jmccarthy14 said:**
> mine isn't slow, but if i do somet hings like 'show desktop' the window slides very slowly/laggily across to the corner, and if i dont move the cube for a minute or so, when i go to move it it lags the first time.  then once i let go and re-grab the cube, everything is as fast as i could want, but the first time it slows down.  wabbly windows seem kindof slower too so i'm wondering why its the rendering of these windows

i am using nvidia10xxxxx i use gentoo now but used to use ubuntu and this forumn is the only one that had a geforce 8400m related compiz problem

again not slow but somet hings are choppy.  why? on a nice graphics card.

i have only triplebuffer enabled, allowglxwithcomposite(or add, i forget), and renderaccel

Im having the same problem on 8400M G. It seems that this applies to all effects in compiz. When it has been unused for a while it takes some time for the effects to get "up to speed". I think this is why the wobbly is almost always kinda slow..

Did you find what the problem with the "slow start" was? Does anyone else have a solution?

I'm using gutsy by the way.

---

### Post by strigare on 2007-10-13
See what happens when you use compiz but disconnect emerald. I had all of this problems, but switching to GTK-Window-Decorator "fixed" them

---

### Post by starcannon on 2007-10-13
I'm having performance problems on an HP Pavilion 2600dv Notebook with the 8400m GS card as well, I tried those xorg.conf mods with minor improvement (thanks btw :) ) 
Disabling Emerald helped alot to (thanks alot for that one to :) )
But performance is still not great.
Those mods fixed the lag I experienced with maximize and minimize animations, however, open and close animations are choppy, particularly my favorite burn up and burn down animation. I have noticed burn down which I set to closing a window seems to work well about half the time, burn up which I have set for new windows is always choppy.

---

### Post by quadm on 2007-10-22
Has this issue been resolved since the gutsy release? (Im considering upgrading my laptop from a vaio sz480 (geforce go 7400) to a sz680 (geforce go 8400) mainly for the graphics boost with compiz. would not be worth it if its not gonna make a difference!)

thanks.

---

### Post by theophane on 2007-10-27
> **taqtikat said:**
> Im having the same problem on 8400M G. It seems that this applies to all effects in compiz. When it has been unused for a while it takes some time for the effects to get "up to speed". I think this is why the wobbly is almost always kinda slow..

Did you find what the problem with the "slow start" was? Does anyone else have a solution?

I'm using gutsy by the way.

I'm having the same problem. Did you have this solved ?
I'm kinda pissed, cause this graphic card is part of the reason I purchased my Aspire 7720G, I thought compiz fusion would be kickass, which is not the case.

Cheers

---

### Post by zach382 on 2007-10-28
This problem seems to still not have been resolved. I am running the final gutsy with compiz fusion and things are still laggy one the effects haven't been used for a while. I would like to know if there is a permanent fix not just a hacked workaround.

---

### Post by theophane on 2007-11-01
Hi folks !

Has any of you guys resolved this problem ?

I've posted something on the official Nvidia forums : [http://www.nvnews.net/vbulletin/showthread.php?t=101161](http://www.nvnews.net/vbulletin/showthread.php?t=101161)

Feel free to post something too, so we can get some attention from nvidia.

---

### Post by bcrom on 2007-11-07
I am having the same problem.  This is very frustrating.  The worst part is the inconsistency of the lag.  Sometimes it runs very smooth and sometimes it will lag like crazy.

---

### Post by jespdj on 2007-11-07
I have a Dell XPS M1330 with nVidia 8400M GS running Gutsy and I have not noticed any problem with the speed of the graphics on the desktop. Switching tabs in Firefox is not slow at all.

When I installed Ubuntu, I got the message about the restricted driver for the video card being available and I enabled it, and it works without problems.

---

### Post by theophane on 2007-11-07
I still have this problem, and it's very annoying.
Here is a thread I wrote about this issue on the official nvidia forums : [http://www.nvnews.net/vbulletin/showthread.php?t=101161](http://www.nvnews.net/vbulletin/showthread.php?t=101161)

No official answer yet... :(

---

### Post by bcrom on 2007-11-08
I also have a Dell XPS m1330, and I do experience this problem.  It's strange that you don't jespdj.  Have you tried the fire or beam up animation effects?  That's where mine lags the most.

---

### Post by bcrom on 2007-11-08
Here is an explanation from the nvidia forums, and this makes a lot of sense:

> The card has two modes where it runs 2D and 3D (only difference is the clock used). To save power the card runs with the 2D clocks until you start a 3D applications. But it seems that in case of compiz the card does not go into 3D mode because its generally not needed and would waste power. ...it seems like the fire effect needs some gpu power to be smooth.

---

### Post by theophane on 2007-11-08
> **bcrom said:**
> Here is an explanation from the nvidia forums, and this makes a lot of sense:

I saw this, but I still think it is ********.
When I've practiced an effect for awhile and got into that "3D" mode, I still get globally low performances. I hope this will be fixed soon enough.

And by the way, what you are quoting is a member's post. **None of the Nvidia techies** have made a statement on this issue yet, which is what annoys me.

---

### Post by LML on 2007-11-08
> **bcrom said:**
> I also have a Dell XPS m1330, and I do experience this problem.  It's strange that you don't jespdj.  Have you tried the fire or beam up animation effects?  That's where mine lags the most.

On my Dell xps m1330 this fire plugin works great, but moving the cube (with enabeled transprency during rotation) is lagging using it the first time for a while.

---

### Post by Lukyan on 2007-11-19
I didn't have any kind of these problems with my 8400m GS, the only issue is some strange artifacts when I use Info for resizing plugin in Desktop Effects.

Do you know how to fix the problem? :KS

---

### Post by jobeirne on 2007-11-21
> **theophane said:**
> I'm having the same problem. Did you have this solved ?
I'm kinda pissed, cause this graphic card is part of the reason I purchased my Aspire 7720G, I thought compiz fusion would be kickass, which is not the case.

Cheers

I'm with you fellas. There's gotta be a fix. I had the same issue when I was using Vista for a while, and some attributed it to the card's driver idling the 2D/3D power until it was under considerable use. I'm fairly sure it's a driver issue. On my Vista partition, I'm using an older, hacked version of the nvidia driver (169.something?) and it woks considerably better than the current, up-to-date nvidia driver.

I'd love a fix for this. Once I get the thing 'sped up', compiz runs flawlessly.

---

### Post by theophane on 2007-11-21
> **jobeirne said:**
> I'm with you fellas. There's gotta be a fix. I had the same issue when I was using Vista for a while, and some attributed it to the card's driver idling the 2D/3D power until it was under considerable use. I'm fairly sure it's a driver issue. On my Vista partition, I'm using an older, hacked version of the nvidia driver (169.something?) and it woks considerably better than the current, up-to-date nvidia driver.

I'd love a fix for this. Once I get the thing 'sped up', compiz runs flawlessly.

I'm not running the Window OS at all, so I can't say. 
What I know is I still have this very annoying problem under Ubuntu 7.10.
I've read A LOT of threads regarding this issue on the web and we are not a few unlucky users. This problem seems to be recurrent on all -or at least on a lot of-  8400M GS cards.

No official statement from Nvidia yet, which is getting annoying.

Anyways, 

Rock'On  :-({|=

---

### Post by jespdj on 2007-11-21
> **bcrom said:**
> I also have a Dell XPS m1330, and I do experience this problem.  It's strange that you don't jespdj.  Have you tried the fire or beam up animation effects?  That's where mine lags the most.
Well, the Compiz effects sometimes are slow and laggy indeed also on my m1330: for example minimizing or un-minimizing windows isn't always going very smooth. But I've never experienced problems with switching tabs in Firefox.

The nVidia 8400M GS is not the fastest available graphics card, but it's not terribly slow either and it *should* easily be able to handle the Compiz effects. Most likely the problem is in the driver...

---

### Post by starcannon on 2007-11-22
HP Pavilion dv2600 here, 8400m gs, same problems, bought this configuration originally thinking I would be screamin' along. This thing doesn't really do any better than the pos onboard intel X3100. Guess it must be time to switch back to ATi, strange how ever so many years the leader will become complacent, and then another leader crawls to the top. Wonder if AMD/ATi will fall into the complacency trap like the old ATi, and now Nvidia have done.
Okay, Okay, /rant OFF all the same, crazy that I have a 6 series that out performs this 8 series.

---

### Post by dumplinknet on 2007-11-30
Has anyone found a way to fix this lag that the 8400M GS is causing?

---

### Post by mongo on 2007-12-02
I have the same problem. A solution would be more than welcome (switching between tabs in Firefox/Opera is driving me nuts).

---

### Post by bigbrovar on 2007-12-05
mehn i guess am screwed.. i use to use intel GMA on my last laptop then a friend said that compiz runs very well with nvidia .. so i sold my lappy and got this sony vaio that comes with nvidia 8400m gt now am hearing about all this slowness..grrrrhhh:confused:

---

### Post by starcannon on 2007-12-06
> **bigbrovar said:**
> mehn i guess am screwed.. i use to use intel GMA on my last laptop then a friend said that compiz runs very well with nvidia .. so i sold my lappy and got this sony vaio that comes with nvidia 8400m gt now am hearing about all this slowness..grrrrhhh:confused:

Hang in there though, Nvidia is good about getting drivers going, intel, well, not so much. So your still in good shape, we just have to wait for the 8 series linux drivers to get brought up to speed is all, I hate being patient, wish I could order laptops with a 7950gt in them, those rock on linux.

---

### Post by dumplinknet on 2007-12-14
has nvidia came out with drivers for the 8400M GS yet to improve linux? has anyone found a better way to improve the laggy-ness of this card?

---

### Post by theophane on 2007-12-15
> **dumplinknet said:**
> has nvidia came out with drivers for the 8400M GS yet to improve linux? has anyone found a better way to improve the laggy-ness of this card?

Nope, and this is driving me crazy. :mad:
I only use Linux and this is very annoying. I though everything would just be fine with an nvidia card, but obviously, this is not the case.

However I noticed on several forums that not all 8400M GS cards are affected by this problem, which is pretty weird.

What do you guys think of this ?

---

### Post by theophane on 2007-12-16
Hi !
I found a hack that worked for me. I found this on the official Nvidia forums.

Here it goes :

[QUOTE=Sayonara]try this:

in terminal run:
# while true; do nvidia-settings -q all > /dev/null; sleep 25; done

this seems to stick PowerMizer at maximal performance level
I have no time to track this down yet.

card: Quadro 1600M
driver: x86_64-169.04

watch out do not burning your gpu :)[/QUOTE]

Hope it will work for you :)

---

### Post by bigbrovar on 2007-12-24
> theophane  	
Re: Nvidia 8400M GS slow! - Please help!
Hi !
I found a hack that worked for me. I found this on the official Nvidia forums.

Here it goes :

Quote:
Originally Posted by Sayonara
try this:

in terminal run:
# while true; do nvidia-settings -q all > /dev/null; sleep 25; done

this seems to stick PowerMizer at maximal performance level
I have no time to track this down yet.

card: Quadro 1600M
driver: x86_64-169.04

watch out do not burning your gpu
Hope it will work for you 
i just tried what u suggested .. hope that i wont fry my cpu.. cus it a little scary

---

### Post by bigbrovar on 2007-12-24
mehn i tried it and after sometimes my screen just frooze nothing moved .. not even the cursor.. i was so embarrassing cus my windoze friends were there .. and there had a good laugh .. "so much for linux stability" :(

---

### Post by starcannon on 2007-12-24
Just installed the Dec. 20 2007 169.07 drivers and so far they are excellent, give those a go and see if that helps.

---

### Post by dumplinknet on 2007-12-26
has anyone else tried the new nvidia drivers (from the post above)? i wanna know how it is.
does it really help fix the lagg in the 8400M GS? seriously the only bad thing about the 8400M GS is that it lags on the first thing. for example, when you try to turn the cube, its very laggy the first time when you havent used it. but after about a minute of not using it, it becomes laggy again!!!! and switching between firefox tabs are SO SLOW. and what annoys me is the maximizing and minimizing is VERY LAGGY! 
**has anyone found if this driver works or not?**

---

### Post by bigbrovar on 2007-12-26
i think the driver works well and has corrected most of the lagging issues on compiz.. however the is a bug in the drivers that makes your system fan to over run

---

### Post by bigbrovar on 2007-12-26
by the way any body know how i can install the new driver .. i have downloaded it for nividia but its not a deb file the extension is a .run file and i dont know what to do

---

### Post by jespdj on 2007-12-26
Read [the instructions]("http://www.nvidia.com/object/linux_display_ia32_169.07.html") (step 3).

---

### Post by bigbrovar on 2007-12-26
i actually tried but i got an error about a dependencies problem so i couldnt proceed

---

### Post by FrankVdb on 2007-12-26
I don't get it. I have the Dell XPS M1330 as well (GeForce 8400 card) and I don't have any lag on that laptop. I'm running Gutsy on it with the restricted nVidia driver installed.

---

### Post by jespdj on 2007-12-29
> **bigbrovar said:**
> i actually tried but i got an error about a dependencies problem so i couldnt proceed
What dependencies problem? If you don't tell us the exact details then we can't help you solve the problem. Do you have a C compiler and the Linux kernel headers installed? If not, install them first:
```
sudo apt-get install build-essential linux-kernel-headers
```

I installed the newest driver (169.07) and I haven't used it for a long time yet, but the lag problem seems to be gone, and also the fan seems to blow less.

I had to disable the "nv" module, otherwise the new driver wouldn't initialize properly. I did that by editing /etc/default/linux-restricted-modules-common and adding "nv" to the line with DISABLED_MODULES.

---

### Post by theophane on 2008-01-02
These new drivers don't fix anything for me. I still have this annoying laggy thing :(

---

### Post by jespdj on 2008-01-02
Hmmm, after using it some more the lagging doesn't seem to have completely disappeared on my laptop either. My desktop PC (with 8600 GTS) doesn't have the problem at all.

However, the fan on my laptop really does seem to blow a lot less with the new driver.

---

### Post by dumplinknet on 2008-01-05
> **jespdj said:**
> [B]
I had to disable the "nv" module, otherwise the new driver wouldn't initialize properly. I did that by editing /etc/default/linux-restricted-modules-common and adding "nv" to the line with DISABLED_MODULES.[/B]

uhhh... can you tell me how to do that?

---

### Post by Nepherte on 2008-01-09
I have a Sony Vaio with an Nvidia 8400M GS as well and using the latest drivers still gives me very poor performance. Even with my on board Intel vga I get better real time performance (although glxgears gives me less fps). My problem is mainly hiding, restoring windows and alt+tab windows. It doesn't matter if I use compiz or not, the performance remains bad.

p.s. to install the latest nvidia drivers:
1. Download the latest drivers from their site

2. Stop the xserver: sudo /etc/init.d/gdm stop

3. Navigate to the directory where you downloaded the driver using the 'cd' command

4. Install them: sudo sh NVIDIA-Linux-x86-169.07.pkg1.run

5. Follow the onscreen instructions and restart x: sudo /etc/init.d/gdm start

---

### Post by matroska on 2008-02-17
I have the problem too with my new desktop with 8500 gt card.

A driver bug?

---

### Post by Mopana on 2008-02-29
I have gusty final; Nvidia 8400M on a new dell 1420 with nvidia driver. I had lots of lag which was especially noticeable in firefox tab switching. There was no difference in lag between compiz and metacity; however, when I maintain desktop effects with compiz but enable GTK Window Decorator instead of Emerald the lag nearly disappears.

---

### Post by lviggiani on 2008-04-21
Hi, I could fix the problem with my notebook (Dell XPS M1330 with GeForce 4800M GS) and my compiz run smooth now on Gusty.
This is what you should check:

1) The driver should be nvidia 169.12
2) Compiz should be run with the Indirect Rendering option (don't use "Loose Binding")
3) Compiz should be the one from Ubuntu repository 0.6.0
4) Use kde-window-decorator (or GTK Window Decorator if you're using GNOME) rather than emerald since series 8 GPUs seem having bad pixmap capabilities
5) In the xorg.conf I added :
    Option         "TripleBuffer" "True"
    Option         "BackingStore" "True"
(I don't know if it really helps)
6) CPU Scaling policy set to performance in the guidance-power-manager
7) You need to kill powermizer otherwise it will downclock your GPU after 15 seconds and the effects will not run smooth. To do so, I have improved a script from technomagik ( [http://ubuntu-utah.ubuntuforums.org/showthread.php?p=4758876#post4758876](http://ubuntu-utah.ubuntuforums.org/showthread.php?p=4758876#post4758876) ) so that it only activates when you're running with the AC power in, thus saving batteries. Just put it on your ~/.kde/Autostart folder and forget about powermizer!

```
#!/bin/bash
while true; do
	acon=`grep -o on /proc/acpi/ac_adapter/AC/state`
	if [ "$acon" == "on" ]; then
		nvidia-settings -q all > /dev/null;
	fi
sleep 10;
done
```

8 ) Reboot


I hope that this will help nVidia users.
If it helps (and if you like) please give me beans! :)

---

