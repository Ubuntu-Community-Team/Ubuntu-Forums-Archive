---
title: "Pressing &quot;Shutdown&quot; does nothing"
date: 2008-01-11
forum: General Help
---

### Post by pat_can_vault on 2008-01-11
Pressing "Shutdown" does nothing. Well, at least at first. Upon installing Gutsy for the first time, I press Shutdown and pop! up comes the options, Logoff, hibernate, Restart, Shutdown and Lock Screen. 

After having my system for a while, Installing beryl, and screenlets, When I press the Shutdown button, it takes about 10 minutes for the little box to pop up, and the "Lock Screen" and 'Hibernate" options are gone.

What do you suggest?

I have Ubuntu 7.10 
1gb RAM...
etc

---

### Post by p_quarles on 2008-01-11
Try disabling Beryl, and see if the problem changes. Do this by pressing alt-F2 and typing:
```
metacity --replace
```
This will at least help narrow down the source of the problem.

---

### Post by pat_can_vault on 2008-01-11
Nope, sorry, this changed nothing.

I thought I might add that this happened on a previous computer that had 7.10. It also ran the same stuff as me...

And about 3 hours ago, It 'randomly' came up as it should. Smiling, I pressed cancel, (because I actually didn't want to log off) then I'd see if it worked again but it didn't.

Also, when I press the button, my whole computer is frozen until it pops up.

---

### Post by danwood76 on 2008-01-11
How did you install beryl?
Are you using XGL or the standard xserver?

regards,
Danny

---

### Post by pat_can_vault on 2008-01-11
I'm not quite sure what you mean... (n00b)

I installed beryl using apt... from ubuntu.beryl-project.org

---

### Post by danwood76 on 2008-01-11
thats fine, if you had installed XGL then you would know about it as its quite difficult. it would cause shutdown button issues.
But you havent installed XGL so thats not it.

You could try removing beryl and using compiz fuzion instead which is the combination of compiz and beryl all in one nice package as the groups have now formed.

regards,
Danny

---

### Post by pat_can_vault on 2008-01-11
OK thankyou for your help!

In a previous post I'd said that the same thing had happened with my previous computer?

That was using compiz-fusion.
I'll still give it a try.

Thanks, pat

---

### Post by LeAstrale on 2008-01-11
if youre using a  standard 7.10 then there should be no problem, just remove your beryl and sudo apt-get install CCSM

that would give you the advanced control panel to control the desktop effects which you can set under appearences

---

### Post by nowshining on 2008-01-12
the waiting/freezing is a known Gutsy bug, it takes/should take about 1 minute to pop-up - hibernate and susspend too, i had it dissappear sometimes on me too, go to my website for a work around/fix on this in the tips/fixes and howtwos section. :) the site is in my sig.

---

