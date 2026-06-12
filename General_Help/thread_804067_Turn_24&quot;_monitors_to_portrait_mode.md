---
title: "Turn 24&quot; monitors to portrait mode?"
date: 2008-05-22
forum: General Help
---

### Post by renolinux on 2008-05-22
Hi all, I have a Dell workstation that is dual core with 2gb ram, Quadro FX 550 video card and two 24" dell wide screen monitors. I currently run them at 1900x1200 each. I am using nvidia's software to make it all work.

Kubuntu 8.04 runs nicely on it and I am generally happy. These are rather high end Dell monitors and they have the ability to be turned sideways so that they are taller than they are wide. I'd like to be able to run both monitors in this configuration to make better use of my desktop space. Having  a 40" wide monitor set up is just about too big! Never thought I'd have to say THAT. But my employer supplied me these monitors for my workstation, so here I am.

So... how do I make that work? I'd imagine I'd have to reconfigure /etc/xorg.conf in some way, but I have *no* idea about it.

Thanks a lot!

---

### Post by renolinux on 2008-05-23
I figured it out! [http://ubuntuforums.org/showthread.php?t=301380&page=3](http://ubuntuforums.org/showthread.php?t=301380&page=3) that thread had me add the "Option "RandRRotation" "On"  sections. Then I was able to rotate them. I had to trick X by saying that the right monitor was on TOP before it would let me use the monitors side to side correctly. 

THIS is going to take some getting used to.

---

### Post by PinkFloyd102489 on 2008-05-23
Well you have to think. It rotates clockwise so the original top is now on the right. But X still sees it as being on top.

---

### Post by renolinux on 2008-05-24
Yep, that's exactly right. It works beautifully and having better use of all that desktop space is great. Its one huge square! :)

---

