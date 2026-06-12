---
title: "failed to initialize HAL- error"
date: 2007-10-17
forum: General Help
---

### Post by shorty28898 on 2007-10-17
i just updated to 7.10, and now the HAL error comes up, and it does not allow me to get a connection.  can someone help?

---

### Post by thedonvaughn on 2007-10-17
Hello,
I'm assuming you have tried rebooting?
Does "sudo /etc/init.d/hal restart" correct the issue?

---

### Post by shorty28898 on 2007-10-17
No it did not work.  After saying that HAL was restarted, nothing hapened, except that it froze ubuntu about 30 seconds later, the only way of getting out was ctrl alt backspace to logout, any more ideas?  it only hapenes when i update the HAL, so i sopped doing it, but in 7.10 it installed

---

### Post by seldenthuis on 2007-10-18
Does this work?  ```
sudo /etc/init.d/dbus restart
```

---

### Post by seldenthuis on 2007-10-18
See also: [http://ubuntuforums.org/showthread.php?p=3545464]("http://ubuntuforums.org/showthread.php?p=3545464") and [https://bugs.launchpad.net/ubuntu/+s...bus/+bug/25931]("https://bugs.launchpad.net/ubuntu/+s...bus/+bug/25931").

Apparently there is a problem with the boot order when CONCURRENCY=shell in /etc/init.d/rc.

I hope this helps.

---

### Post by white on 2007-10-18
> **seldenthuis said:**
> See also: [http://ubuntuforums.org/showthread.php?p=3545464]("http://ubuntuforums.org/showthread.php?p=3545464") and [https://bugs.launchpad.net/ubuntu/+s...bus/+bug/25931]("https://bugs.launchpad.net/ubuntu/+s...bus/+bug/25931").

Apparently there is a problem with the boot order when CONCURRENCY=shell in /etc/init.d/rc.

I hope this helps.

Well you solved my problem, I was just about to post a thread like this. Set my concurrency back to none and it was all good. :KS

---

### Post by alzie on 2007-10-20
> **seldenthuis said:**
> See also: [http://ubuntuforums.org/showthread.php?p=3545464]("http://ubuntuforums.org/showthread.php?p=3545464") and [https://bugs.launchpad.net/ubuntu/+s...bus/+bug/25931]("https://bugs.launchpad.net/ubuntu/+s...bus/+bug/25931").

Apparently there is a problem with the boot order when CONCURRENCY=shell in /etc/init.d/rc.

I hope this helps.

I tried this (Ihave the same problem) and changed S12hal to S13hal and I changed S13gdm to S14gdm but I still have the HAL failed to inititialize error.  

I'm showing "No network connection" on that icon too but I can access the internet  :confused:

I'll keep on looking

---

### Post by shorty28898 on 2007-10-24
i dont really understand..

---

### Post by moshazat on 2007-10-24
Hello, i need some help here since im new with linux and ubuntu.
Image below is my Guest profile for ubuntu gnome desktop currently after i updated my ubuntu 7.04 to 7.10 at 18oct...

[IMG]http://img86.imageshack.us/img86/6558/error710ki8.png[/IMG]

As you can see there is a message says "Internal Error : Failed to initialized HAL!" which always popup each time i start my ubuntu.
If you realize also at my top gnome panel at the tray, my Pidgin is really online, but you see more to the right of my pidgin, my connection status is "No network connection" and its icon also show it is offline.

All this happen after i upgrade my ubuntu festy fawn 7.04 to ubuntu gutsy gibbon 7.10. Im really want to fix this.

what is actually happen? 

help

---

### Post by Ramaddan on 2007-10-25
Hi,

I had the same problem, but after using the fix here, everything is back to normal.

I followed the fix in this thread:
[http://ubuntuforums.org/showthread.php?p=3545464]("http://ubuntuforums.org/showthread.php?p=3545464")

Hope it helps anyone.

---

### Post by Ramaddan on 2007-10-25
My files in /etc/rc2.d/ after Feisty to Gutsy upgrade were named:

S12Dbus
S12hal
S13GDM

So I renamed them to:

S12Dbus
S13hal
S15GDM

And now I have no issues. Hope this helps anyone.

---

### Post by shorty28898 on 2007-10-26
i tried that, and then did the tihng at the bottom where he changed S13gdm to S15gdm..
and the HAL error is stillll there..  
any ideas now?



These are mine..and the error still shows..

S12dbus
S13hal
S15gdm

---

### Post by Ramaddan on 2007-10-26
Hi,

I'm not that great in terms of details of how Ubuntu works, but the idea is that the Dbus is supposed to start before the HAL engine, and then GDM, so that everything works out fine.

Did you restart after making the changes?

Just type in a terminal:
> cd ~
ls /etc/rc2.d > filelisting

This should save a file called "**filelisting**" in your home directory.

Could you copy and paste the contents here?

Thanks.

---

### Post by E5o on 2007-10-26
Greeting fellow ubuntians

As I myself had this problem, I can confirm that changing the order of the links so that dbus loads, then hal and finally gdm, worked for me.


cheers

E5o

---

### Post by Six_Digits on 2007-10-28
Do they intend to fix this? I've tried all the mentioned and more. Needless to say, I'm back on Feisty.

EDIT - Fixed HAL with the following:

> sudo /usr/lib/hal/hald-generate-fdi-cache

---

### Post by jamesnewell on 2007-10-28
I had the same problem after following some tweaks and saw a post about "CONCURRENCY=shell" being the problem. Changed this and works fine.

Hope this might help someone else.

James

---

### Post by marcelloconti on 2008-02-18
> **seldenthuis said:**
> See also: [http://ubuntuforums.org/showthread.php?p=3545464]("http://ubuntuforums.org/showthread.php?p=3545464") and [https://bugs.launchpad.net/ubuntu/+s...bus/+bug/25931]("https://bugs.launchpad.net/ubuntu/+s...bus/+bug/25931").

Apparently there is a problem with the boot order when CONCURRENCY=shell in /etc/init.d/rc.

I hope this helps.

Wow, great. Exact.  After change "CONCURRENCY=none" in "/etc/init.d/rc" system works fine again.

---

### Post by TrendRat on 2008-02-18
Six_Digits, thanks for that input, it has made an improvement when all the other suggestions here didn't work for me.  PC is not hanging as before, and the little alarm emblem on my network indicator went away.  hal error on startup went away.  I can see my router and other computers on network, but can't see internet.  One thing at a time.....

---

### Post by prince_niceguy on 2008-02-21
I followed the advise [here]("http://linux4humanbeing.blogspot.com/") and it fixed my issue of HAL. Also, I made changes related to apport and avahi from the same blog. Increased my boot time too.

---

### Post by itsjustarumour on 2008-02-22
> **thedonvaughn said:**
> Hello,
I'm assuming you have tried rebooting?
Does "sudo /etc/init.d/hal restart" correct the issue?

I just got this issue, all I'd done was install a newer version of AWN using the standard how-to here:

[http://ubuntuforums.org/showthread.p...&highlight=AWN](http://ubuntuforums.org/showthread.p...&highlight=AWN)

Rebooted my machine to check AWN would start up OK, and got the HAL error message and no network connection - Network Manager had just ditched the settings for both my Ethernet and Wireless connections.

"sudo /etc/init.d/hal restart" didn't seem to fix it, however I then used Synaptic to reinstall HAL and all the relevant libraries, and everything is tickety-boo again  :-)

---

### Post by juky on 2008-04-03
Just FYI, I Had an HAL error, and fixed it by renaming S12hal to S13hal. So "dbus", "hal" and "gdm" are like this:

```

S12dbus
S13hal 
S30gdm

```

And HAL error is not present, everything works a charm.

Thanks for the link which helped me a lot.

Cheers!

---

