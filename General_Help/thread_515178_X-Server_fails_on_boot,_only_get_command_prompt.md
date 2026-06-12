---
title: "X-Server fails on boot, only get command prompt"
date: 2007-08-01
forum: General Help
---

### Post by samuraizebra on 2007-08-01
Ok I know this is a bit of a regular topic. But I've looked hard and I can't find the solution to my specific problem.

I've installed Ubuntu 7.04 Desktop on a standard x86. Just so you are aware - I don't get this problem when I use the 7.04 Live CD .... 

Anyway, as I was saying, now that I've installed Ubuntu to a new partition (sharing my HDD with Win XP Pro) I can't boot into GUI Ubuntu (or whatever you call it) I get a load of messages about the X-Server failing to load and asking if I want more details. Basically I can get back to a command prompt, but from there I can't even begin to think how to go about fixing this problem.

All other threads and tutorials take you through being able to use Ubuntu "properly" - the way us GUI-loving noobs like it - to install/update missing drivers.

I can't get that far so any of that help is useless. As mentioned before I can boot into Ubuntu off a Live CD (which is great and really makes me want to fix this problem!!) - but even this doesn't help because I can't seem to make any lasting changes to the installed file system as i never have enough access!

I'm really desperate to gt this fixed. Please help?

---

### Post by merlinus on 2007-08-01
At the command prompt, type sudo dpkg-reconfigure -phigh xsever-xorg

Then select vesa as your video driver and use the space bar to select the resolution.

Then reboot.

Once in ubuntu, do a search for the drivers for your video card, or continue using the vesa driver.

-merlin

---

