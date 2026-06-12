---
title: "Performance problems on fresh install of Feisty"
date: 2007-06-26
forum: General Help
---

### Post by richardq on 2007-06-26
I just backed up my dual boot xp/ubuntu box and wiped it clean, installing a fresh copy of Feisty (getting rid of XP entirely). However I have a few performance problems that are puzzling me:

My machine is a P4-3Ghz with 1GB of ram with Intel Onboard Graphics.

Some of the symptoms:

- Running the standard UI (metacity) is fairly sluggish. Dragging windows leaves artifacts. Resizing windows has large lag sometimes. This is on a fresh install with very few additional apps installed yet.

- I installed Beryl (since this is what I was running before) and performance of the UI was greatly improved. I've since removed it and installed Compiz-Fusion instead and the performance improvement is the same as with Beryl.

- The performance of the UI (either metacity or compiz/beryl) is inconsistent though. Sometimes it's dog-slow for a while and other times reasonably quick.

- Firefox is pretty darn slow to load pages. I've tried swiftfox with no improvement and I've also done the etc/hosts thing, and tried disabling ipv6 temporarily with no improvement. Again it's inconsistent, sometimes ok, most times dog slow.

- My dsl connection (I have a dsl modem, no router) seems to disconnect every 10 or 20 minutes. I thought it was doing that only when the sleep/screensaver became activated, but I've since seen it happen at other times. I have to do 'pon dsl-provider' in a terminal window to get it going again. That has never happened to me before. I've tried using opendns but that hasn't seemed to improve things.

I'm not sure whether the inconsistent performance and dsl connectivity are related or not.

However, on my dual boot setup, I used to always have an annoying problem with slow-loading of applications. That seems to have pretty much disappeared on this fresh install so it's not all bad news. ;)

I'm no linux expert, but quite comfortable fiddling with things. Any suggestions or pointers would be much appreciated.

---

### Post by richardq on 2007-06-26
I should also add that the performance of the desktop is perfectly fine using the LiveCD. It's runs significantly better and quicker than the installed desktop. Not sure if that info helps or matters.

---

### Post by cylent on 2007-06-26
I am experiencing similar problems even my mouse sometimes drags on.

my system specs are about like yours

p4 3.4Ghz
1 gig ram
installed ubuntu on a 40gig drive. (1.5gig swap)

I did disable all the CPU throttling options in the system bios and that mad a very minor improvement however the system is still sluggish. forget about using Beryl. its just not worth the time.

---

### Post by richardq on 2007-07-03
On my previous install on this machine (a Feisty/XP dual boot configuration) I had no problems running Beryl, but the performance hit with this up to date version of Beryl doesn't seem to work as well. I've found good performance now that I've removed it (and Compiz-Fusion) completely. I can live without it although I do enjoy it in small doses.

Big improvement I found was in going back to my old Xorg.conf file (I had saved it before the big reinstall) and matching up the settings. I found a major improvement by configuring Xorg for my specific monitor and video card. This included the screensize and refresh rates. The stock Feisty install had a generic monitor and generic video card as the default configuration. This ran poorly. Customizing it back to my hardware made a huge difference.

I can't remember where I found the info on fine-tuning the xorg.conf file but I will have a look and post back here if I find it.

---

