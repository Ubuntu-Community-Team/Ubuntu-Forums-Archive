---
title: "Freezeups"
date: 2007-10-10
forum: General Help
---

### Post by ph8 on 2007-10-10
hey guys, feisty randomly locks up on my quad core, 4gb ram system - i'll be plodding along fine then sound will fail (start looping repeatedly over the same 1 second period) then the mouse/keyboard will stop working - where do i start debugging? no  obvious error msgs

i've already tried things like running with noapic to no avail :( It's almost like all the USB devices are deactivating spontaneously

---

### Post by dabl on 2007-10-10
Couple of notions for you:

1. If you weren't aware, it sounds like you need to know about "raising skinny elephants". :)

No need to subject your system to a hard power-off cycle, when it appears to be "frozen".  In fact, a little bit of the keyboard may actually be functional, even if the screen feedback isn't.  So, when you are hearing that little 1-second sound loop, and looking at a non-responsive screen, press Alt and SysRq (aka "PrtScn"), and while holding them down, press in sequence R S E I U B.  "_R_aising _S_kinny _E_lephants _I_s _U_tterly _B_oring"

This should trigger a graceful shutdown/warm restart.

2. I'd be suspicious of the x configuration (which includes keyboard and mouse setups).  There's a log file at /var/log/Xorg.0.log.  After your next re-start event, open the last backup of it, and examine the tail end of it.

HTH!  :)

---

### Post by brundlefly76 on 2007-10-10
> **ph8 said:**
> hey guys, feisty randomly locks up on my quad core, 4gb ram system - i'll be plodding along fine then sound will fail (start looping repeatedly over the same 1 second period) then the mouse/keyboard will stop working - where do i start debugging? no  obvious error msgs

i've already tried things like running with noapic to no avail :( It's almost like all the USB devices are deactivating spontaneously

Wow, I just registered on the forums for the first time to get help with the same or similar issue.
I've been using Linux for 12 years and I can usually always find a solution somewhere, but I dont have many leads on this one.

I mostly use my Feisty install from a SecureCRT terminal in the same room, which has been my main interface to Linux since Ive been using it.

Recently, however, and it seems like maybe after an routine update, my terminal will become unresponsive for 3 seconds or more - its hard to tell because I have to be typing to notice, and most of the time I am reading code.

I thought this might be a network issue, but it happens on the raw console as well.

Examining top(1), all seems quiet, except that I do see user tomcat5 jumping in and out with a high-cpu java process now and then. I have never done java web development so I dont know what the relevance of this is, and am not entirely certain it is the problem.

It is extremely unusual, as I have used dozens of distros and never experienced this problem on an otherwise fine unloaded box with ample system resources.

---

### Post by brundlefly76 on 2007-10-10
As a side note, I just noticed that if I run top(1), I will lose the session entirely and get disconnected (!)

---

### Post by ph8 on 2007-10-11
Raising Skinny Elephants does indeed work during lock up, thanks for that! You learn something everyday!

I still can't narrow down the original problem though, i believe that in ctrl+alt+f1 console i see the errors /dev/sr0 - input/output buffer error - is this my sound card? If so i think this could be a symptom rather than an indication of the actual problem!

Henri

---

### Post by ph8 on 2007-10-13
Freezeups are kept to a minimum if i don't run amarok (but i still watch a lot of vids in kaffeine/vlc/xine) and don't watch any vids as they're downloading (but rather wait until they're 100% finished)

Still no idea how to fix it!

---

### Post by PmDematagoda on 2007-10-13
I had the same problem once with my Ubuntu installation where the problem escalated until the whole system stopped working properly, I fixed it once by cleaning the memory modules a bit, when that didn't work the second time I had that problem, I changed their location to another slot or channel after which the problem got solved, you might have the same issues as well.

---

### Post by tgalati4 on 2007-10-13
If you have dust in your machine or a cooling problem, then it could be your Southbridge chip acting up.  If you are using on-board sound, the sound chip is normally contained in the Southbridge.  When it gets hot, strange things happen.

It could also be a power supply problem.  Momentary drops in power can cause strange behavior.

---

### Post by ph8 on 2007-10-13
I've got an absolutely immense 1KW power supply in the machine, although it's entirely possible that the machine is sensitive to regional variations in power i suppose? I had very few of these issues over the summer in one lot of student accomodation but it happens here (in other student accom) and at my home

So it is almost definitely hardware related? I might try just swapping the memory pairs around later, does that sound right? They're paired up in a sort of ABAB formation if memory serves - please do let me know if it sounds like i'm talking crap, still learning :p

---

### Post by HermanAB on 2007-10-13
The annoying periodic 3 second freezeups is a different issue.  It is most likely caused by your CDROM drive not being supported properly by the Hardware Abstraction Layer.  The solution is to replace the CDROM drive with a modern one, or to kill hald-addon-storage.

Cheers,

H.

---

### Post by PmDematagoda on 2007-10-13
> **ph8 said:**
> I've got an absolutely immense 1KW power supply in the machine, although it's entirely possible that the machine is sensitive to regional variations in power i suppose? I had very few of these issues over the summer in one lot of student accomodation but it happens here (in other student accom) and at my home

So it is almost definitely hardware related? I might try just swapping the memory pairs around later, does that sound right? They're paired up in a sort of ABAB formation if memory serves - please do let me know if it sounds like i'm talking crap, still learning :p

Yes, you can try that, it may be something wrong with a slot or a memory module, or just a problem concerning too much dust in your CPU:).

---

### Post by ph8 on 2007-10-19
This problem is fixed in Gutsy - assuming it was a kernel issue

Thanks for all your help

---

