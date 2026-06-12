---
title: "Browsers causing system instability?"
date: 2007-07-08
forum: General Help
---

### Post by fragility14 on 2007-07-08
I've been having some instability problems, that generally seem to be related to browsers but cause the whole system to get slowed down a lot. This happens with Firefox, Swiftfox, Opera, Epiphany etc. I am having some other scattered problems.

Beryl is on but effects are turned down and doing things which involve beryl is never what causes a problem. I installed ubuntu for the first time and did so in a haphazard fashion software wise, I am ready to reformat and start over in a more coherent fashion, but am wondering if someone has a solution for browsers causing system instability.

(my computer is plenty fast to run browsers fine, I use an ubuntu computer at work sometimes that has significantly lower specs than this computer and runs more quickly and without problems)

---

### Post by AlexThomson_NZ on 2007-07-08
Might be some other process in the background slowing it down.

Open a terminal and run 'top'.  Keep an eye on it as you open browsers and play around.

I wouldn't think browsers could cause a system instability like that, but I have seen it myself (for some reason expanding threads on Digg temporarily locks my system up!)  Is it a particular site, or just when the borwser loads?

---

### Post by hikaricore on 2007-07-08
Keep in mind, it could be an issue with your video drivers or plug ins you're using.
The Linux versions of flash are notorious for causing problems.

What type of video card/drivers are you using?

---

### Post by fragility14 on 2007-07-08
xorg is using 99% of the cpu when it stops like that...swift fox loading the home page at myspace took 30-60%


a lot of the time it is xorg, but wth something like ronpaulnation.com/tv or youtube it uses around 95% of the CPU for swift fox. Yet, generally less than half of my ram is used...any way to make it use the processor less and ram more? (the videos skip and right now this text isnt typing smoothly because of a window running a youtube video in the background)

btw this is a centrino 1.5 with 1024 DDR333 ram (been extensively tested), and a 64 mb on board graphics card.

I'm all about checking the integrity of my hardware, Toshiba doesnt release a hard drive integrity checker, is there a good one you could direct me to?
edit: I'm using an Intel 855GM with the drive agpgart-intel


I'm very concerned my processor is going bad, the terminal also takes a long time to show my user information and it uses 99% of the processor while doing that.

I also had a complete freeze from a browser today (it is VERY common for my browsers to have to end because they're not responding, but uncommon for the whole system to actually freeze fully like that, it hasnt done it since I replaced the battery which was going crazy.)

---

### Post by hikaricore on 2007-07-08
All around desktop slowdown like that is usually the fault of the intel drivers, it's especially bad with firefox and flash.

Check to see if you have direct rendering enabled:

```
glxinfo | grep rendering
```

If this returns no, search around the site for *intel direct rendering* there's a few guides on fixing this.

Also you may want to consider changing the line:

>     DefaultDepth    24

in the Screen section of your */etc/X11/xorg.conf* file to:

>     DefaultDepth    16

To edit xorg.conf you'll need to run:

```
gksudo gedit /ect/X11/xorg.conf
```

And edit it as sudo root.

After you edit and save this file, close all open applications and restart GDM with Ctrl+Alt+Backspace.

You'll be amazed how the little change in colour depth affects your GUI speed.

---

### Post by AlexThomson_NZ on 2007-07-08
Ahh good point hikaricore, 64mb GFX isn't much now browsers cache multiple tabs, etc.

---

### Post by fragility14 on 2007-07-08
direct rendering is already enabled and switching to 16 does not cause a performance increase.

How do I find out if my processor is bad? it seems to use 90+ % of it at some point during every few minutes it is being used, yet memory usage never spikes. Any way to make it use more memory and less cpu?

I may try kubuntu just to see if it happens to just go in a better fashion.

---

### Post by hikaricore on 2007-07-09
Kubuntu will not run any better that ubuntu as you'll just be switchng from gnome to kde...

Did you restart X after chaning to 16 bit colour?

---

### Post by fragility14 on 2007-07-09
Nothing is working to make such things better, i am going to reinstall in a more coherent fashion, I tried a Kubuntu live CD and feel more comfortable with it (well, except that I have gotten use to the Mac-OSXish feel of Ubuntu), and more of the programs I seem to have taken a fancy to are KDE native, not Gnome, I have heard repeatedly it is a better desktop environment. And Ubuntu has been giving me hell for reasons that no one seems to be able to explain...so time to try something new.

---

