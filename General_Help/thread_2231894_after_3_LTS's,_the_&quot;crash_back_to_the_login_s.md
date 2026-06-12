---
title: "after 3 LTS's, the &quot;crash back to the login screen&quot; bug still occurs"
date: 2014-06-28
forum: General Help
---

### Post by eival on 2014-06-28
just happened, opening up sites in firefox on Ubuntu 14.04 64bit and boom, black screen with a terminal cursor at the upper top of the screen, about 30 seconds later it loads the login screen.

this has been happening since 8.04 which is when i first started using Ubuntu, never happened on Debian over the last year i was using their LTS (Weezy) since it was the only one that would fit on my USB stick at the time till i got a new HDD, so this is a specific Ubuntu-fork development/coding issue and obviously its got nothing to do with the UI cause you've only had Unity since 11x onward but it was happening back with Gnome prior to that.

and it doesnt even recognize it as a crash, like when the UI freezes and resets itself and the blue "crash" icon appears letting you report the issue, so the OS itself doesnt even think something wrong just happened.

why is Firefox able to affect the OS itself? i already have 3 of the 4 addons turned off "website/desktop/online intergration", there's obviously something else hidden in the about:config or something that doesnt run Firefox as a shell just like every other app on the OS and sends some type of "logout" signal.

---

### Post by coffeecat on 2014-06-28
I have never, ever, ever seen what you describe in all the installations of every version of Ubuntu since 2005 on about a dozen or more different pieces of hardware. And I don't recall seeing this "bug" mentioned by others in forum threads here.

By "bug", what do you mean? Do you have a launchpad link? Have you filed a bug on launchpad? How many different sets of hardware have you seen this on since 8.04? What are the hardware specifications?

---

### Post by eival on 2014-06-28
look through my post history, ive made threads about this before, with 8.04, 10.04, thru its 3rd year of support then i was on Debian for the last year till now. ive gone from AMD proccessors and Intel, Nvidia graphics, intergrated graphics.

---

### Post by mörgæs on 2014-06-28
It's not as far-fetched as it may sound. Here's a bug that I have confirmed: 
[https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1316832](https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1316832)

I know this is LXDE and not Unity. Just saying that a crash leading to log-out does happen.

---

### Post by eival on 2014-06-28
[http://ubuntuforums.org/showthread.php?t=1625644](http://ubuntuforums.org/showthread.php?t=1625644)

4 years later

and then i posted in that thread again, 2 years after that

[http://ubuntuforums.org/showthread.php?t=1625644&p=12184504#post12184504](http://ubuntuforums.org/showthread.php?t=1625644&p=12184504#post12184504)

---

### Post by uRock on 2014-06-28
Type "log" into the menu search, then open System Log and see if you can find anything that give give a clue into what is causing this. If you can find something, then it may be helpful in fixing the issue and creating a bug report.

---

### Post by eival on 2014-06-28
meant to quote uRock

Jun 28 15:43:01 gnome-session[1334]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.#012

then after that

it pretty much resembls this report on github

[https://github.com/linuxmint/muffin/issues/123](https://github.com/linuxmint/muffin/issues/123)

---

### Post by lite.m.finocchiaro on 2014-09-17
This just happened to me for the first time on 14.04 LTS. I, too, have been plagued by the problem for years.

Sep 17 14:24:13 LiteDesktop gnome-session[1845]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.#012
Sep 17 14:24:13 LiteDesktop colord: device removed: xrandr-Ancor Communications Inc-VE248-B6LMQS027761
Sep 17 14:24:13 LiteDesktop colord: Profile removed: icc-ac461a52248897d25bad4cda9ee3483d
Sep 17 14:24:16 LiteDesktop kernel: [696961.866086] nvidia 0000:03:00.0: irq 43 for MSI/MSI-X
Sep 17 14:24:17 LiteDesktop acpid: client 1541[0:0] has disconnected
Sep 17 14:24:17 LiteDesktop acpid: client connected from 5338[0:0]

I'm running Unity on a dual-core machine x64 Nvidia graphics card, Nvidia driver.

---

### Post by nadrach on 2014-09-17
Can do this almost every time in Lubuntu 14.04, both 64-bit and 32-bit.
"Preferences>Default applications for LXSession" and click on a "Reload" button. Usually the "Webbrowser" category will do it.
The earlier quoted bug report and fix ([https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1316832](https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1316832)) may be the answer here, but if so, it has yet to be backported to 14.04 after nearly 3 months.

---

