---
title: "How to change Compiz theme is Lubuntu?"
date: 2012-10-16
forum: General Help
---

### Post by SteveDeFacto on 2012-10-16
I've been looking all over for a compiz theme manager I can use in Lubuntu. I read somewhere that gnome-tweak-tool would work but it does not appear to have any effect. I know I can edit text files but is there not a simple manager I can use?

---

### Post by vasa1 on 2012-10-16
> **SteveDeFacto said:**
> I've been looking all over for a **compiz theme manager I can use in Lubuntu**. I read somewhere that gnome-tweak-tool would work but it does not appear to have any effect. I know I can edit text files but is there not a simple manager I can use?
Why do you want to use a "compiz theme manager" with Lubuntu?

---

### Post by CrusaderAD on 2012-10-16
Is there not a theme manager you can use? It's been a while since I used Lubuntu, but I think there's a theme or appearance manager. I believe you can install GTK themes to your .themes directory within your home directory and it will show up the in appearance manager for you to change the theme.

---

### Post by cortman on 2012-10-16
Lubuntu doesn't use compiz, it uses Openbox.
You should have lx-appearance installed by default. This takes care of GTK themes. For the window themes, you should also have obconf installed.

---

### Post by vasa1 on 2012-10-16
> **cortman said:**
> Lubuntu doesn't use compiz, it uses Openbox.
You should have lx-appearance installed by default. This takes care of GTK themes. For the window themes, you should also have obconf installed.
**lxappearance** handles both from what I can see. It's called up by clicking on **Customize Look and Feel** from Preferences or running **lxappearance** from a terminal. The gtk themes bit is under "Widget" and the window themes is under "Window Border".
(This is with Lubuntu 12.10.)

---

### Post by vasa1 on 2012-10-16
> **cortman said:**
> Lubuntu doesn't use compiz, it uses Openbox. ...
But YouTube has videos on how to install compiz on Lubuntu. I would have thought people using Lubuntu wouldn't be too keen on compiz but ...

---

### Post by NikTh on 2012-10-16
This might help : [Lubuntu Theming](https://help.ubuntu.com/community/Lubuntu/Theming)

---

### Post by cortman on 2012-10-16
> **vasa1 said:**
> But YouTube has videos on how to install compiz on Lubuntu. I would have thought people using Lubuntu wouldn't be too keen on compiz but ...

Assuming the OP is just using Lubuntu as it is and not trying to change WM's, he wouldn't be using compiz. If he installed compiz, it should have been part of the instructions to install compiz-config-manager.

> **vasa1 said:**
> lxappearance handles both from what I can see. It's called up by clicking on Customize Look and Feel from Preferences or running lxappearance from a terminal. The gtk themes bit is under "Widget" and the window themes is under "Window Border".
(This is with Lubuntu 12.10.)

Odd, I ran lxappearance on #! and all Ihave are Widget, Icon Theme, Mouse Cursor, and Other. I guess it must be different in Lubuntu.

---

### Post by NikTh on 2012-10-16
> **cortman said:**
> 
Odd, I ran lxappearance on #! and all Ihave are Widget, Icon Theme, Mouse Cursor, and Other. I guess it must be different in Lubuntu.

I think obconf  can be applied too ... both #! and Lubuntu.

---

### Post by nothingspecial on 2012-10-16
Maybe the op is after a compositing manager.

xcompmgr is a lightweight one that will allow you to run apps that require compositing.

---

### Post by cortman on 2012-10-16
> **nothingspecial said:**
> Maybe the op is after a compositing manager.

xcompmgr is a lightweight one that will allow you to run apps that require compositing.

+1 to this, xcompmgr is an excellent compositing solution.

---

### Post by SteveDeFacto on 2012-10-16
Well xcompmgr is an interesting alternative however I have other reasons for using compiz like the grid feature. I want to use the lxde desktop simply because it is more responsive than other desktop managers I've tried even with compiz. Lxappearance has no option to change the window theme.

---

### Post by vasa1 on 2012-10-16
@OP, which version of Lubuntu are you using? In both 12.04 and 12.10, lxappearance has a tab called "Window border" which allows changes to the Window Manager.
Also, are you running a full version of Lubuntu or is it assembled from parts? If it's the latter, maybe you left out something or installed something older?

@cortman, what is  "lxappearance on **#!**"?

---

### Post by cortman on 2012-10-16
> **vasa1 said:**
> @OP, which version of Lubuntu are you using? In both 12.04 and 12.10, lxappearance has a tab called "Window border" which allows changes to the Window Manager.
Also, are you running a full version of Lubuntu or is it assembled from parts? If it's the latter, maybe you left out something or installed something older?

@cortman, what is  "lxappearance on **#!**"?

I was referring to running the version of lxappearance that comes with [Crunchbang]("http://crunchbanglinux.org/") (!#), which according to dpkg is version 0.5.1-1crunch. The "crunch" part of the package name indicates that it's probably a remixed version for Crunchbang.

---

### Post by vasa1 on 2012-10-16
> **cortman said:**
> I was referring to running the version of lxappearance that comes with [Crunchbang]("http://crunchbanglinux.org/") (!#), which according to dpkg is version 0.5.1-1crunch. The "crunch" part of the package name indicates that it's probably a remixed version for Crunchbang.
Thanks for the clarification.

I hope OP provides more clues that may help but right now it seems to be a case of insufficient data.

---

### Post by SteveDeFacto on 2012-10-17
First off I am running Lubuntu 12.04. After sitting here scratching my head for about an hour trying to figure out why you guys have a window borders tab I finally figured it out. Lxappearance is running a plugin called lxappearance-obconf(openbox config). This plugin does not work while compiz is running and even if it did work it only changes openbox's window theme. I thought since lxappearance has an openbox plugin that it must have a compiz plug in. However, after searching for the last hour I can't seem to find one. So I'm back to square one...

---

### Post by SteveDeFacto on 2012-10-17
Alright, I don't believe there is a solution. The only way I could set the window theme was to run gnome-settings-daemon and gnome-tweak-tool. A less than ideal solution so I just gave up and went with emerald which does everything I need and far more than I'll ever need. heh

---

### Post by CrusaderAD on 2012-10-17
How do you like emerald? I've tried it a few times and found it disappointing and buggy.

---

### Post by SteveDeFacto on 2012-10-18
So far no problems other than it being an extra 25MBs of ram that does little more than give me flashing buttons and a theme manager. However, my desktop still runs much faster than it ever did when I used ubuntu and unity or mint and cinnamon. With the cairo dock and guake I have a pretty sweat setup so I'm not going to complain.

---

### Post by CrusaderAD on 2012-10-18
Nice, pop a screenshot up if you get a chance.

---

### Post by geovino on 2012-10-20
"xcompmgr is a lightweight one that will allow you to run apps that require compositing."

just installed xcompmgr. How does it create shadows on the windows edges?

can it also allow to scale windows in small version on the desktop?

running Lubuntu 12.10 64bit

---

### Post by SteveDeFacto on 2012-10-22
> **CrusaderAD said:**
> Nice, pop a screenshot up if you get a chance.

A couple days late but I figure even if you don't get to see it someone else may be interested. My epic setup only take up about 400MBs of RAM and if I do say so myself it's quite epic!

[http://i.imgur.com/V8gRn.jpg](http://i.imgur.com/V8gRn.jpg)

[http://i.imgur.com/VEwtO.jpg](http://i.imgur.com/VEwtO.jpg)

---

### Post by buckyaustin on 2012-10-22
Well done been a while since I have seen compiz emerald in work. Still looks amazing. Didn't even occur to me to use it on Lubuntu. Great idea thanks for posting this. I think I'm going to switch to Lubuntu from Kubuntu.

---

### Post by SteveDeFacto on 2012-10-22
> **buckyaustin said:**
> Well done been a while since I have seen compiz emerald in work. Still looks amazing. Didn't even occur to me to use it on Lubuntu. Great idea thanks for posting this. I think I'm going to switch to Lubuntu from Kubuntu.

Yes, it's very good! Snappy, beautiful, and feature rich! I also use Guake as a terminal and I made several other more complex modifications. I want to make my own ubuntu distribution because I am enjoying this set up so much but I have yet to figure out how because all the tools I tried crashed or just didn't work.

---

### Post by wildmanne39 on 2012-10-22
Hi, you can click on the link in my signature to a wiki I wrote on compiz that might help, but for the most part people do not use compiz with lubuntu.
Thanks

---

### Post by pqwoerituytrueiwoq on 2012-10-22
if you are referring to the title bars in compiz not following the set theme
```
sudo apt-get install dconf-tools;dconf-editor
```
browse to [FONT=Courier New]org.gnome.desktop.wm.preferences[/FONT] look at [FONT=Courier New]titlebar-font[/FONT] and [FONT=Courier New]theme[/FONT]

that is how i changed it on xubuntu

---

