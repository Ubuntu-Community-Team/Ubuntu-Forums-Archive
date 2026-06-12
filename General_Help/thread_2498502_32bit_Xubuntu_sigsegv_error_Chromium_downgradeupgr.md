---
title: "32bit Xubuntu sigsegv error Chromium downgrade/upgrade?"
date: 2024-06-16
forum: General Help
---

### Post by v47 on 2024-06-16
ooh looks like I actually have an account here, nice.

anyway, I have a fairly simple task at hand - get an old 32bit atom pc up and running (it technically can run win10 32bit, but uhh, it's.. not great), and the only extra thing that I need there is the Chromium browser with acceleration enabled. so, Xubuntu 18.04, updated to max (makes it 18.04.6), and the last official Chromium build loaded via software center.. aand [that build is busted]("https://support.google.com/chrome/thread/67845533?hl=en") (he is doing something slightly different but I've checked this on 3 different 32bit machines, same problem).

so the question becomes, how do I get a Chromium build loaded there which does not suffer from that issue. doesn't really matter too much whether it's a bit older, it just needs to work (a newer, or rather, the newest 32bit build would be preferable if it exists, but I'll take what I can).


[FONT=Verdana]//solution: did a clean install of 18.04, let it fully update (redundant packages removed and language support updated last) downloaded the latest 18.04 32bit Chromium build from [here]("https://launchpad.net/ubuntu/bionic/i386/chromium-browser"), [/FONT]rightclicked [FONT=Verdana]to install via sw center (few complains about some fw not being available but it continued), everything completed ok and the browser works with acceleration enabled. adblock plus is not compatible anymore (probably abandoned 32bit support) but no matter, just installed the second most downloaded ad blocker (adblock ultimate) and looks like all is set and good to go.[/FONT]

---

### Post by tea for one on 2024-06-16
> **v47 said:**
> anyway, I have a fairly simple task at hand - get an old 32bit atom pc up and running 
Not such a simple task because many distros do not issue 32-bit iso files.
Xubuntu 18.04 reached end of life in April 2021.

Try an internet search for supported 32-bit distributions - they still exist but not within the Ubuntu family.

---

### Post by v47 on 2024-06-16
yes, but it still installs and updates fine, so as long as I can get a working Chromium build loaded, I'm all set.

---

### Post by guiverc on 2024-06-16
I'll agree with what *Tea for One* has already said.

The only 32-bit architecture that Ubuntu now supports is 32-bit ARM (ie. *armhf*).

Ubuntu 18.04 LTS reached EOL for *i386* in 2023-May, being the last supported system for 32-bit x86 (*what Debian & Ubuntu both refer to as **i386*).

I still use *i386* devices myself (*and one is an old eepc using intel atom*), and I just moved my installs over to Debian....

The actual Debian *release* I use does actually vary based on the GPU of each device, as I found some GPUs (esp. on IBM Laptops) did better with the older kernels, but given Debian *buster* (10) is approaching its EOL *extremely soon!* those systems will soon be upgraded to *bullseye* (11) anyway, so I'd just install *bullseye* (11) now.

---

### Post by v47 on 2024-06-16
yes, I'm quite aware of all of that. but the question actually is whether I can get a working Chromium build loaded onto what I currently have there.

so for example, according to the guy I've linked, Chromium 84.0.4147.125 should still be ok. can I get it from somewhere? if I can, how can I install/load it? his post also says he did downgrade to that build, so this should be possible.

> **guiverc said:**
> I'd just install *bullseye* (11) now.
this is probably going to be my long term solution, but right now, if I can just get Chromium working quickly then that would be enough for a while.


//ok, so it seems [this]("https://askubuntu.com/questions/1222180/how-to-install-specific-version-of-chromium-on-ubuntu") is exactly what I need, so guess I'll try that.

//turned out to be incredibly easy - did a clean install of 18.04, let it fully update (redundant packages removed and language support updated) downloaded the latest 18.04 32bit Chromium build from [here]("https://launchpad.net/ubuntu/bionic/i386/chromium-browser"), rightclicked to install via sw center (few complains about some fw not being available but it continued), everything completed ok and the browser works with acceleration enabled. adblock plus is not compatible anymore (probably abandoned 32bit support) but no matter, just installed the second most downloaded ad blocker (adblock ultimate) and looks like all is set and good to go.

this is not a permanent solution (at one point, there will be no more updates and the browser will inevitably cease to display web properly), but should be good for a couple of years.

---

