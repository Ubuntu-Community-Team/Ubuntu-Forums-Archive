---
title: "Ubuntu 6.06: Why Firefox 1.5.0.9 and not 2.0.0.1?"
date: 2007-01-28
forum: General Help
---

### Post by Phrawm48 on 2007-01-28
Does anyone happen to know why Ubuntu 6.06 seems "locked into" Firefox 1.5.0.9 to the extent that one can't readily upgrade the system to Firefox 2.0.0.1?

I've installed F'fox 2 and am running it in addition to 1.5, but I'd rather make F'fox 2 my system default and remove 1.5 entirely.

However, as has been pointed out in other threads, removing 1.5 breaks things at the system level.  For example, Synaptic informs me that I'll break *gnome-app-install* and *yelp* if I uninstall Firefox 1.5.

More to the point, is there a straightforward way to tell Ubuntu 6.06 (2.6.15-27-386) to connect itself to and use Firefox 2 as its "total system default"?

Cheers & thanks,
Ric
SFO

---

### Post by Ramses de Norre on 2007-01-28
Those apps are build around firefox' Gecko engine so they can't work without it. And the ubuntu policy is to not update packages of a stable release except for security fixes to maintain stability.
Firefox 2 might hit the backports repo's but in either way it wont be officially supported.

---

### Post by cmost on 2007-01-28
Install swiftfox.  It's firefox 2.0.0.1 with some enhancements that speed it up.  I've used it in Dapper with great success.  You can do a search here to figure out how to install it.  The easiest way is to use Automatix2.  Enjoy!

---

### Post by aysiu on 2007-01-28
This script will help you install Firefox 2:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by tagginannie on 2007-01-28
> **Phrawm48 said:**
> Does anyone happen to know why Ubuntu 6.06 seems "locked into" Firefox 1.5.0.9 to the extent that one can't readily upgrade the system to Firefox 2.0.0.1?

I've installed F'fox 2 and am running it in addition to 1.5, but I'd rather make F'fox 2 my system default and remove 1.5 entirely.

However, as has been pointed out in other threads, removing 1.5 breaks things at the system level.  For example, Synaptic informs me that I'll break *gnome-app-install* and *yelp* if I uninstall Firefox 1.5.

More to the point, is there a straightforward way to tell Ubuntu 6.06 (2.6.15-27-386) to connect itself to and use Firefox 2 as its "total system default"?

Cheers & thanks,
Ric
SFO

Hi Ric,

Two really great tutorials on installing Firefox 2  **_[Installing Firefox on Ubuntu]("http://www.psychocats.net/ubuntu/firefox")_**
and [_**HowTo Install the Latest Firefox in Ubuntu (Ultimate HowTo)**_]("http://ubuntuforums.org/showthread.php?t=330386")

Suzy :KS

---

### Post by fragos on 2007-01-28
Truth is Firefox 1.5 is more stable than 2.0.  Which extensions and plugins you use has an impact on stability but, Firefox always seems to get blamed.  IMHO I see no reason for most users not to upgrade to Edgy.  Then you will have newer versions of many applications and system components.

---

### Post by f.l.u.f. on 2007-01-29
> **aysiu said:**
> This script will help you install Firefox 2:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Call me stupid, but I ran the script and it didn't seem to work.  Running Firefox from either command line or the link still brings up 1.5.0.9.  Of course I'm still trying to learn Linux and usually end up beating my head against the desk every time I try to do something other than surf the net.

---

### Post by f.l.u.f. on 2007-01-29
NM, started working on its own. :confused:

---

