---
title: "boots fine and works in graphical mode, but hangs while producing output in text mode"
date: 2007-09-21
forum: General Help
---

### Post by Keyper7 on 2007-09-21
Hi,

I have a HP Pavilion DV6258se (Turion X2, NVIDIA GeForce Go 6150) and I've installed Feisty 64
on it. Currently, I'm working for ways to boot without the noapic parameters. I've had relative
success with some workarounds but today I faced something I wasn't expecting.

While currently I have a quite stable system in graphical mode, I'm experiencing hangs in text
mode. They are quite easy to reproduce: all I have to do is switch to a text terminal and
execute something that produces a lot of output (ex: dmesg or ls -l in a directory with lots of
files). The system then just hangs in the middle of the output. The text cursor keeps flashing,
but I can't switch terminals, go back to graphical mode or anything. I have to hold the power
button. This does not happen in a terminal window in graphical mode.

I can confirm that this does not happen at all if noapic is enabled, but this is not an acceptable
workaround for me right now (several topics about that already).

Did this happen to anyone else around here?

Thanks.

PS: I also have fsck hanging in a random percentage (usually between 70% and 80%)
unless noapic is used... perhaps the two issues are related?

---

### Post by Keyper7 on 2007-09-21
Ah, it seems I'm not alone after all:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/112775](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/112775)

Unfortunately, it seems there's no solution yet. :(
Suggestions?

---

