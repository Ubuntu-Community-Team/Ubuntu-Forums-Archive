---
title: "Using &quot;Apt-Get Install&quot; to see newer version of already installed dependancy"
date: 2014-12-07
forum: General Help
---

### Post by antiartist on 2014-12-07
Hey all;

I"m having issues with my Transmission 2.77 installation in that it crashes soon after starting with segfault error concerning libevent:
[HTML]Dec  4 08:14:45 HouseMedia kernel: [507375.714526] transmission-da[6763]: segfault at 10 ip 009f3e85 sp b77d6530 error 4 in libevent-2.0.so.5.0.1[9c5000+39000][/HTML]

The ubuntu repository seems to carry Libevent 2.0.10 and I see from their website ([http://libevent.org/](http://libevent.org/)) that 2.0.21 is the most current version.  Since I found some older posts regarding similar issues with Libevent crashes and the issue was resolved in a package update, I thought I'd try the same thing.  But when I compile the latest libevent (using reference from [https://help.ubuntu.com/community/CompilingTransmission](https://help.ubuntu.com/community/CompilingTransmission)), Apt-Get Install still wants to install Libevent 2.0-5 (2.0.10) as a missing dependency.  How do I get the system and/or Apt-get to recognize that a newer version of apt-get is already there?

I have [COLOR=#393939][FONT=arial]Ubuntu Linux 10.04.2[/FONT][/COLOR]

---

### Post by deadflowr on 2014-12-07
I think you'd want to compile it with checkinstall.
Which will create a binary package of the compile package and make the system know you have it.
References
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
and
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by Impavidus on 2014-12-07
Consider using a later version of Ubuntu. 10.04 server edition is getting near end of life, desktop edition already is. You packages may be in server edition, I don't know. Ubuntu 14.04 comes with Transmission 2.82 and libevent 2.0.21.

---

### Post by antiartist on 2014-12-19
I've been holding off on an upgrade past Ubuntu 10.04 because I rely on this box a little too much and just haven't had the time to do the upgrade (and inevitably put in a several hours of troubleshooting).  

I now have libevent2.0.21-stable installed (used checkinstall) so it shows up in synaptic.  I removed libevent2.0.5 and proceeded with trying to install Transmission again.  And again, I'm being prompted to install libevent2.0.5.  What am I overlooking!??!

---

### Post by Impavidus on 2014-12-20
You haven't had a few hours spare time in the past two years? Wow, you must be a very busy person. But keeping an end of life system running takes time fixing all kinds of issues, in the end more time than installing and tuning a supported release.

Maybe transmission depends on a specific version of libevent?

---

### Post by Yellow Pasque on 2014-12-20
Your transmission .deb probably depends on "libevent2.0-5" explicitly. You need to have a package with that name installed to use transmission. You could try using checkinstall to name your custom package similarly, but that seems like a really ugly hack and a recipe for apt version conflicts.

---

