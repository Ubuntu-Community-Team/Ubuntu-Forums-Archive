---
title: "modprobe.d"
date: 2007-10-06
forum: General Help
---

### Post by ofb on 2007-10-06
I'm not sure how modprobe.d works in 7.04.

I have e100 installed, which is giving me trouble. So to experiment,

sudo rmmod e100
sudo modprobe eepro100

That works, but then I can't make it permanent.

The only default reference to these is in /etc/modprobe.d/blacklist,

# replaced by e100
blacklist eepro100

I've tried blacklisting e100 and un-blacklisting eepro100, and I've tried adding aliases based on old examples from when the kernel used modprobe.conf, and I've tried making strings based on examples in 'man modules.conf'.

I'm not having any luck. What /seems/ to be happening is both modules are loaded, so I get the same errors I got under default, plus a couple of new lines mentioning eepro100.

So, by this point I'd like to know a few things.

1) How should I do it, of course.

2) Just how is modprobe.d and module-loading supposed to work in 7.04 anyway?

I've read 'man modules.conf', but that's hard to follow for someone with zero experience. Partly there's the issue that the man pages haven't been fully updated yet. And partly the greater issue that man pages describe a command's syntax, but not the larger action(s) they're working on. So I have lots of questions, like how is the order the modules are loaded decided?

---

