---
title: "Refresh Rate problems"
date: 2007-01-23
forum: General Help
---

### Post by itguy12 on 2007-01-23
I have just installed Ubuntu 6.10 on a Dell Dimension 1100, which also have Win XP installed as well so I'm in a dual boot scenario. When I choose to boot Ubuntu, my Pixelvision 17" FP monitor show "out of range" on the screen when Ubuntu gets to the GUI. However, when I boot into Win XP it is fine. Win XP is set to 1024 x 768 at 60hz. When I hook my this PC to a regular CRT monitor and go to Ubuntu's Screen Resolution options, I can change the resolution to what I need, but the only refresh rate option is 75hz. I'm pretty sure the FP monitor will work @ 60hz but it's not a option. How do I get this to be an option? I'm new to Linux so any help would be great!

---

### Post by yopnono on 2007-01-23
> **itguy12 said:**
> I have just installed Ubuntu 6.10 on a Dell Dimension 1100, which also have Win XP installed as well so I'm in a dual boot scenario. When I choose to boot Ubuntu, my Pixelvision 17" FP monitor show "out of range" on the screen when Ubuntu gets to the GUI. However, when I boot into Win XP it is fine. Win XP is set to 1024 x 768 at 60hz. When I hook my this PC to a regular CRT monitor and go to Ubuntu's Screen Resolution options, I can change the resolution to what I need, but the only refresh rate option is 75hz. I'm pretty sure the FP monitor will work @ 60hz but it's not a option. How do I get this to be an option? I'm new to Linux so any help would be great!

Don't know what graphic card you have, but you can always use modeline 'gtf' or some online tools or 'xvidtune'

[http://doc.gwos.org/index.php/ChangeResolution#Adding_custom_modeline](http://doc.gwos.org/index.php/ChangeResolution#Adding_custom_modeline)
[http://www.bohne-lang.de/spec/linux/modeline/](http://www.bohne-lang.de/spec/linux/modeline/)

---

