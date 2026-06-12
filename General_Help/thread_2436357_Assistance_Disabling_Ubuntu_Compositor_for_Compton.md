---
title: "Assistance Disabling Ubuntu Compositor for Compton and i3wm"
date: 2020-02-04
forum: General Help
---

### Post by chris199 on 2020-02-04
Hello, I am attempting to use i3wm with Ubuntu 19.04 but I'm having some issues with screen tearing in both Chrome and Firefox that I do not experience when using the default environment. I've seen some materials online suggesting that the solution to this issue is to install Compton compositor but that I first need to disable the existing compositor before running Compton. It's not clear to me how to do this. When I enable Compton without this I encounter some severe errors so it seems that there is some other compositor running, I think the one included integrated in GNOME? I've read some things suggesting that it is no longer possible to disable compositing in GNOME. 

Does anyone have any suggestions on how I might be able to use i3wm tear free with my current Ubuntu installation?

---

### Post by wildmanne39 on 2020-02-04
Hi, 19.04 has reached EOL which means it will no longer have updates not even security updates, I recommend installing a supported release like 18.04 then if you want you can upgrade directly to 20.04 when it comes out in April.

---

### Post by chris199 on 2020-02-05
Thank you for the information, I have updated to 19.10 but I am still experiencing the same problem. When I enable Compton in i3 I am able to play fullscreen video and scroll websites without screen tearing, but I then experience a large amount of graphical glitches I believe related to the existing compositor not being disabled. Would you be able to point me in right direction to learn what I need to do to fix this?

---

### Post by yetimon_64 on 2020-02-05
The compositor for the gnome desktop is mutter. It should not be running if you are in i3 and the gnome DE is not running. Just to check if it is involved or not run the next code in a terminal while using i3 and compton...
```
ps -A | grep mutter
```
If the terminal returns to a prompt with no output, mutter is not involved with your problem.
I would be surprised if it is running _*without*_ the gnome DE being active.

I suspect _*with*_ gnome running you are right about not being able to disable mutter, it is pretty much essential when the gnome DE is actually in use from what I've read about it.

A fuller description of your "graphical glitches" would be helpful, either more detailed descriptions of or a screenshot of such if possible. Also posting your graphics  and hardware specs may help here as well.

Regards, yeti.

---

