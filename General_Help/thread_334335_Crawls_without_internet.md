---
title: "Crawls without internet"
date: 2007-01-08
forum: General Help
---

### Post by v1100110 on 2007-01-08
Thank you for reading this far. I like Ubuntu, I'm trying to leave windows behind, so I'm trying MacOS and some linux distros.
I'm running edgy, compiled my kernel to 2.6.19, also I have the proprietary Nvidia driver running beryl. All this runs fine except I think the 1 second lag before my file system window comes up is a bit unresponsive.  
All this is when I'm connected to the internet. When my internet connection is down, it takes at least 30 seconds for a window to open. I can plug my computer back into the router and everything is normal- unplug it and immediately everything takes forever to open.  I did a clean install and I've only been up and running for about 3 days now, so there's not much that could have happened as in programs sending info home or anything. 
I really hope someone has an answer!

---

### Post by v1100110 on 2007-01-08
no one has any idea about this? I know I have seen some threads about the problem, but to no resolve.

---

### Post by rogblake on 2007-01-08
Are you running a caching name server? On my Dapper system, bind will sometimes chew up 100% of the CPU when not connected to the internet.

Bring up a terminal windows and enter the "top" command to see if there is some process hogging the system.

---

### Post by v1100110 on 2007-01-08
no, I've checked my processes and nothing is using over 2% of my cpu and only 3 processes are active.  I did run the top command and it showed the same thing.  Could samba be a cause?  strange thing is it's not the network- it's only when the actual internet is down.  I just found out it was a problem today when my internet went out for a few hours.

---

### Post by v1100110 on 2007-01-10
bump?

---

### Post by phansiizwe on 2007-01-10
I am connecting via WLAN using ndiswrapper/wpa_supplicant with a static IP.
As soon I as turn on my computer while WLAN is turned off in the router, Ubuntu slows down to a crawl.

I though this would be an issue with ndiswrapper/wpa_supplicant.

Anyone have any clues?

---

### Post by v1100110 on 2007-01-10
Have you tried removing your IPv6 connections? I heard that worked for one guy, but unless there's different places you can delete them that didn't work for me.

---

### Post by phansiizwe on 2007-01-12
My IPv6 is disabled, which I checked using:

```
ip a | grep inet6
```

If the output is empty, IPv6 is disabled.

Also, according to post #8 in [http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798), IPv6 cannot be the problem with slowdowns throughout Ubuntu so I guess the problem is caused by something else.

---

### Post by v1100110 on 2007-01-14
Yea, you wouldn't think that would make a difference but there's a thread about it working for another guy.  I never could find out what the problem was- so I decided to give SuSe a shot again, being that my install was only a week old in the first place. I didn't like it at all after I had been using ubuntu- so then I reinstalled- now everything's fine.

---

