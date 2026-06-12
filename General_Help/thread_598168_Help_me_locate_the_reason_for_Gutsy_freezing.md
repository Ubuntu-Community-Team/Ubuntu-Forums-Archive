---
title: "Help me locate the reason for Gutsy freezing?"
date: 2007-10-31
forum: General Help
---

### Post by Rapax on 2007-10-31
Hi

Here's my setup: I'm running Gutsy on a Dell Inspiron AMD64. I originally installed normal 64bit ubuntu, but then apt-get installed kubuntu desktop over it. I now use KDE and kdm.

Recently (as in the last three or four days), when I leave my machine running unattended for a few hours (for example over night), it will be totally frozen when I come back.

The freeze is not on the level of the X-Server freezing, as I can neither ping the machine, nor connect to it by ssh when it's frozen. No mousecursor is shown, caps-lock does not react (LED on the keyboard). The only thing I can do is hold the power button for five seconds to force a power cycle.

I have already eliminated compiz-fusion as the culprit, by disabling it entirely (kwin --replace). I have also had all my other applications (opera, pidgin, OOo, etc.) closed, and still the freeze occurs.
Last night, I left 'top' running in a shell window and disabled the screen saver, so this morning I had a snapshot of what was running when the freez occured. Nothing out of the ordinary, 'init' was the top process, using less than 1% CPU and virtually no mem.

The freeze has never happened while I was working with the machine, and it also has never happen in Feisty (same setup) or in Vista.

Any ideas how I could trace down what's happening when I'm not watching my machine?

---

### Post by louieb on 2007-10-31
Are your fans working? Heat will cause a PC to lock up.

---

### Post by Rapax on 2007-10-31
Yes, acpi -t shows a nice constant temp of 22°C

---

### Post by Rapax on 2007-11-01
Here's something weird. I remembered that the day before it first happened, I had set up a user account for my wife on my machine.
I removed it yesterday morning, and so far....no freezes.

Can anyone make an educated guess about this being a possible cause, or maybe just dumb luck and coincidence?

---

### Post by buntunub on 2007-11-01
There are dozens of threads about this issue since Gutsy release. If you scan through them (via search engine) you will find that it ~might~ stem from powernowd misbehaving. It ~might~ be caused by kernel IO, which can be disabled. It could be caused by GPU overheats. It could be caused by faulty Nvidia/ATi drivers. It could be caused by Venus being in juxtaposition with Uranus on a full moon too. Nobody seems to have an answer. Nobody seems to even have half a clue of what could be causing this. However, ALOT of folks are experiencing it in varying degrees. It all seems to be Ubuntu specific as well.

---

### Post by Rapax on 2007-11-01
> **buntunub said:**
> There are dozens of threads about this issue since Gutsy release. If you scan through them (via search engine) you will find that it ~might~ stem from powernowd misbehaving. It ~might~ be caused by kernel IO, which can be disabled. It could be caused by GPU overheats. It could be caused by faulty Nvidia/ATi drivers. It could be caused by Venus being in juxtaposition with Uranus on a full moon too. Nobody seems to have an answer. Nobody seems to even have half a clue of what could be causing this. However, ALOT of folks are experiencing it in varying degrees. It all seems to be Ubuntu specific as well.

I did do a search, and I did look at those reports, however, it doesn't seem to be the same phenomenon. All the other reports claim that the freezes happen during heavy use, something I've never observed. Some also explicitly claim that it never happens during idle time, which is exactly when my freezes were happening.
Besides, After I removed my wifes account (that she never logged into, btw), my machine has been running flawlessly again.

---

### Post by Felipaus on 2007-11-01
What kernel are you using? Is your CPU a dual core one?
I've the same problem of you: Feisty OK, random freezes (hard reset only) with Gutsy (kernel 2.6.22.14).
I've a dual Pentium III mb ad I used the generic kernel  (I need SMP dual processor support). With i386 kernel no more freezes (but no SMP dual proc support; only one CPU recognized).
I hope a SMP fix in the new kernel will be released soon...

---

### Post by gunashekar on 2007-11-01
I had installed 7.04 and then later installed afresh 7.10 on my compaq presario V6000 laptop. Besides the problems with sound, the keyboard freezes quite frequently and I am forced to shutdown  (restart does not work) . 
I suspect overheating but the same does not happen on windows xp. 
wonder what could be the problem?

---

### Post by Rapax on 2007-11-04
Ok, my suspicion is confirmed. After deleting the extra user account 3 days ago, I didn't experience a single freeze (freezing every few hours before that).
Last night, I added another user account, and the freeze is back.

I am now convinced that this particular type of freezing is somehow linked to the existence of multiple desktop user accounts.
Any ideas how to go about fixing this?

---

### Post by FuturePilot on 2007-11-04
What graphics card do you have?

---

### Post by Rapax on 2007-11-05
> **FuturePilot said:**
> What graphics card do you have?

GeForce 8600 GT/PCI/SSE2

Do you think this may be a graphics card issue?
If I were to boot the machine into console mode only, with the second user account available, to see if it freezes, would that be a meaningful test?

---

