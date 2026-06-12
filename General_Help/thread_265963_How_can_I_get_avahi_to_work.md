---
title: "How can I get avahi to work?"
date: 2006-09-26
forum: General Help
---

### Post by Kashirigi on 2006-09-26
So, avahi is supposed to be dead easy. Let's say I want to use banshee-daap, too.

So, here I go:

sudo aptitude install avahi-daemon avahi-discover avahi-utils libnss-mdns service-discovery-applet mdns-scan zeroconf banshee-daap 

(Let's assume I have banshee installed)

This should install avahi and my life will be easy.

In fact, for a day, it sort of worked. I could see something in avahi-discover. I could see music share names, but I could not see their contents. Now I have changed nothing, and now when I run avahi-discover, there is nothing. NOTHING! The box is completely empty.

avahi.org and every other place I have found have been pretty much completely useless in helping with avahi setup. This is giving me so much frustration I feel like pitching my computer out the window.](*,) 

Can anyone give me any suggestions, no matter how small?

---

### Post by armalite on 2007-02-06
Nice to see i'm not alone in this universe. 
Same problems here, avahi-discover window is empty, even though i have plenty of services running in my lan.
Anyway a good wiki or documentation to start with is really missing.

---

### Post by PatheticMoFo on 2007-02-15
yeah I had a similar problem, turned out I needed to add "mdns" to this file: /etc/nssswitch
you gotta look for the line that starts with

hosts:

and make sure mdns is amongst those, so it should look like this:

hosts:          files dns mdns

I'm no good at explaining stuff, so I hope someone understood that, 'cause it took me a long time and a lotta frustration to figure that one out. Also, one tutorial on avahi mentions it, and they might explain it in a clearer way (you haveta scroll down a bit in their how-to to where they mention it) [http://www.ubuntuforums.org/showthread.php?t=347019](http://www.ubuntuforums.org/showthread.php?t=347019)

---

