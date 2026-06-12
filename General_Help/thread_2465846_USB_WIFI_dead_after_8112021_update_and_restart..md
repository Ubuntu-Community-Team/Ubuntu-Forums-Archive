---
title: "USB WIFI dead after 8/11/2021 update and restart."
date: 2021-08-13
forum: General Help
---

### Post by terraclast on 2021-08-13
I just installed the latest updates for 20.04 Focca Fossia. Everything went as it should and looked good.  
It prompted me to restart Ubuntu and I did.  
When I logged back in I couldn’t reach the internet and noticed the link light on the USB WIFI receiver (BrosTrend AC3 V2) wasn’t blinking.  
Ran ifconfig, only broadcast and loopback were available.  
Looked in network, and the only option there was for hardwired. I didn’t see anything that looked like WLAN access.  
I also noticed that the lock screen behavior is different than before the update.  
At this point I decided I would try to restore from backup because I don’t yet know how to rollback an update.  This did not work and threw a bunch of errors.  
I think the update is “ :1.586” or at least that’s the sender, but this is the first time I sought that information out and could be wrong.  One of the updated libraries looks to be for plugins: libfwupdplugin1:amd64 (1.3.11-1~focal1, 1.5.11-0ubuntu1~20.04.2).  However there are many other updates in the log.  


Is there an easy fix? Can I just roll back to pre-update in the cli? Or do I have to drag out a networking cable and plug it into my router? Hoping for the relatively easy fix.  

Thanks,
C

Edit: put the wrong date and made it seem like I created a time machine and installed an update from Oct. It’s now corrected.

---

### Post by terraclast on 2021-08-13
I looked for the WIFI area in settings and it just wasn’t there. That is, until I searched for it and entered it from search. Then it popped up above network. 
However, it is saying “No Wi-Fi Adapter Found” 
The adapter is plugged in and it was working the whole time up to the update. 
I’m highly confused by this.

---

### Post by Autodave on 2021-08-13
Can you give us some info on your PC please: make, model?

---

### Post by Timothy Taylor on 2021-08-13
Hmmm

I've noticed that suspend will not unsuspend on my laptop after this update.  
Networking is not enabled and attempts to enable it are ignored. Everything locks up if I try to restart and I have to use Alt-PrtScr-B.
I noticed this problem on my desktop also before the HDD failed

---

### Post by Impavidus on 2021-08-13
Was there a kernel upgrade amongst those upgrades? In that case, booting an older kernel may help.

---

### Post by terraclast on 2021-08-13
I have an HP Z440 and it should have an Intel Ryzen.

---

### Post by terraclast on 2021-08-13
I didn’t see one yesterday, but I will check later today, it looked like all lib updates. What kind of file would it be?

---

### Post by tea for one on 2021-08-13
To list all the installed kernels, open a terminal and enter:-
```
ls /boot | grep vmlinuz-
```

---

### Post by GhX6GZMB on 2021-08-13
10/11/2021?
Do you have a time machine? Where did you get the flux capacitor?

---

### Post by terraclast on 2021-08-13
Lolz. Oops. Yeah, 8/11/2021. 
I’ll see if I can correct it. My bad.

Edit: it’s been corrected: thank you for the heads up.

---

### Post by terraclast on 2021-08-13
Awesome, will report back when I can get back in front of the box. 
Thank you.

---

### Post by terraclast on 2021-08-13
There appears to be two kernals available:
vmlinuz-5.11.0-25-generic
vmlinuz-5.8.0-63-generic

Thank you for the command to check that.

---

### Post by tea for one on 2021-08-14
Can you reach your Grub menu?

Advanced options > Select the previous kernel 5.8.0-63-generic

---

### Post by mikewhatever on 2021-08-14
Have you installed a driver for that USB wifi? If so, it must be reinstalled after every kernel update.
An output of "lsusb" should provide some relevant info.

---

### Post by terraclast on 2021-08-14
> **mikewhatever said:**
> Have you installed a driver for that USB wifi? If so, it must be reinstalled after every kernel update.
An output of "lsusb" should provide some relevant info.

Oh, interesting. I didn’t know that. I’ll give it a try before I going the GRUB route as Tea for one suggested. 
Thank you.

---

### Post by terraclast on 2021-08-15
So, I just looked around for a 5.11.0-25-generic kernel version of the driver and I wasn’t able to find one. Looks like I’ll have to follow Tea for one’s advice and stay there until a new driver comes out. &#129335;*&#9794;&#65039;

---

### Post by terraclast on 2021-08-15
> **tea for one said:**
> Can you reach your Grub menu?

Advanced options > Select the previous kernel 5.8.0-63-generic

I switched to 5.8.0-63-generic and it is working again.  Thank you for the solid suggestion.  And now we wait until a new driver is available for 5.11.0-25-generic as I am far too much of a n00b to be meddling with the kernel myself.  

Many thanks to all who helped here!!!

---

