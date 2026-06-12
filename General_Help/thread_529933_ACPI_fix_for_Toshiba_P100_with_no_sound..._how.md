---
title: "ACPI fix for Toshiba P100 with no sound... how?"
date: 2007-08-19
forum: General Help
---

### Post by sargant on 2007-08-19
I've been poking around the internet most of today and seem to almost have this nailed, except the last step has gone way, way into the realms of Stuff I Haven't Got A Clue About (this is my first day of using linux, so I am a total newbie!)

I have a Toshiba P100-216 (PSPADE) + BIOS 3.50 which suffers from the soundcard/ACPI problems that people have posted everywhere already, and the fix appears to be "custom DSDT files".  Using acpi=off on boot also works.  I've had a poke about [http://acpi.sourceforge.net/](http://acpi.sourceforge.net/) and I am now left stumped with the fact my model isn't listed (nor is a similar model, P100-434)

Is there an existing DSDT file for my laptop on this machine already, and is it possible to just cut&paste a hack into that file, or could I use any vaguely-similar looking file off that website and give it a try safely?

---

### Post by sargant on 2007-08-20
Right, I've got slightly further but I'm now up against a brick wall

I've followed the tutorial here: [http://www.linuxquestions.org/questions/showthread.php?t=531575](http://www.linuxquestions.org/questions/showthread.php?t=531575)

But I'm now stuck at step 6, specifically I get this error:
"/etc/sysconfig/kernel: no such file or directory"

Any help please?

---

### Post by sargant on 2007-08-20
Turns out ubuntu-specific instructions were further down the page.  Never mind then, all fixed!

---

### Post by reticentae on 2007-08-28
Where on the page are the ubuntu specific instructions? I could not find them...

---

### Post by sargant on 2007-08-28
Post #11:

[http://www.linuxquestions.org/questions/showpost.php?p=2773589&postcount=11](http://www.linuxquestions.org/questions/showpost.php?p=2773589&postcount=11)

I think this still leaves issues with the GPU fan though and problems with overheating, so I've got rid of ubuntu for now.  Somebody has created a fix for it [here]("http://www.nvnews.net/vbulletin/showthread.php?t=75995&page=2") so I'm going to do a diff against his file and my own and see what changes he made.

I'm also getting a creative audigy notebook soundcard soon, which may of course make all this ACPI nonsense irrelevant!

---

### Post by reticentae on 2007-08-28
Ah, found it. Thankyou!

Works great now on Toshiba P100-A3A (PSPA3A), sound!, finally sound! (without acpi=off that is)

I don't know about the fan or overheating though, everything seems to be working fine at the moment in that department, unless its something I'm not aware of...

---

