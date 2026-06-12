---
title: "Chrome freezes at random intervals"
date: 2019-12-16
forum: General Help
---

### Post by JohnDillinger43 on 2019-12-16
I'm having a weird issue that seems to be specific to Chrome in Ubuntu (don't have this problem with Chrome on Windows or Firefox on Ubuntu) -- every 10 seconds or so it will freeze for about 10 seconds.  It's not completely unresponsive, but if I'm typing, what I'm typing doesn't show up until after the 10 second interval, if I'm resizing/maximizing a window it will hang for a few seconds, if I'm watching video it will freeze on one frame, etc.  I still have 16.04 64-bit, and just upgraded to Chrome 79.0.3945.79.  I like Chrome for its speed but this problem is so annoying that I've been using Firefox instead.  Any leads on anything I can check out would be appreciated.

---

### Post by TheFu on 2019-12-17
Modern browsers are RAM and CPU hogs.
* Disable all addons and plugins. Does it still happen or not?  If not, then the cause is an addon or plugin.
* When it slows, what is the total system RAM use?  Is swap almost fully used too?  Can you close other programs to gain more RAM and does Chrome become responsive again?

**top** and **free** are the programs to use for monitoring RAM and swap.

BTW, I had a similar issue with Firefox yesterday.  Closed down Thunderbird which freed about 1G of RAM and everything was fine for an hour.  Then FF started getting slow again, so I checked the RAM/swap use. It was close to running out again, so I looked over my 20 tabs for those with lots of javascript and closed a few.  That freed up the RAM and the entire system became responsive again.

Hope this gives you some ideas.

---

### Post by Bashing-om on 2019-12-17
JohnDillinger43; Hello

What version of chrome are you running presently ?

My chromium version now,  after recent updates:  
> 
Version 79.0.3945.79 (Official Build) Built on Ubuntu , running on Ubuntu 18.04 (64-bit)


Is also acting up, and intermittently un-responsive for some time on all web pages.
Usable but aggravating.
"Top" does not show an issue with memory, so I am going to await an update that might bring resolution.

[INDENT]these things happen :( 
[/INDENT]

---

### Post by TheFu on 2019-12-17
Does chromium show the same issue?  Both browsers use the same base code.
I haven't seen it in chromium, yet.

---

### Post by Bashing-om on 2019-12-17
TheFu -

> **TheFu said:**
> Does chromium show the same issue?  Both browsers use the same base code.

Yes, issue appears to be very similar in chromium. Took several minutes and reloads to reply to this thread :(

[INDENT]Yukkie
[/INDENT]

---

### Post by localbuddha on 2019-12-18
Registered just to write to this topic: yes, Chrome 79 & Chromium 79 are freezes in Ubuntu. It starts after update Chrome to v79, so I installed Chromium (v78 for this moment of time). After few days Chromium updated to v79, and also starts freezing, like Chrome. So I've managed to downgrade Chrome to v78.

"how to": [https://stackoverflow.com/questions/32248164/how-to-downgrade-chrome-on-ubuntu-and-disable-auto-update](https://stackoverflow.com/questions/32248164/how-to-downgrade-chrome-on-ubuntu-and-disable-auto-update)
Here is an older versions of Chrome: [https://www.slimjet.com/chrome/google-chrome-old-version.php](https://www.slimjet.com/chrome/google-chrome-old-version.php)

---

### Post by TheFu on 2019-12-18
That explains why I haven't seen any issues yet:
```
$ dpkg -l|grep chromium
ii  chromium-browser                               78.0.3904.108-0ubuntu0.16.04.1                  i386
```

Weekly patching (Saturdays), means we don't see the bleeding edge mistakes, unless they are still there over a weekend.

---

### Post by Bashing-om on 2019-12-19
update

In my case, not a freeze but a loss of focus. Hovering the mouse over the browser's reload icon and then mousing back to the page restores.

strange!

---

### Post by maclenin on 2019-12-27
Howdy!

I can report the same issue - freeze / lag:

**google chrome:** Version 79.0.3945.130 (Official Build) (64-bit)

**chromium:** Version 79.0.3945.79 (Official Build) (64-bit)

No problems with firefox (71.0)....

No (recent) issues with the chrom* browsers prior to the latest (79) update.

Issue affects: 16.04.6

Issue affects: 18.04.4

Ref: [https://support.google.com/chrome/thread/23283471?hl=en](https://support.google.com/chrome/thread/23283471?hl=en)

---

