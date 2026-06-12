---
title: "No ssh, samba or plex after update"
date: 2024-05-12
forum: General Help
---

### Post by unicav on 2024-05-12
I've been running Ubuntu server 22.04 without a hitch for months. Just did an update and now I can't access it at all.
At the console I have internet, I've updated and upgraded again. I can ping out. 
Firewall is not active.
sshd shows active and listening - can not connect from my PC it times out.
smbd shows active - can not connect to shares
plex can not connect.
ip a shows interfaces active
ip r shows static routes from the IP to the gateway.

I'm at a loss at this point

---

### Post by TheFu on 2024-05-12
Unlikely the issue is with the install.  None of my 22.04 systems (patched yesterday) have any network issues.

I'd suggest you try to ping by IP address other devices on the LAN and on the internet.  

If you cannot reach the internet, check your ISP, router and switch ports.
If you cannot reach any LAN computers/devices, check the cable and switch port THIS computer connects.

Looking at services happens first, but when so many aren't working, it is likely a bonehead hardware issue outside the computer.  The last thing to check is the NIC in the computer.  Try a different NIC and double check the drivers it is using. Did those change recently?  Does your 2nd or 3rd NIC connections into the server still work?  Try those.

---

### Post by unicav on 2024-05-12
I have tried ping from other devices I get nothing. I have tried access to ssh, shares and Plex from several devices. The reason I discovered it was inaccessible was because I was going to save a file to it and couldn't get in then I realized Plex was down. All my other devices are fine, no issues with Internet or network. The last thing I did the other night was run an update and let it reboot and go to bed. Didn't try to use it until yesterday and poof nothing

---

### Post by unicav on 2024-05-12
Found the problem. My TP-Link Deco router decided to change the entire LAN range for some reason so none of my static devices were working properly.

---

### Post by MAFoElffen on 2024-05-12
LOL. Dang. Hate when that happens.

Be sure to mark this as "Solved". We are responsible to mark our own threads we open as solved when that time comes. Visit the "Thread Tools" link in the upper giht of the page, then select "Mark Thread as Solved".

---

### Post by unicav on 2024-05-12
Done. Thanks

---

### Post by TheFu on 2024-05-12
Happens to all of us.  We get fixated on "what changed recently" because that usually is where a problem starts.

Router stuff follows .... ignore if you aren't interested ....

BTW, if your router hasn't gotten any patches in the last 3 months, perhaps it is time to get a new one and pick one with a very long patch/update period. There are consumer router companies that patch for 5-7 yrs across all their routers, not just the most popular.  

I have one that was $38 refurbished.that I expect to keep using AND get updates for at least 5 more year from Asus.  Just sayin'.  Most consumer routers from one country get just a few years of firmware updates, so either choose models that can run openwrt/dd-wrt or go with brands that have a history of long firmware update periods.  I like Asus because they are under a US FTC mandate for another 10 yrs with outside oversight to ensure their routers are maintained.  You can read more about the agreement here: [https://www.ftc.gov/news-events/news/press-releases/2016/02/asus-settles-ftc-charges-insecure-home-routers-cloud-services-put-consumers-privacy-risk](https://www.ftc.gov/news-events/news/press-releases/2016/02/asus-settles-ftc-charges-insecure-home-routers-cloud-services-put-consumers-privacy-risk)

BTW, I was burn by the same brand you have - bought it and less than 2 yrs later, they stopped releasing firmware updates.  On paper, it was a fantastic, capable, router.  In theory, it supported dd-wrt as well, but in practice, the only way to get dd-wrt onto it was go back to the first released firmware, then get the German version and upgrade to that, then load dd-wrt over it. It was really picky and I never got passed the German firmware once support ended.  My next router was a small AMD x86-64 computer built to run as a router.  Bought that almost 10 yrs ago now and don't have any plans to replace the hardware. Initially, I put pfSense on it, but then switched to OPNSense about 6 yrs ago.  Those are nerdy router distros - probably too nerdy for normal consumers, but great for network nerds.  If you knew you'd get 10+ yrs from a router hardware, that initial cost becomes less important, though I spent less than $150.  It was patched Friday. Updates keep coming 1-2 times a month.

---

### Post by him610 on 2024-05-13
It is all of the recent sunspot activity. The same sunspot activity that gives us the visually stunning aurora borealis these last few nights also cause glitches and other disruptions in our electronic devices and networks.

---

