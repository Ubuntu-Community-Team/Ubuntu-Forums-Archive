---
title: "Intel(R) PRO/Wireless 3945 &amp; Dl-524"
date: 2007-09-14
forum: General Help
---

### Post by Vevmesteren on 2007-09-14
Good morning Friends, 
I have since some time now, the most annoying problem when connecting to my own network. 

I am running on a DELL XPS M1210. The wireless card and browser are stated in the subject of this post. Essentially everytime I start up my computer keeps one connecting and disconnecting to the router. This goes one for quite sometime anything between 3 and 20 times until finally a connection is maintained. The connection is made then dropped shortly after. I have turned off all network security. Something else that I noticed is that the connection light is not actually constant but blinking slightly, just a tad though, even when the connection is made. The wildest thing, when I connect to my neighbours network, all is well, the connection stays on on first connection...

any ideas. I am thinking that my router must be the problem, but my wifes OSX computert connects no problem, so does my Laptop when booted in WIndows...

thanks

V

---

### Post by mcduck on 2007-09-14
I have the exact same wireless card on my laptop (Asus A6Ja) and the same wireless router, and no problems. On my laptop the connection light blinks a bit when some data is transferred through the wireless network.

Also, I'm using the Network Manager to handle the connection, so it doesn't actually connect until I log into Gnome first time after boot (as the network keys are handled by Gnome's Keyring Manager).

Probably this wasn't really helpful, but at least you know that everything _should_ work fine with the hardware you have.. ;)

---

### Post by odin1965 on 2007-09-16
You seem to be a victim of the ipw3945 bug. While this card works very well for some, for others, it is very flaky. mine worked perfectly at first, then acted up, now doesn't work at all.  There is a bug, either in the kernel , or in the current ipw3945 driver which seem to cause many, many different symptoms.
[http://ubuntuforums.org/showthread.php?t=530352](http://ubuntuforums.org/showthread.php?t=530352)
[http://ubuntuforums.org/showthread.php?t=533331](http://ubuntuforums.org/showthread.php?t=533331)
[http://ubuntuforums.org/showthread.php?t=525152](http://ubuntuforums.org/showthread.php?t=525152)
[http://ubuntuforums.org/search.php?searchid=27234705](http://ubuntuforums.org/search.php?searchid=27234705)

There are also many bug reports on Launchpad;
[https://bugs.launchpad.net/bugs/+bugs?field.searchtext=ipw3945&orderby=-datecreated&search=Search&field.status%3Alist=New&field.status%3Alist=Incomplete&field.status%3Alist=Confirmed&field.status%3Alist=Triaged&field.status%3Alist=In+Progress&field.status%3Alist=Fix+Committed&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/bugs/+bugs?field.searchtext=ipw3945&orderby=-datecreated&search=Search&field.status%3Alist=New&field.status%3Alist=Incomplete&field.status%3Alist=Confirmed&field.status%3Alist=Triaged&field.status%3Alist=In+Progress&field.status%3Alist=Fix+Committed&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

---

