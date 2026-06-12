---
title: "Wierdest firefox problem"
date: 2005-09-26
forum: General Help
---

### Post by jvictor on 2005-09-26
Hi 
I am not able to acess google from my firefox browser.

If i do a nslookup and give the ip add i am able to , but not by typing google.com or using the search extension at the right top !!

I just installed ubuntu 4.10 and upgraded to the latest version of firefox.

---

### Post by heimo on 2005-09-26
[quote=jvictor]
If i do a nslookup and give the ip add i am able to , but not by typing google.com or using the search extension at the right top !!

I just installed ubuntu 4.10 and upgraded to the latest version of firefox.[/quote]

Is there some reason you are using Warty and not Hoary (5.04)? Anyway, you could try to disable ipv6, change ipv6 to off in file /etc/modprobe.d/aliases and in firefox type: about:config in address bar and search for ipv6 and double click on network.dns.disableIPv6

---

### Post by jvictor on 2005-09-26
Thanks a tonne; it works. :) I'd liek to know the reason behind it though, google not liking ipv6 :). 
Well i just cant get hoary :) .. i tried downloadin a couple of times but the install fails... while copying some udeb from the cdrom :(

---

### Post by heimo on 2005-09-26
No idea what's wrong with ipv6, but you're definitely not first one with this problem.

You can also upgrade without CD, using Synaptic or apt-get. If you want to install from CD, you should probably check that the iso file you downloaded was ok (using md5sum) and then burn the image using low speed (4x or 8x max).
[https://wiki.ubuntu.com/VerifyIsoHowto](https://wiki.ubuntu.com/VerifyIsoHowto)
[https://wiki.ubuntu.com/HoaryUpgradeNotes](https://wiki.ubuntu.com/HoaryUpgradeNotes)

Oh, and BTW; shipit (link on front page of ubuntu.com) takes orders of free Breezy CDs. :)

---

### Post by jvictor on 2005-09-27
OK :) is there any way to upgrade to AMD 64 from intel install ? :rolleyes: I've an AMD 64 bit machine and am looking to get a 64 bit OS :) for it. So far ubuntu looks really good.. v clean , stable, fast, & unbloated. May consider to replace the whole xp system with ubuntu after a few more days of testing.. :razz:

I tried getting the iso using different methods from different sources the isos look fine when we check the md5 , but the install fails . i Use a cdRW and use a ne DVD writer (Sony) .  I also tried writing at different speeds .. no use though :( the install fails while copying jfsutils.udeb

---

