---
title: "3 Ubuntu Wishes."
date: 2008-02-29
forum: General Help
---

### Post by Megabreath on 2008-02-29
ok so I've installed Ubuntu and smoothed out all the problems such as graphics and sound cards, but there are 3 things I haven't been able to get my head around, and need a step by step solution because I am very lost. :confused:

1. this is probably the most important of my problems, no sound from firefox while playing any flash videos, I've tried to look around the forum for solutions but I seriously cant get my head around to what exactly do I have to type in or download to fix this problem, any suggestions?

2.probably the least urgent problem but it would be nice to fix it, I have a 5 button mouse and just need to know how do I get the other two ones working, for example a back and forward button.

3. how do I get beryl and is it free?

---

### Post by masque7 on 2008-02-29
> **Megabreath said:**
> 3. how do I get beryl and is it free?
right-click your desktop
go to visual effects
chech the bottom one option... custom
then once you've done that there's a 'box' next to custom
you can configure compiz (was beryl) in there

i'll get back to you on the others

---

### Post by Megabreath on 2008-02-29
hm... no beryl box in sight, but i'm not very concerned, it's no 1 I seriously need to sort out.

---

### Post by PreviousN on 2008-02-29
Beryl is free, but it has recently remerged with compiz to form a set of extensions known as compiz-fusion.

The bottom line is that yes, its free, and yes, its' available. I'll help you out if you could tell me which type of graphics card you've got. 

Search for a program called "envy"...or rather, I'll search and post the link...
[http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu4_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu4_all.deb)

Install that deb. If you want to read about the website, here's the main link: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Anyways, upon running that, you should be able to choose to install the driver for whichever gpu you've got. If you've got NVIDIA, choose automated nvidia, if you've got ati, choose ati.

Then enter your password and just let it do its think. Press the enter key when prompted. Then, upon completion, it'll ask you to write the xorg.conf. Do it (make a backup first if you need, if you don't, its simple to revert to a new one by using deb reconfigure). 

Anyways, upon completion of the restart, you can go to:

System > Preferences > Appearance > Visual effects 

And choose what you want. If it works, then great!

---

### Post by SOULRiDER on 2008-02-29
You didnt say what Ubuntu version it is you were using.

For your first issue i found this:
[http://ubuntuforums.org/showthread.php?t=364121](http://ubuntuforums.org/showthread.php?t=364121)

About beryl:
Beryl was a fork of compiz but the two projects merged back and created compiz fusion. Compiz fusion is currently installed by default in 7.10, but you can install the compiz-gnome package to be able to cusotmize it all you want. to do so just do
```
sudo aptitude install compiz-gnome
``` in a terminal. You can now configure everything fromt he preferences menu.

---

### Post by Megabreath on 2008-02-29
I think i'm using fiesty.

Edit: ok beryl is done, thanks all.

But as for the sound, I really cant get my head around these solutions, I should had stated I have the most bare basic knowledge of ubuntu. -_-

---

### Post by SOULRiDER on 2008-02-29
Are you running 32 or 64 bit Ubuntu?

---

### Post by SOULRiDER on 2008-02-29
Check out post #5 in [http://ubuntuforums.org/showthread.php?p=3446685](http://ubuntuforums.org/showthread.php?p=3446685)
Everything around code tags should be pasted in a terminal.

---

### Post by Nemooo on 2008-02-29
For the mouse button question, there's a solution here:

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Microsoft_Intellimouse](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Microsoft_Intellimouse)

If you scroll down there's also solutions for the MX510 and MX518.

---

### Post by Achtung on 2008-02-29
If the last solution didn't help for your mouse problem, look into btnx:
[http://ubuntuforums.org/showthread.php?t=455656](http://ubuntuforums.org/showthread.php?t=455656)

---

### Post by Megabreath on 2008-02-29
> **SOULRiDER said:**
> Are you running 32 or 64 bit Ubuntu?

32.

---

