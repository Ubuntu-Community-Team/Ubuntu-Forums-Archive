---
title: "Display manager pops up after suspend"
date: 2014-07-27
forum: General Help
---

### Post by Bucky Ball on 2014-07-27
Hi all,

Odd one and still digging for a solution. 

* Just installed Ubuntu minimal 14.04 with xfce4 desktop environment on an old Dell D420 and everything runs great out of the box; wireless, graphics, sound, everything! It has a new lease of life;

The issue is trifling, but annoying. 

*When I close the laptop lid the machine suspends, fan goes off, screen goes dark;
* When I open the laptop lid, everything is as it should be; screen goes on, wireless comes up, all normal, except the Display GUI pops up (see attachment).

While I'd normally be happy to diddle around and tweak with this for awhile, the install is for a friend who starts uni tomorrow so need to hand over tomorrow or next day and want to kill any glitches. So far, this is the only one and I'd be happy to adopt this old crock when my friend gets her new computer later in the year! ;)

Any ideas? Further info, just ask, and thanks in advance for any clues. ;)

PS: Just for interest sake, this machine has a 1.8" hard drive! I've never heard of or seen anything like it. And the connection is also totally unfamiliar. Still working fine, though. :-k

---

### Post by Toz on 2014-07-27
Hi Bucky Ball.

I saw this on a system a little while ago. I believe that XF86DISPLAY is somehow being triggered on resume (acpi?). I wasn't able to find the root cause, but I removed the XF86DISPLAY keyboard shortcut from Settings Manager >> Keyoard >> "Application Shortcuts" and that at least supressed the dialog from appearing.

---

### Post by Bucky Ball on 2014-07-27
Hi and cheers, Toz. I'll give that a try tomorrow and report back. This is a minor annoyance in the scheme of things and I'm stunned at how well everything is working, I have to say. ;)

---

### Post by Bucky Ball on 2014-07-28
That seemed to work. I don't think I ever would have found that single-handedly. Cheers. ;)

---

