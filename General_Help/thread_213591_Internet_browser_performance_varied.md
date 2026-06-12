---
title: "Internet browser performance varied"
date: 2006-07-11
forum: General Help
---

### Post by AirRaven on 2006-07-11
I've been getting extremely erratic performance from my internet in Ubuntu since my last reinstall. Some pages take up to a hundred seconds to load in a browser, and others load instantly.

I'm running a 576k broadband connection over a wireless network, being accessed with an rt2500 wireless chipset. 

The last time I had this problem, I fixed it by setting up a static IP address and disabling ipv6 in /etc/modprobe.d/aliases (alias net-pf-10 off). I'm also using my ISP's DNS instead of my router.

The trouble is, with my current installation, I've done all this and I'm still getting latency issues.

EDIT: I'm also getting speeds of around 4000b/s (Not kb/s) in Synaptic and other package managers. 

Does anybody have any clue what could be causing this?

Previously my problem was solved in [this thread](http://www.ubuntuforums.org/showthread.php?t=181171). I've followed the instructions again to the letter (sans the advice about using my IP's DNS as a gateway, which simply breaks my internet connection), but I'm still having latency issues.

---

### Post by kb3hkg on 2006-07-11
has anything else changed since you reinstalled? especially since you are using wireless there are lots of things that can cause this, a good test is to see how it wors if plugged into router to help narrow down possible problems.

---

### Post by AirRaven on 2006-07-11
> **kb3hkg said:**
> has anything else changed since you reinstalled? especially since you are using wireless there are lots of things that can cause this, a good test is to see how it wors if plugged into router to help narrow down possible problems.

As far as I can tell, I've changed absolutely nothing since I last installed.

The only difference I can think of is that I installed with the Dapper Live Install CD instead of doing a dist-upgrade from Breezy, and that I'm not running on the K7 kernel and I've not got the Xubuntu/Kubuntu-desktop packages installed. That's the only difference there is.

I don't have access to the router- it's currently attached to my father's computer, and he's using it at the moment.

---

