---
title: "How do you work around not having Flash 8 or 9?"
date: 2006-11-24
forum: General Help
---

### Post by Roasted on 2006-11-24
How do you do it? I was going to try downloading IE7 and running it in wine with Flash 9 but I couldn't launch the exe. Said I didn't have permission even though when I went to properties/permissions I had full permissions on everything.

Any suggestions?

---

### Post by codejunkie on 2006-11-24
there is flash 9 support for Linux, although it is still in beta it still works pretty well. just search the forum for flash 9 and you should find tons of threads about where to find installing etc, just in case though here's the direct link to the files [http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html) you can also run the latest version of flash in Firefox through wine and it works pretty well also.

---

### Post by jocko on 2006-11-24
Why not install flash 9 for linux instead? Get it from the [adobe labs website]("http://labs.adobe.com/downloads/flashplayer9.html"). Download the .tar.gz file (click the link "download installer for linux"), unpack it and follow the instructions in the readme.txt file to install it. And you probably need to uninstall flash 7 first.

Good luck.

Edit: I'm typing too slowly, codejunkie beat me to it...

---

### Post by Roasted on 2006-11-24
Using Adobe's flash tester it says I only have 7 installed. I successfully moved the flash 9 plugin into the plugins folder using the sudo mv command in terminal.

Now when I was in /usr/lib/ I noticed I have "mozilla" and "mozilla-firefox". Is this maybe why I'm not getting the results from flash 9, because it should be in the mozilla-firefox folder instead?

---

### Post by Roasted on 2006-11-24
Well I just got it in with flash 9. But still I wonder why the hell it wouldn't work when I tried to manually do it. That kind of bugs me. Any ideas?

---

### Post by dmizer on 2006-11-24
because flash 9 is still beta, so when you manually install flash, it won't default to a beta, it defaults to flash 7 instead.

---

### Post by reclusivemonkey on 2006-11-24
> **Roasted said:**
> How do you do it? I was going to try downloading IE7 and running it in wine with Flash 9 but I couldn't launch the exe. Said I didn't have permission even though when I went to properties/permissions I had full permissions on everything.

Any suggestions?

How did you install with wine? Did you use this;

[http://www.tatanka.com.br/](http://www.tatanka.com.br/)

That's the best way to get IE working in Linux. Just install wine and cabextract with apt-get then run the script. I've not head of anyone having problems and it installs flash 9 as well. Very handy for those IE only sites.

---

### Post by Roasted on 2006-11-24
> **dmizer said:**
> because flash 9 is still beta, so when you manually install flash, it won't default to a beta, it defaults to flash 7 instead.

Interesting... But I wonder what the hell is the point of even ATTEMPTING to install it manually then? Why wouldn't Adobe's site be like here install Automatix 2 THEN flash! 

??

---

### Post by paulyche on 2006-11-24
The IE7 download does a *Windoes Genuine Advantage (WGA)* check. So I doubt you'd be able to install it in wine anyway.

---

### Post by codejunkie on 2006-11-25
Roasted

if your still having problems with it showing up as flash 7 after you installed the flash 9 beta, it may be because if you installed flash 7 through automatix or synaptic, it installs flash plugin in /usr/lib/firefox/plugins you need to delete the libflash.so and libflash.xpt files in there first then install flash 9, you also need to remove the **pluginreg.dat** file in your /home/yourusername/.mozilla/firefox folder and restart firefox before the new plugin will be registered correctly. 

hope this helps 

codejunkie

---

### Post by dmizer on 2006-11-25
> **Roasted said:**
> Interesting... But I wonder what the hell is the point of even ATTEMPTING to install it manually then? Why wouldn't Adobe's site be like here install Automatix 2 THEN flash! 

??
you find that reasonable?

automatix is a script designed specifically for ubuntu (it does not work in other versions of linux with the exception of mepis).  its purpose is to make all multimedia support (not just flash) quickly accessible to the ubuntu user.  it has absolutely zero connection or affiliation with either adobe flash, firefox, or ubuntu.  it is a completely independent project.

so first of all, the ubuntu writers can't tell you to use automatix because it's a scrip which can compromise the integrity of their system.

adobe can't tell you to use automatix because:
1) they probably don't even know it exsts
2) they would have no way of detecting that your operating system is ubuntu and therefore capable of using automatix.

firefox can't direct you to automatix for installing the flash plugin because:
1) firefox probably doesn't even know that automatix even exists.
2) firefox developers can't reccomend using something that can compromise the integrity of the firefox code.

the whole point here is that if you desire to run code which is still in beta development (flash 9 for linux), you will not have the luxury of the full features (read: adobe site integrated install) that go along with a stable and supported release.

---

