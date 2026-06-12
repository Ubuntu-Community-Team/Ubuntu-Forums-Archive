---
title: "Invisible windows in Ubuntu"
date: 2008-03-22
forum: General Help
---

### Post by stiansoftcore on 2008-03-22
Hi, I went on searching for "desktop dimmer", and found *this [http://ubuntuforums.org/showthread.php?t=523837](http://ubuntuforums.org/showthread.php?t=523837) * thread. I did something there, and now all my Ubuntu windows are invisible, like this:
[IMG]http://i25.tinypic.com/20ha2h.png[/IMG]

How can I reset this? Because it's really hard using Ubuntu with alle the windows invisble and all, I barely managed to take a screenshot and restart my computer =/

What I mainly did, was
*Open CCSM
*General Options
*Opacity settings
*Changed the Opacity value to 100 (yeah, just laugh)
* Did this "Toolbar | Utility | Dialog | ModalDialog | Fullscreen | Normal | Desktop" (don't remember where the place to put it is named, but I guess you understand)

Somebody? Thanks :)

---

### Post by Tomatz on 2008-03-22
Disable the 3d windows plugin in ccsm :)

[edit]

Sorry didn't read correctly. Just click the brush buttons next to the values you changed in ccsm to reset to defaults :)

---

### Post by stiansoftcore on 2008-03-22
> **Tomatz said:**
> Disable the 3d windows plugin in ccsm :)

[edit]

Sorry didn't read correctly. Just click the brush buttons next to the values you changed in ccsm to reset to defaults :)

hehe.. yeah. I wished it was that easy, only problem is, that I cant navigate through CCSM.. Beacuse the window is kind of invisible? :P

---

### Post by Tomatz on 2008-03-22
> **stiansoftcore said:**
> hehe.. yeah. I wished it was that easy, only problem is, that I cant navigate through CCSM.. Beacuse the window is kind of invisible? :P

Duh lol

you could do it from recovery mode 

or open a (invisible) terminal and type:

killall compiz

:)

---

### Post by stiansoftcore on 2008-03-22
> **Tomatz said:**
> Duh lol

you could do it from recovery mode 

or open a (invisible) terminal and type:

killall compiz

:)

already tried killall compiz, nothing happened. When I've used f.ex "killall wine" before, it says "Wine: no processes were killed" =/

But I'll try recovery mode =)

---

### Post by stiansoftcore on 2008-03-22
What do I do in recovery mode? Can't understand a thing.. Help!! :confused:

---

### Post by walkerk on 2008-03-22
Not too sure where compiz's settings folder is as I don't use it but perhaps ~/.Compiz

You could rename that folder so the options won't be loaded...


Or press Alt-F2, type gnome-terminal, <ENTER>

wait a few seconds an then run

metacity --replace &


Or you can remove Compiz-Fusion from your system all together from recovery mode (press Esc at Grub and boot into recovery mode)

---

### Post by stiansoftcore on 2008-03-22
> **walkerk said:**
> Not too sure where compiz's settings folder is as I don't use it but perhaps ~/.Compiz

You could rename that folder so the options won't be loaded...


Or press Alt-F2, type gnome-terminal, <ENTER>

wait a few seconds an then run

metacity --replace &


Or you can remove Compiz-Fusion from your system all together from recovery mode (press Esc at Grub and boot into recovery mode)

You're my angel <3 

"metacity --replace &" worked, thank you sooo much :D 
Enjoy the rest of your holiday ! :)

---

### Post by walkerk on 2008-03-22
> **stiansoftcore said:**
> You're my angel <3 

"metacity --replace &" worked, thank you sooo much :D 
Enjoy the rest of your holiday ! :)

You're welcome :) Enjoy

---

