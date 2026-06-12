---
title: "XGL/Compiz Installation"
date: 2006-09-13
forum: General Help
---

### Post by mikesena on 2006-09-13
I know this has been asked a number of times, but i can't find where, or any that help me.

I have installed this before and had it working, but i removed it because it was too unstable.  i'd like to try it again.

can anyone please tell me of an easy installation script (preferable) for installing compiz, that suits Intel graphics card, not just nvidia or ati?

Or, if there isn't one, a decent, working guide on how to get it installed?  I've tried a few, but i can't find the one i used originally.

thanks

---

### Post by viciouslime on 2006-09-13
[https://help.ubuntu.com/community/CompositeManager/]("https://help.ubuntu.com/community/CompositeManager/")

best guide there is in my opinion. Read that page to decide whether you want Xgl or aiglx then click the relevant link for instructions on how to install either of those. Then, once you have installed those, follow the link for how to install compiz. Easy peasy :)

---

### Post by scratched on 2006-09-13
I had the same instability problem using xgl on my intel graphics card. I switched to aiglx and I've never had a crash since. It works great on intel cards. Here is the post that walks you through the installation:
[URL="http://www.ubuntuforums.org/showthread.php?t=244559"]http://www.ubuntuforums.org/showthread.php?t=244559
[/URL]

Unfortunately no one has created an install script for aiglx/compiz, but the step by step on that thread is pretty simple and basic to understand. You should be able to get it working if you follow the instructions on that thread exactly.

---

### Post by Circus-Killer on 2006-09-13
you can do as the previous poster said, but imho, xgl/compiz is not ready to be used, even as an unstable package. its still got a loooong way to go.

---

### Post by mdeltito on 2006-09-13
> **Circus-Killer said:**
> you can do as the previous poster said, but imho, xgl/compiz is not ready to be used, even as an unstable package. its still got a loooong way to go.

I wouldn't say it is not ready to be used. On a faster machine it flies and looks great, i have it running fairly well as my default environment and i have no issues. Now if your talking compatibility, thats another story...

---

### Post by kalbir on 2006-09-13
This guide:

[http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card](http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card)

got aiglx/compiz working for me perfectly on an Intel i810 card. I tried to get Xgl up and running but it caused me lots of headaches- with aiglx I haven't had a crash so far (been running it for a week now).

---

### Post by wislon on 2006-09-13
One thing that does help with this is 'compiz-manager' (I had to apt-get install it).

I'd been having some problems with switching between cgwd and gnome-window-decorator, but this seems to have solved a couple of my problems. I am going to be testing the switching  between window managers and window decorators over the next few days, and have my fingers crossed! :)

---

### Post by beerorkid on 2006-09-13
automatix bleeder is the easiest way I know of.
[getautomatix.com](http://www.getautomatix.com/)

and compiz-manager is awesome. it is so nice to see this comming along so nicely.  make sure to install compiz-manager and start off in a normal gnome session.  Then enter compiz-manager to start XGL/compiz.

---

### Post by mikesena on 2006-09-13
i can't use the automatix bleeder, because i don't have ati or nvidea graphics card

---

### Post by beerorkid on 2006-09-13
ahhhh....  sometimes I do not read the origional post well enough.  Srry.

I have a severely low end ATI card on my laptop and have not gotten it to work yet (have not tried to hard actually)

I read in some post that the AGLIX? is a better option for intel and slower cards.

how pittiful, I host some of the compiz packages, yet know so little about it ;)

---

