---
title: "Firefox 3 beta 5: Shockwave player won't load"
date: 2008-05-14
forum: General Help
---

### Post by dx7r on 2008-05-14
Hello I apologize in advance if this is the wrong section to post this topic as I have just recently joined these forums.

I have started using ubuntu 8.04 Hardy Heron for about 2-3 weeks now and I have recently found a problem with the new firefox 3 browser. When I access some sites that use the shockwave flash player (swf files), the player doesn't even load and all i get is a huge blank white space where the player should be. I'm able to see the player for a split second when its loading the page but it quickly dissappears. Important thing to note is that these sites were sites that I would visit back when I was using firefox 2 and they worked just fine. I dl a ff2 binary and checked it out and the player works fine when I'm using it, however when I'm on ff3(the default browser on my system) the players don't appear. Other websites like youtube work fine but here are two notable sites where the problem occurs:

[http://www.revver.com/]("http://www.revver.com/")
and
[http://www.crunchyroll.com/]("http://www.crunchyroll.com/")

Also another thing to note is I have asked my friend who also is using the current Ubuntu 8.04 if he has this problem and apparently he does as well.

I would greatly appreciate any help in at least identifying the cause of the problem.

---

### Post by PmDematagoda on 2008-05-14
It seems to work properly on my Firefox 3, did you try reinstalling the Flash player?

---

### Post by alexandremrj on 2008-05-14
Open synaptic (System - Administration - Synaptic) and search for flash.

See what kind of flash you are using.

The open source flash sometimes doesn't work with some sites so you may have to remove the open source plugin and install adobe one.

P.S: If you have questions about this ask first before doing anything, I'm assuming you know a bit about synaptic

---

### Post by dx7r on 2008-05-14
I have tried reinstalling the adobe flash via synaptic but still no luck.As for it being the opensource version I don't know how to check it but the description of the package says that the plugin is downloaded from the adobe site and the name of the version is "9.0.124.0ubuntu2".

---

### Post by Baul on 2008-05-14
I was also having problems with flash - mostly due to having AMD 64 x2 CPU but found the two links below very helpful in fixing the problem.  Hope they are of use!

[http://ubuntuforums.org/showthread.php?t=476924&highlight=Flash+player+problem](http://ubuntuforums.org/showthread.php?t=476924&highlight=Flash+player+problem)

and more recent version

[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by dx7r on 2008-05-14
@ Baul 

Thanks for the links but it seems that fix is for 64 bit processors mine is 32 bit (there's no "ml" flag in the cpuinfo and I have i686 on my uname -a output). So I'm not so sure whether or not if I should try it out let alone if it will work.

---

### Post by dx7r on 2008-06-17
Okay I found out the problem pretty much using the old "adblock" add on for the browser was causing the flash players to not load instead I just upgraded to the "adblock plus" everything seems to be working fine now.

---

### Post by rockstarrem on 2008-06-17
I'm glad to see everything is working but in case anyone was wondering there is a possible sound problem that can be easily fixed. All you need to do is install libflashsupport and restart your computer and you should be fine, I did a few other random things so I'm not positive this is the exact case but it's worth a try!

---

### Post by ducunee on 2008-07-02
Simular problem display site [mycokerewards.com]("mycokerewards.com")
Adobe flash player installed Using totem to open swf files get message 
GStreamer error from support library.

---

