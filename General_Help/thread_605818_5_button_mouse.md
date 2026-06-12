---
title: "5 button mouse"
date: 2007-11-07
forum: General Help
---

### Post by Angry penguin on 2007-11-07
I am currently running feisty and my 7  button logitech mx500 mouse doesn't have full functionality. I have tried every guide on this forum it seems like. I'm just trying to get the forward and back buttons to work in firefox and nautilus. 

The problem is, when I run xev to find how my buttons are mapped, buttons 6 & 7 both show up as button 6, even though they are two separate buttons, xev detects them as the same button. 

Logic would dictate that if you can't even differentiate between two buttons, you can't map them to separate keyboard presses.

Soooo... am I screwed here or what?

Thanks in advance.

---

### Post by linuxwizard on 2007-11-07
Have you looked at this one.

[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

---

### Post by jamesford on 2007-11-07
u should check out btnx, search the forum for it as well as this site [http://www.ollisalonen.com/btnx/](http://www.ollisalonen.com/btnx/)

---

### Post by Angry penguin on 2007-11-14
If I understand this properly, Linuxwizard. I need to know where the buttons are currently mapped, so that I can properly assign them in imwheel. To do that, I use xev. XEV shows that buttons 5 and 6 are the same button, when indeed, they are not. This leads me to believe that it is a problem with the way Ubuntu, or some part of it, detects my mouse button presses and NOT a problem with the way they are mapped.

Correct me if I am wrong, because I really want to understand this so that I can fix the problem and not just stick a band-aid on it for now.

Jamesford, I will give that a shot and let you know if it works.

Thanks all.

---

