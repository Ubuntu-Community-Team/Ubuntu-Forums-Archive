---
title: "Firefox sluggish at the beginning, like the old days i Windows"
date: 2008-04-29
forum: General Help
---

### Post by petri on 2008-04-29
Directly after boot when I start Firefox (Hardy 64-bits) it grays out quite often and the harddrive works like it was in Windows a few minutes (and of course usage of CPU rises with the gray periods).

Is it 64-bits or what?

System is AMD 5000+ and 4GB ram.

---

### Post by Sukarn on 2008-04-29
I don't know what's causing this problem, but I'm facing it as well, and its damn annoying.

I'm an amd64 user too.

---

### Post by Sukarn on 2008-04-29
Sorry, double post.

---

### Post by petri on 2008-04-29
Yes I know, read the stickys... :mrgreen:

This explains pretty well the Firefox problem: 
[http://ubuntuforums.org/showpost.php?p=4834089&postcount=4](http://ubuntuforums.org/showpost.php?p=4834089&postcount=4) 

and the whole sticky can be found [http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851)

I have also problem with the segmentation fault (random exits) but I haven't tried it yet.

---

### Post by ghost_ryder35 on 2008-04-29
> **petri said:**
> Directly after boot when I start Firefox (Hardy 64-bits) it grays out quite often and the harddrive works like it was in Windows a few minutes (and of course usage of CPU rises with the gray periods).

Is it 64-bits or what?

System is AMD 5000+ and 4GB ram.
Have you guys tried this?
[quote=miguel]
To all interested parties, according to the bug report, deleting the urlclassifier files in your firefox profile (at ~/.mozilla/firefox/some-random-profile-name/
[/quote]

and

going to edit, prefrences, security tab and then un tick the two boxes that say "tell me if the site..."

---

### Post by Darkdelusions on 2008-04-29
If you go to about:config and disable network.dns.disableIPv6 it will also speed up the browser (this is assuming your not using IPv6)

---

### Post by petri on 2008-04-29
Yes ghost_ryder35, it was that "box ticking" what I needed. I'll wait a couple of days with deleting the urlclassifier* files.

---

### Post by ghost_ryder35 on 2008-04-29
> **Darkdelusions said:**
> If you go to about:config and disable network.dns.disableIPv6 it will also speed up the browser (this is assuming your not using IPv6)
to expand on this
```

sudo gedit /etc/modprobe.d/blacklist

```
add the line
```

##disable ipv6
blacklist ipv6

```
stops ipv6 modules from being loaded on system boot

---

### Post by ghost_ryder35 on 2008-04-29
> **petri said:**
> Yes ghost_ryder35, it was that "box ticking" what I needed. I'll wait a couple of days with deleting the urlclassifier* files.
please make sure to mark this thread SOLVED

---

### Post by petri on 2008-04-29
> **ghost_ryder35 said:**
> please make sure to mark this thread SOLVED

I did bit before but obviously it didn't work. How do I do it?

---

### Post by Sukarn on 2008-04-29
> **petri said:**
> I did bit before but obviously it didn't work. How do I do it?

At the top of the thread, "Thread Tools -> Mark as Solved"

---

### Post by petri on 2008-04-30
Why can't I see it?

I see these alternatives:

Show Printable Version
Email this Page
Subscribe to this Thread
Add a Poll to this Thread

---

