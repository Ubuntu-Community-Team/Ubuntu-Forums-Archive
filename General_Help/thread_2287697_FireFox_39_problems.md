---
title: "FireFox 39 problems"
date: 2015-07-21
forum: General Help
---

### Post by kellyvotrenom on 2015-07-21
Having a lot of problems with FF39 it seems. Much slower than before and much, much slower than Chrome - even in Safe Mode, even with different profiles. Occassionally crashes while browsing however Crash Reporter is initiated _everytime_ I close the browser. Occassionally unmounting and re-mounting external USB drives; Syslog shows drives being unmounted and re-mounted (this only happens when FF is open). Doesn't copy all my bookmarks in folders when exporting to HTML (JSON seems OK).


I have completely removed and reintalled from Synaptic - renamed .mozilla file and am still having problems.  Only started after either Cinnamon Desktop update or FF39 update (both happened about the same time).  Computer had been crashing frequently (black screen) before FF reinstall but that seems to have stopped with new installation.  However, crashing and crash reporter continues to occur.  I do not have these problems using Chrome or Chromium.


Is there something I missed in removing FF?  Right now I have switched to Chrome and Chromium for most of my web browsing but prefer FF


Kelly Votrenom


Ubuntu 14.04 (x86-64)
Cinnamon ver. 2.6.12
Linux Kernel 3.13.0-57
AMD II X1 945 proc
3.9 GiB memory
AMD Radeon HD 4650 Graphics Card

---

### Post by amoun on 2015-07-21
Trusty on 8 year old ASUS  900 . That's a 900Mhz celeron processor with 1Gb ram; 4 + 16 Gb ssd and Firefox 39 perfect.

---

### Post by kellyvotrenom on 2015-07-23
Good for you

---

### Post by MGrowl on 2015-07-23
I'm on trusty and use FF39 too, also already did an update concerning flash on it. I don't have any problems with it crashing. Although, the flash seems a bit messed up sometimes and slower than usual to load. Maybe you can use this for reference with FF39. 

Perhaps the problems are with cinnamon-desktop?

---

### Post by wildmanne39 on 2015-07-23
I had the crashing problem, I had to install pepper flash and a new shockwave then deacivate the old shockwave and it works great again.
With firefox you have to install the wrapper to because pepper flash is made for chrome originally.

---

### Post by kellyvotrenom on 2015-07-25
I found a post where someone installed FireFox developer edtion to alleviate the problem.  I tried it and it seems to working fine.


[http://paperforshare.blogspot.com/2014/11/how-to-install-mozilla-firefox-developer-edition-on-ubuntu-backtrack-debian-linuxmint.html](http://paperforshare.blogspot.com/2014/11/how-to-install-mozilla-firefox-developer-edition-on-ubuntu-backtrack-debian-linuxmint.html)

BTW, this seems to be a common problem with using the Pepper Flash  extension with FF39.  Other solutions have been to remove Pepper Flash  and FF and then re-install from the Mozilla site download, not the  Ubuntu repository.


Thanks for your replies.  I wanted to mark this solved but do not know how, instructions in the forum don't work

---

### Post by Vladlenin5000 on 2015-07-25
> **kellyvotrenom said:**
> Other solutions have been to remove Pepper Flash  and FF and then re-install from the Mozilla site download, not the  Ubuntu repository.

If you want to follow that route then the better way is to add the Firefox Dev (Aurora) PPA and simply do apt-get update/upgrade, you FF will immediately turn into the Dev version (41.0a2 as of today).
You can also download, extract and run it (any version) from the extracted folder but it won't be installed.

---

