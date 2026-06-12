---
title: "Where are the scientific calculators?"
date: 2016-06-20
forum: General Help
---

### Post by George_Ross on 2016-06-20
I recently installed Ubuntu 16.04 64-bit & can't find a good scientific calculator. When I had Ubuntu 11.10 you could check on "scientific mode" from the drop down menu but not now. I can't find other calculators in the Software section that includes it either. 

Doing some searching I found & installed Galculator which was said it should look like this;
[ATTACH=CONFIG]269670[/ATTACH]

but instead looks like this (Note the absence of drop down menu) 
[ATTACH=CONFIG]269672[/ATTACH]

I tried to update/reinstall with Synaptic Manager but nothing changes. At least Synaptic Manager says what version the software is.
[ATTACH=CONFIG]269671[/ATTACH]

Last, I found a tar.gz version (Galculator_1.3.1) that fails to install. Seems dependencies are missing & I went on an endless chase to satisfy these.

To sum it up, all I want is a simple scientific calculator. Galculator seems like a workable one but maybe it's not installed properly. 

Any suggestions?

---

### Post by Linuxisfast on 2016-06-20
Try qalculate-gtk, its the best all in one tool from scientific to alegra, calculus, analysis, comp science and more including conversions. sudo apt install qalculate-gtk

---

### Post by mcduck on 2016-06-20
The default Gnome calculator has basic, advanced, programming and financial modes. Maybe your problem is actually that the global application menus aren't working? I assume you did try opening the menu from your top panel (where it's located instead of the program window itself like in the old days...)

Anyway, I agree with Linuxisfast, Qalculate is great, worth having around even if you find the missing menu of the default calculator...

---

### Post by George_Ross on 2016-06-20
[COLOR=#000000]Thanks mcduck! How about that? I never noticed the top menu but there it was.

[/COLOR][ATTACH=CONFIG]269683[/ATTACH]

---

### Post by mastablasta on 2016-06-21
speedcrunch is another option

---

### Post by George_Ross on 2016-06-21
Thanks mastablasta, I'll try them both.

---

### Post by mastablasta on 2016-06-22
although i just checked latest speedcrunch seems to be without the pad (buttons). maybe not really needed on keyboard?! but they shoul dbe there to use on touch devices. strange why they did that. version 0.10 had them. maybe it's just me that can't find them...

edit... found why it's gone:
> Now for some bad news for some of you: the virtual keypad is gone. The reason for this is that it goes against the SpeedCrunch philosophy and main goal - to be a keyboard-oriented, fast to use scientific calculator. The old keypad was both ugly and not very functional. I'll consider re-adding a keypad in the future IFF a significant user base asks for it and a good and scalable design is found. I see this feature in the same category and usefulness as RPN support.

so 0.10 has it,  0.11 keyboard oriented and doesn't have it.

---

