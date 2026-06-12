---
title: "Line spacing in Libre Office"
date: 2014-01-17
forum: General Help
---

### Post by Barney-R on 2014-01-17
This isn't really an Ubuntu problem, and it's more an irritation than a problem, but I'd like to find a solution.

Recently, when I open an existing document in Libre Office Writer, any new text I type is at one-and-a-half line spacing, though every setting I can find says it's set for single spacing, like the earlier portions.

It's hardly a life-threatening situation, but it's annoying, and I'd appreciate any advice as to how I can restore my documents to single line spacing.

Ubuntu 12.04, last updated January 13th 2014.

---

### Post by ajgreeny on 2014-01-17
Try a new configuration for LO by renaming the old one at **~/.config/libreoffice** as a backup and see if that overcomes the problem.That will give you a default setup, so if you have customised the layout of the different toolbars for writer, calc, etc etc, you can copy them over from the old renamed version to the new one.  By default the configs are at **~/.config/libreoffice/4/user/config/soffice.cfg/modules/**

If you are still using LO 3. instead of LO 4, your configuration files will be in a differently named pathway, but I'm sure you will be able to find them easily enough.

---

### Post by Barney-R on 2014-01-28
Thanks for that, ajgreeny, and please accept my apologies for the late response. Sometimes life gets in the way.

I'm a bit reluctant to try the solution you suggest because I've made a few changes (don't show history being one) and don't remember how I went about it, but I'll certainly keep it in mind in case things go disastrously wrong in the future.

I've had to do the same thing with FireFox a couple of times when it became infected with the adf.ly hijacker.

What's happening is that I've got a few documents that need to be added to from time to time, and I use horizontal lines to keep the additions separate.

If I type the new text **above** the line (then add another line above it), I keep the single line spacing, but sometimes (only sometimes) if I type **below** the line, it switches to 1.5 line spacing and nothing I do will change it back.

It's an annoyance, so I'll keep struggling with it, but it's hardly life-threatening.

---

