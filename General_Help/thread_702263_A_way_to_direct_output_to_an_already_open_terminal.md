---
title: "A way to direct output to an already open terminal?"
date: 2008-02-20
forum: General Help
---

### Post by chochem on 2008-02-20
I'm running the [tilda]("http://tilda.sourceforge.net/") terminal directly on my desktop and love it to bits. However, I was wondering: Is there a way to run a command (e.g. by way of a keybaord shortcut) that will direct the output to tilda (e.g. having the MPC playlist written out)? I can easily identify the terminal window in a program like wmctrl but that doesn't help me with producing output.

---

### Post by freelinuxhelp on 2008-02-20
The tee command might work for you here. you can find out what psudoterminal tilda is using and redirect stdout to the pts.

---

### Post by chochem on 2008-02-21
Thanks for the tip :) Sadly, it works from terminal 2 to terminal 1 (tilda) but not from a run dialog or a keyboard combination but that's probably an issue with the way keyboard shortcuts work. Thanks again.

---

