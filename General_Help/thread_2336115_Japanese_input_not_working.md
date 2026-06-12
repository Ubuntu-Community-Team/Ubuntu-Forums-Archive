---
title: "Japanese input not working"
date: 2016-09-04
forum: General Help
---

### Post by goemonburo on 2016-09-04
I am an English speaker who often writes in Japanese to friends, etc.  I am finding that my Lubuntu 16.04.1 LTS install has a weird bug that's frustrating the hell out of me:  it doesn't seem to remember my switching the input method from the default, "none," to fcixt or ibus.   Nearly all the instructions I can find online say "Go to Preferences, Language Support, and choose either ibus or fcixt, logout, then log back in."

But when I do that, the same "none" is back, always preselected.  Any settings I change require relogging in...which means they vanish.

I can see the nice input window sitting there.  But it just doesn't DO anything...I hit "cntl-space" and it appears or disappears, but never allows me the option to write anything but English/romaji.  

Anyone know what's causing this?  

Thank you!

---

### Post by goemonburo on 2016-09-05
Okay, so I solved this by "sudo gnome-language-selector":  for some reason as a regular user I didn't have permissions to write to whatever appropriate config file was needed.  Pretty lame, but at least I can now type &#26085;&#26412;&#35486; (nihongo) when I need to!!!  Whew!!

---

### Post by RobGoss on 2016-09-05
Glad you found a fix for your problem would you mind marking this thread as solved you can do this by using the **Thread** **Tool **tab at the top of this post Thanks so much

---

