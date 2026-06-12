---
title: "printer stopped working"
date: 2008-03-06
forum: General Help
---

### Post by linuxted on 2008-03-06
After a recent upgrade my hp photosmart 7150 stopped working.   It is connected to the computer via USB and does have power and paper.  I've tried fiddling with the drivers and it is just acting wierd (printer queu sits there)

Don't remember if this is gutsy, but here is uname -a:
Linux office 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

I'm really lost on this one, any help would be appreciated

Thanks,
mozart

---

### Post by kuja on 2008-03-06
I had a similar problem with my HP Photosmart C5280 about a week ago, also after doing some upgrades. I couldn't find a resolution, but I narrowed the problem down to some sort of problem with foomatic, I think. Check your /var/log/cups/error.log file (or similar) to see what I'm talking about (assuming it's the same problem, and I'm willing to bet that it is). Since I ***really*** need my printer after a couple days of trying to get things back in working order (ie: downgrading every printer-related package I could think of), I pulled out my Install DVD and reverted to a non-upgraded Gutsy.

---

### Post by linuxted on 2008-03-06
> **kuja said:**
> I had a similar problem with my HP Photosmart C5280 about a week ago, also after doing some upgrades. I couldn't find a resolution, but I narrowed the problem down to some sort of problem with foomatic, I think. Check your /var/log/cups/error.log file (or similar) to see what I'm talking about (assuming it's the same problem, and I'm willing to bet that it is). Since I ***really*** need my printer after a couple days of trying to get things back in working order (ie: downgrading every printer-related package I could think of), I pulled out my Install DVD and reverted to a non-upgraded Gutsy.

Yeah, this is REALLY frustrating.  I need the printer to work and hope somebody is trying to fix this.  The printer has been down for a week.

My error_log and page_log files are empty btw.  I do see the following in the access_log

localhost - - [06/Mar/2008:14:44:21 +0000] "POST / HTTP/1.1" 200 181 Get-Jobs su
ccessful-ok
localhost - - [06/Mar/2008:15:16:29 +0000] "POST / HTTP/1.1" 200 181 Get-Jobs su
ccessful-ok

---

### Post by kuja on 2008-03-06
Looks like you might not be getting the same error afterall. I'm sure that doesn't reassure any though, seeing as its still not working :\ I'm going to take a look around launchpad and see if it was reported.

---

### Post by kuja on 2008-03-06
I  see some very similar things (to mine) that seem to say disabling apparmor takes care of the problem. Maybe it'd be worth a try for you? ("sudo /etc/init.d/apparmor stop" should do the trick, I think)

---

### Post by linuxted on 2008-03-06
> **kuja said:**
> I  see some very similar things (to mine) that seem to say disabling apparmor takes care of the problem. Maybe it'd be worth a try for you? ("sudo /etc/init.d/apparmor stop" should do the trick, I think)

That didn't seem to help, but I found something that did.

Go to System-> Administration -> Printing
If you don't see (like I didn't) "Print Test Page" go to the "Policies" tab and select "enabled".
If that still doesn't work, try different URI settings on the Settings tab.

For reference I'm using "ptal:/mlc:usb:photosmart_7150" for the URI and "HP PhotoSmart 7150 Foomatic/hpijs (recommended)" for the make and model

Hope that helps you.

I'm printing again with no issues.

imho this is a bug that someone in the know should fix.  This is a far from intuitive work around.

---

