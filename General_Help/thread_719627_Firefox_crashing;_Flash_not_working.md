---
title: "Firefox crashing; Flash not working"
date: 2008-03-09
forum: General Help
---

### Post by Syg on 2008-03-09
These are two separate problems.

The first and most important is that when I visit certain websites (i.e. myspace) the page half loads and then the entire screen becomes unresponsive - Firefox, Gnome, other windows, everything. I can't do anything other than move the mouse (the loading animation becomes frozen too). The only solution to this is do a hard reboot.

(This also seems to happen when I use the search bar, after suggestions are displayed.)

In my quest to fix the problem, I've removed Flash (which caused further problems; see below), disabled JavaScript and Java, removed various other plugins (including ubufox, xine and firebug) and reinstalled the Firefox package. I also was going to completely remove Firefox and install it again, but removing a package called 'ubuntu-desktop' doesn't seem like it would help (even though it's a metapackage).

[SOLVED]
The second problem is that now that I've removed flashplugin-nonfree, I can't get it back again. I can install it, but Firefox tells me that it's not there and embedded Flash doesn't get displayed.
[/SOLVED]

I've got a nasty feeling all this is to do with me using the x86_64 architecture - it's caused other problems before.

Using Ubuntu 7.10 x86_64, Firefox 2.0.0.12.

---

### Post by zvacet on 2008-03-09
Download flash from [here](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash) and follow instructions.Because you use 64 bit version it wil be better for you (you will probably get faster answer to your qurestions if you posted in [this](http://ubuntuforums.org/forumdisplay.php?f=134) subforum.

---

### Post by Syg on 2008-03-09
Flash is now working. After clicking around in Firefox a bit it asked me to choose from Adobe Flash and Gnash, but it said I had already installed flashplugin-nonfree. So I removed the package, clicked around in Firefox some more, and it eventually installed the package for me.

So that's one out of two problems solved. But Firefox still crashes a lot - 4 times in the past 30 minutes. Also, YouTube causes crashes as well (this was before Flash was installed as well as afterwards).

Is it worth me giving up on x86_64, burning 32-bit Gusty and installing that instead? I was thinking of doing it for Hardy anyway.

---

### Post by Syg on 2008-03-09
I've 'completely removed' Firefox and installed it again (by installing ubuntu-desktop, which included a load of stuff I don't want like ekiga, evolution, tomboy, etc.). This did absolutely nothing. When it says that it will remove all settings, it's complete rubbish, Firefox is exactly the same as before, settings, crashes and all.

I also tried using Epiphany instead, but it suffers from the same problem. Is this just Gecko being unstable? I can't even switch to Opera because it's 32-bit only (that and I hate Opera).

By the way, Songbird works absolutely perfectly on the web (besides being a very good music player), so I'm using that as my main browser at the moment.

---

