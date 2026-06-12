---
title: "Firefox2 = 100% CPU?!"
date: 2006-11-08
forum: General Help
---

### Post by breakerfall on 2006-11-08
Hiya!

Anyone else having trouble with firefox 2 eating up 100% CPU when loading pages or links?

for example:
I've got a bookmark folder with 12 bookmarks in it and when I 'open in tabs' its taking about 3-5 MINUTES to open all the tabs because it maxes out the processor for the whole process!  Windows finishes the same 12 tabs in about 30 SECONDS on the same machine!  
This is driving me CRAZY!  

I've also tried an Automatix-installed Swiftfox with similar results...
(Epiphany works fine, FWIW)

Any ideas?

I do have a few extensions running, but I've got the same ones and then some in Windows.

thanks,
mike

---

### Post by localuser on 2006-11-08
I just tried it with 16 tabs and all opened in about 10 seconds.

What extensions are you running?

[edit] I just saw your signature.  Are you running 64 bit OS?

---

### Post by breakerfall on 2006-11-08
ahem...
i guess this is a lesson in 'dont use showcase in linux'
-or-
'dont post before you try stuff, idiot'

but even with showcase turned off (not disabled) it was still wicked slow...
now that i disabled it, firefox has sped up quite a bit
(and now that ive re-enabled it, firefox still seems quicker than before)

anyhooooo..........
if youre using windows, Showcase ([https://addons.mozilla.org/firefox/1810/](https://addons.mozilla.org/firefox/1810/)) is an awesome extension...

and now for a smily - :redface:

and no, not running 64bit yet
you?

---

### Post by localuser on 2006-11-08
Since showcase is a tab management add-on, then I it makes sense that it might be the cause of the problem.  It may be leaky, in which case it also makes sense that Firefox is faster after a reinstall.  Things may start to slow down after some time.

---

### Post by breakerfall on 2006-11-08
<homer>mmm leaky...</homer>

thanks for the help, local....

u running 64bit?

-mike

---

### Post by localuser on 2006-11-08
> **breakerfall said:**
> u running 64bit?

No, I'm not.  I understand that the 64-bit version is not as stable as its 32-bit little brother

---

### Post by deleopario on 2006-11-08
Are you sure you have the right video drivers? When I first installed my system loading webpages took generally about thirty seconds each and the CPU was maxed out.

---

### Post by papparainen on 2006-11-16
This is a Nautilus related bug that is reported widely. If you do a google search i.e. Ubuntu 100% processor load etc. you'll find out more.

It is triggered if you are uploadin 2 or more files at the same time etc. 
I'm still looking for an official patch as I'm still a n00b with Ubu ;). 

Dapper Drake seems to be OK, though ;)

---

### Post by ciscosurfer on 2006-11-16
There are many threads on the forums here that discuss your issue.  You can do a quick search to find out more.

---

### Post by papparainen on 2006-11-16
[https://launchpad.net/distros/ubuntu/+source/gnome-vfs2/+bug/54684](https://launchpad.net/distros/ubuntu/+source/gnome-vfs2/+bug/54684)


[https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/68100](https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/68100)

[https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/56786](https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/56786)

---

### Post by localuser on 2006-11-16
Am I missing something?  Are the bugs cited valid for Nautilus or Firefox?  The OP was complaining about Firefox when opening multiple tabs.  What's the connection?

---

### Post by papparainen on 2006-11-16
Quote:
"
Anyone else having trouble with firefox 2 eating up 100% CPU when loading pages or links?"

Try killing or stopping the Nautilus process from the task manager. It helps for me ;). There's yur connection ;)

plus:
"

Hi

I think this also happens on my edgy install on startup. Nautilus uses 100% CPU and I have to killall it, then everything is fine. This happens to me almost on every reboot. I think it's the same issue since I sometime have images or folders with videos on my desktop folder and they show with the "creating thumbnail" icon
"

Cheers

---

### Post by Zimmer on 2006-11-21
Similar experience, 100% cpu with firefox, TOP shows  a perl process running as root as the culprit at @ 96%  killed the perl process and all ok again..... ??

---

