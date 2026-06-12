---
title: "Firefox 1.0.7 Released!"
date: 2005-09-21
forum: General Help
---

### Post by bierpullen on 2005-09-21
Mozilla has released the official version of the newest firefox.
[http://www.mozilla.org/products/firefox/](http://www.mozilla.org/products/firefox/)

---

### Post by karuptdata on 2005-09-21
You should really try the beta version..its awesome cant wait for final release!!

---

### Post by treris on 2005-09-21
What I'd like to know is whether FF 1.0.7 is going to be implemented in the breezy repo's or the hoary backports for that matter, seeing that breezy is gonna come out in october and 1.0.7 is not a very big update and all.

---

### Post by Jonathan2007 on 2005-09-21
Well Neowin.net seems to make a big deal about 1.0.6 being susceptible to an exploit and it only deals with Unix/Linix systems. But maybe they were being a little biased (seeing how they are a Windows centric site) and it may not be as big of a deal as they make it out to be. Still I would like to see 1.0.7 backported into Hoary.

See [this](http://www.neowin.net/comments.php?id=30540) link for the article on Neowin.

---

### Post by matthew on 2005-09-21
Quick note before the upgrade: 1.0.7 will break your firefox extensions according to the release notes.
[http://www.mozilla.org/products/firefox/releases/1.0.7.html](http://www.mozilla.org/products/firefox/releases/1.0.7.html)

EDIT: see my comments below...obviously they won't all break.

---

### Post by linbetwin on 2005-09-21
I'm quoting from Panda Software's daily newsletter:

[I][INDENT]"Madrid, September 21, 2005 - The Mozilla Foundation has released a new
version of Firefox -1.0.7-, which all users of this browser are advised
to install, as it incorporates improvements and resolves several
vulnerabilities.

The security flaws resolve in the new version of Firefox include the
following: buffer overflow in the Hosts name process; prevention of 
URLs
filtered by external programs (only in Linux); blocking of Proxy
Auto-Config (PAC) script; and restore of the 
InstallTrigger.getVersion()
function.

At the time of writing this bulletin, the new version of Firefox was
only available in English. However, the rest of the languages this
browser supports are due to be released shortly."[/INDENT][/I]

---

### Post by installer on 2005-09-21
[QUOTE=matthew]Quick note before the upgrade: 1.0.7 will break your firefox extensions according to the release notes.
[http://www.mozilla.org/products/firefox/releases/1.0.7.html](http://www.mozilla.org/products/firefox/releases/1.0.7.html)[/QUOTE]

Well I have just installed it and my extensions (all I have is adblocker and mouse gestures) still work fine.

---

### Post by matthew on 2005-09-21
[QUOTE=installer]Well I have just installed it and my extensions (all I have is adblocker and mouse gestures) still work fine.[/QUOTE]
Cool. I'm glad yours worked out well. I was just repeating what the release notes were saying for the sake of those who use many extensions. It is likely that a lot of extensions will still work well, there's just no guarantee and apparrently several (sorry, no list) will break until the developers of those extensions update the code to adapt to the 1.0.7 changes. I should have been a little less absolute in my original statement, though.

EDIT: see my comments below

---

### Post by treris on 2005-09-22
is there some way to make the tar.gz package that firefox provides into a .deb package? because if you install a deb package at least it will show up in my synaptic and everything?

i'd like to upgrade to 1.0.7 but have had a lot problems with changing between the repo version and the mozilla version because my java runtime didnt work anymore

---

### Post by aysiu on 2005-09-22
I just did a sudo apt-get upgrade, and Firefox bumped up to 1.0.7 in Breezy.

---

### Post by treris on 2005-09-23
my synaptic is still only showing ff 1.0.6, what repo's do you have in your sources.list? obviously i'm missing one

---

### Post by kahping on 2005-09-23
nice! i guess i'll be updating my breezy tonight  :) 

breezy isn't out yet, so i guess it's still possible for the developers to upgrade to 1.0.7 if they think it's important enough of a fix. for hoary, they'd just backport the fixes to hoary's firefox but maintain the version number

kahping

EDIT:

[QUOTE=treris]my synaptic is still only showing ff 1.0.6, what repo's do you have in your sources.list? obviously i'm missing one[/QUOTE]

firefox is default browser for Ubuntu, so it should be in main. have you tried 

```
sudo apt-get update
``` 

then try updating your firefox, treris?

---

### Post by treris on 2005-09-23
actually i'm using synaptic to update my system, but I have reloaded my repo's a couple of times without firefox being any different, however, i'm not using the breezy repo's yet, is firefox 1.0.7 maybe only available in the breezy repo's?

since firefox is my default browser, and has been for about a year, i would sure like to get te update, maybe I'll just get the file from mozilla and install that one. it's easy enough to get that one installed but it just doesnt show up in synaptic and thats a pity

---

### Post by treris on 2005-09-23
never mind, tonight  version 1.0.7 showed up in my repo list en after I uninstalled version 1.0.6 the installation of 1.0.7 went like a charm, like always with synaptic, hahahahaha

---

### Post by matthew on 2005-09-23
Sorry for the potential FUD above as I noted what was in the release notes. I want to modify my earlier comments to include my current experience. I upgraded from the repos and these extensions work for me:

Forecastfox 0.8.1.1
Image Zoom 0.1.7
Image Toolbar 0.5
Feedview 0.9.7
Tabbrowser Preferences 1.2.7.1
ChromEdit 0.1.1.1
Nuke Anything Enhanced 0.5
CuteMenus - Crystal 0.4A1
Flashblock 1.2.9
openselectedlinks 2005.06.12
Adblock v.5 d2 * nightly 39

untested so far
MediaPlayerConnectivity 0.3.9
User Agent Switcher 0.6.7

---

