---
title: "Pro/Engineer problems after Feisty upgrade"
date: 2007-04-13
forum: General Help
---

### Post by hambone79 on 2007-04-13
I have a Dell M70 laptop running Kubuntu. I originally set it up with Edgy and everything worked fine with Pro/Engineer. Now that I have upgraded to Feisty via dist-upgrade, I'm having problems with panning, zooming, and rotating in Pro/E.

For some reason Feisty causes a delay in Pro/E recognizing my mouse movements. When I attempt to pan/zoom/rotate there is about a 1-2 second delay in Pro/E making a movement. Pro/E appears to respond quickly other than this one little issue so I assume it is something to do with the way Feisty handles input.

---

### Post by hambone79 on 2007-04-13
One other thing I just noticed....

In Pro/E you use the middle mouse button (scroll wheel on most mice) and the CTRL/ALT keys to pan/zoom/rotate. I accidentally held down the scroll wheel like I was rotating a part as I was passing the mouse pointer over a Konsole window. When I did this I get this output:

```
vj928@jarrod-laptop:~$ slow rotationslow rotationslow rotationslow rotationslow rotationslow rotationslow rotation
bash: slow: command not found
 
```

Ever time I moved the mouse I got the "slow rotation" spit out on the command prompt.

---

### Post by hambone79 on 2007-04-13
Ok, I think the middle mouse is attached to a paste function some how. After playing around some more, I can hit the middle mouse button in a text editor or any program where I can input text and it will past the last thing I copied.

Does anyone know how to turn this feature off? I think this is probably what is causing my problem.

---

### Post by hambone79 on 2007-04-13
Scratch my previous post. The problem appears to be related to slow response to mouse events inside of Pro/E.

---

