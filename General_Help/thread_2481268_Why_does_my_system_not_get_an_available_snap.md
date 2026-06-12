---
title: "Why does my system not get an available snap?"
date: 2022-11-23
forum: General Help
---

### Post by superian on 2022-11-23
I use Firefox as my primary browser. It took TWO DAYS from being told about the latest update to it to actually be installed. That means two days of closing it down, trying to get the update I was repeatedly being told was available, only to be told that there were no updates available.

Until then, this is what happened:

```
ian@pc:~$ sudo snap list
Name                               Version                     Rev    Tracking         Publisher       Notes
bare                               1.0                         5      latest/stable    canonical&#10003;      base
..
[..]
firefox                            106.0.5-1                   2067   latest/stable    mozilla&#10003;        -
[..]

ian@pc:~$ sudo snap refresh firefox
snap "firefox" has no available updates

```

.. but..

```
ian@pc:~$ snap info firefox
name:      firefox
summary:   Mozilla Firefox web browser
publisher: Mozilla&#10003;
store-url: https://snapcraft.io/firefox
contact:   https://support.mozilla.org/kb/file-bug-report-or-feature-request-mozilla
license:   unset
description: |
  Firefox is a powerful, extensible web browser with support for modern web application
  technologies.
commands:
  - firefox
  - firefox.geckodriver
snap-id:      3wdHCAVyZEmYsCMFDE9qt92UV8rC8Wdk
tracking:     latest/stable
refresh-date: 13 days ago, at 22:42 GMT
channels:
  latest/stable:    107.0-2      2022-11-15 (2088) 249MB -
  latest/candidate: 107.0-2      2022-11-11 (2088) 249MB -
  latest/beta:      107.0b9-1    2022-11-04 (2062) 187MB -
  latest/edge:      109.0a1      2022-11-17 (2108) 193MB -
  esr/stable:       102.5.0esr-1 2022-11-15 (2077) 183MB -
  esr/candidate:    102.5.0esr-1 2022-11-08 (2077) 183MB -
  esr/beta:         &#8593;                                    
  esr/edge:         &#8593;                                    
installed:          106.0.5-1               (2067) 213MB -
```

So the snap system KNOWS that there is an update available, but will not install it. Why not??

Am I missing something, or is there no way to force an update?

Two days after I start doing this, it works and I finally see:

```
firefox 107.0-2 from Mozilla&#10003; refreshed
```

(Yes, firefox was completely shut down when trying this: it's partly done by a script that waits for that to happen, I have been caught by that before...)

---

### Post by maglin2 on 2022-11-23
I don't know the answer to your question, but it has happened to me too.
It may be the ubuntu practice of phased update roll-out in the hope of catching major problems early. Maybe it's just managing traffic for big downloads.
I think their problem lies in alerting us to the update before we can get it.

---

### Post by ian-weisser on 2022-11-23
Perhaps throttling. See [URL="https://bugs.launchpad.net/snapd/+bug/1996653"]LP#1996653
[/URL]
> 
This is most likely because the updates have been throttled to ease the  load on the snap store. So this is working as intended, although the UX  is slightly confusing. Perhaps it would be better if snapd knew how to  communicate this more clearly to the user.


---

### Post by superian on 2022-11-24
Well, the repositories of .deb packages doesn't seem to do that and they must get vastly more traffic than the snap store.

There are words for people who knowingly withhold security updates for critical software, and none of them are nice.

---

### Post by maglin2 on 2022-11-24
Ubuntu desktop has been using phased updates for years. [https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)
From 21.04 it was extended to servers, containers etc once apt started to support phased updates natively. [https://www.phoronix.com/news/Ubuntu-21.04-Phased-Updates](https://www.phoronix.com/news/Ubuntu-21.04-Phased-Updates)

---

### Post by ian-weisser on 2022-11-24
Be nice. Nobody is *"knowingly withhold[ing] security updates."* Don't tread the shady, hyperbole-laced path leading toward crank-talk.

Throttling is temporary. Be patient. Both the LP Bug report, and a search of snapcraft.io, agree on that. Looks like throttling has occurred many times in the snap-store's history.

I've seen a couple deb security updates get phased (different cause), which has a similar effect upon users.

---

### Post by maglin2 on 2022-11-24
I see that 'snap refresh' should now bypass throttling. 
With the snap itself provided directly by Mozilla this puts us in a better situation than we've had with apt, where (for whatever reason - packaging, phasing) I've sometimes waited days to get a new firefox release.

---

### Post by grahammechanical on 2022-11-24
The snap version of Firefox is the responsibility of the Mozilla developers. They are the ones who push out the refresh of Firefox when they are ready. The system gives advanced notice of an intended update about 11 days in advance. This is useful for those users who never shutdown their machines and always have Firefox open. It gives fair warning of what will happen in the immediate future. Trying to refresh the Firefox snap before the Mozilla developers have pushed the new snap into the channel will fail. 

One of the advantages of snap packaged applications that are being maintained by the original developers of the application is that the update comes direct from the developer without having to go through the Canonical auditing process. We get security fixes quicker.

Regards

---

### Post by superian on 2022-11-30
Firefox 107.0 looks to have been available in the Debian repositories on  the 16th November. That was, from memory, the day that my Ubuntu system  told me that I had to close down Firefox because there was an update.

It took two days for me to actually get it, despite repeated 'snap refresh firefox'.

Tell me again how the snap store means we get security fixes quicker.

---

### Post by superian on 2022-11-30
> **ian-weisser said:**
> Be nice. Nobody is *"knowingly withhold[ing] security updates."* Don't tread the shady, hyperbole-laced path leading toward crank-talk.

Would you prefer "rationing security updates"?

> Throttling is temporary. Be patient. Both the LP Bug report, and a search of snapcraft.io, agree on that. Looks like throttling has occurred many times in the snap-store's history.

Why? Being under resourced or something else?

If an update to a software store or a spell-checker or Spoitfy is delayed, 'Oh well'. If an update to a  browser - a top two application for most desktop users is delayed - that can be serious.

Ubuntu effectively forced the snap versions of firefox and chromium onto its users. (I am aware that it is possible to install a .deb version of both if you jump through some hoops, but from what I can see, you lose the user data that the initial move to the snaps and subsequent refreshes retain, and I have a lot of browser history etc.)

I would say that it has a responsibility to have the snap store be at least as reliable as the .deb repositories it replaces. *And it hasn't been*.

> **ian-weisser said:**
>  I've seen a couple deb security updates get phased (different cause), which has a similar effect upon users.

In my experience, if get-apt update says there's an update, get-apt upgrade gets it and installs it.

Here, snap info firefox was telling me that there was an (important) update, but snap refresh firefox was not letting me have it.

If I sound annoyed about this, I am. I hope this isn't being taken personally, because it's not meant to be, but it is making me seriously consider switching away from Ubuntu, despite having used it as the main desktop OS since 4.10.. 

.. apart from the handful of years between Ubuntu going Unity and there being a Ubuntu with a Gnome 2-alike again..

.. and it's that desktop use that means I spec'd it for dozens of servers.

---

### Post by TheFu on 2022-11-30
> **superian said:**
>  There are words for people who knowingly withhold security updates for critical software, and none of them are nice.

If you are doing risky things where the snap restrictions don't provide sufficient risk management, perhaps a different solution is needed?  Snap packages are a prophylactic solution for many risks. If you need more, then that behavior isn't really suitable for a normal desktop, IMHO.

Sometimes I do risky behaviors online just to see what the current hacking state of the art is.  When I do, I'm running a virtual machine and usually running a specific browser known to have some security issues. I run it in a sandbox that doesn't allow any disk access, not javascript, and nearly all other addons/plugins are disabled, so they might gain a little access to the sandbox.  

If you are worried that a few days delay for any update is a huge issue, I'd ask which govt is out to get you?

Here, we patch weekly unless there's a specific, known, issue, that we are likely to be impacted by.  99.9% of all security fixes don't apply to us.  In the last 10 yrs, only 2 patches got us to patch outside our normal weekend patch schedule (on a weekday!).  If I were living in a country that doesn't respect personal freedoms, I'd have very different needs and a very different stance and I'd be typing under 3 layers of blankets, including 1 "space blanket" to block EM signals.

New is the enemy of stable.

---

### Post by superian on 2022-12-26
> **TheFu said:**
> If you are doing risky things where the snap restrictions don't provide sufficient risk management, perhaps a different solution is needed?

I would phrase it as 'if Ubuntu cannot resource the snap store properly, they should not use it for critical applications'.

For the bulk of desktop users, the browser is a critical application. 

> If you are worried that a few days delay for any update is a huge issue, I'd ask which govt is out to get you?

It depends on the severity, doesn't it? There are programs where once a sufficiently serious security advisory is released, the bots start looking to exploit it. I have had one server hacked in he past decade - that one happened within six hours of the relevant advisory being published. So I have an hourly cron job on the servers that looks for security updates and installs them.

Today on a PC that hadn't booted into Ubuntu for a couple of weeks..

 me@pc:~$ sudo snap refresh
All snaps up to date.

.. and literally seconds later..

me@pc:~$ sudo snap refresh firefox
firefox 108.0.1-1 from Mozilla&#10003; refreshed

 
I suppose I should be grateful that the latter worked and that this update is about as minor as they come - the only change was around a bug for the default search engine - but I have had enough. I am not checking each and every application individually just in  case security updates are being "rationed" or "throttled" and 'sudo snap refresh' is  not being accurate when it says everything is up to date.


 Having to add that line to update scripts was annoying, but this is unacceptable. No more snap store here or on any of the servers: I simply cannot trust it.

---

### Post by TheFu on 2022-12-27
The "Snap Store" is full of random, 3rd party, applications.  It isn't curated by Canonical.  I have some snaps that haven't been updated since 2020 that are installed, so don't think they are "critical applications" in there.

Often, developers don't think through all the uses for their F/LOSS.  Initially, they all start out as nothing to be trusted, but if they are published, now there's know way to know what end-users will believe nor how the software may be used.

I remember sitting in the server room of a control center using Netscape Navigator and reading the EULA, which clearly stated that it shouldn't be used for any mission critical  needs and never used in a control center. ;)  Just sayin'.    I was just reading a website and it was the only way I could know that was happening with the 600+ other controllers (humans) working in the building on that very important day, but I wasn't using it it to make any critical system decisions. I was just babysitting 1 project's server during a critical mission phase.  Sitting in a loud, overcooled, data center, raised floor.  There were 2 other people in the room about 50ft away, also bored.

---

