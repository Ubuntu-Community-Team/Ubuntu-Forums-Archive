---
title: "Slow, stalled shut down/ power off 16.04"
date: 2017-05-09
forum: General Help
---

### Post by zoe-scutterbug on 2017-05-09
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]Hi folks

I am running Ubuntu 16.04 xenial on a ZOTAC ZBOX-EN1070
[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]           Desktop: Cinnamon 3.4.0 (Gtk 3.20.8) dm: lightdm 
System: Kernel: 4.8.0-51-generic x86_64 (64 bit gcc: 5.4.0)

[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
When i try to turn off my computer.
The screen goes blank, but the light on my little zotac box stays on for about 2 minutes before it actually closes down.

 It use to take about 5 seconds.

I have been trying to fix this for days, i have tried editing grub but it did not work.
I’m a very basic level user, with minimal code knowledge and a poor memory.


 I would appreciate any recommendations help?

 Thank you.

---

### Post by zoe-scutterbug on 2017-05-13
This fixed my problem

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1521173](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1521173)


The  bug description contains a work around, which should solve your  problem.

---

