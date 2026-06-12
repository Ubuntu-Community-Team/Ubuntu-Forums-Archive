---
title: "firefox slowing computer"
date: 2008-04-25
forum: General Help
---

### Post by dougleduck on 2008-04-25
Since I upgraded to 8.04 a few days ago my computer slows considerably for several minutes when firefox is first opened.

There is a constant amount of disc access for about 5-10 minutes, and consequently high CPU usage (considering I clear my cache regularly I don't understand why.

After this though it stops and carries on as usual.

Any help appreciated.

---

### Post by dougleduck on 2008-04-26
bump

---

### Post by dougleduck on 2008-04-28
Having tried disabling all add-ons and plug-ins it doesn't seem to make any difference.

Disk access is almost constant, top gives firefox as using a lot of CPU power (though if someone knows a command to give disk access and writing by program that'd help).

Anyone? Is this a bug, haven't found anything but then not sure what to search for to describe it.

---

### Post by joeybutterface on 2008-04-28
Happening to me this morning too.

Firefox is eating up 100% CPU usage and seriously lagging all the time. Continuous restarts but trying to access pages is slow.

All plugins disabled.

This is what you get when you have the brains to ship a Beta product in a so-called stable operating system.

---

### Post by joeybutterface on 2008-04-28
Specs aren't bad either:

Intel Dual Core 2.4Ghz
3gb Ram
250GB Sata II
256mb Nvidia 8600GT

---

### Post by szako on 2008-04-28
Just downgrade to ff2 for now, most of us did. :-)

---

### Post by joeybutterface on 2008-04-28
Are there any directions how to safely do the downgrade?

---

### Post by joeybutterface on 2008-04-28
OK here's what I did:

1. From my home directory backup existing configuration (just in case I ever need it):
tar -cvf firefox.tar .mozilla

2. Synaptic "search for firefox"
Remove firefox3 products

3. Restart Synaptic
4. Search for "firefox-2" and install those products.
5. Remove the black icon in the taskbar for the old Firefox. Then drag and drop the shortcut in Application > Internet > Firefox 2 to the taskbar for the new quick launch to Firefox 2.

All done!

---

### Post by Nurionn on 2008-04-28
*sudo aptitude install firefox-2*

... unfortunately I wasn't able to change the language to German (*mozilla-firefox-locale-de-de* didn't help)

---

### Post by dougleduck on 2008-04-28
Firefox 2 was already here after upgraded I realised, so I'll stick to that for now.

As for why a beta is included. Apparently its because its LTS. Guess they don't add new software to LTS so want a browser thats not out of date in 3 years. So they included a 'new and wont be broken for long' browser. I doubt it was an easy decision for them.

---

### Post by sebbouckaert on 2008-04-28
More about this also found here:

[http://ubuntuforums.org/showthread.php?t=759673&highlight=firefox+eating](http://ubuntuforums.org/showthread.php?t=759673&highlight=firefox+eating)

---

### Post by dougleduck on 2008-04-28
Well having followed that link and disabled the suspected forgery and suspected attack options everything seems ok again now.

I love the fact that everything useful is in .mozilla, backing it up makes switching between the different versions a piece of cake.

---

