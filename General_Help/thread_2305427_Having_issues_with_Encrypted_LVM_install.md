---
title: "Having issues with Encrypted LVM install"
date: 2015-12-05
forum: General Help
---

### Post by 1Waffle on 2015-12-05
> [COLOR=#000000][FONT=Verdana]otherwise it sounds like a quite possible bug with your hardware and the encryption feature. Ubuntu forums might help better if its a bug with a specific combination of hardware. They might direct you to a script or patch to run to gather more information or correct for this since its all open source and could be modified to correct or simply patch an issue.[/FONT][/COLOR]I was directed to here from here:
[http://www.computerhope.com/forum/index.php/topic,153145.0.html](http://www.computerhope.com/forum/index.php/topic,153145.0.html)
I installed Ubuntu 15.04 LTS with Encrypted LVM.
[COLOR=#000000][FONT=Verdana]When I turn on my computer I get the first screen, but I cant type... So I restart and it boots to the second one... Is there a shortcut key or something I'm missing that will allow me to type my password at the first screen?
[/FONT][/COLOR]

---

### Post by Vladlenin5000 on 2015-12-05
15.04 isn't as LTS, **14.04** is.
The support for 15.04 will end in less than 2 months so I see no point in troubleshooting.

---

### Post by 1Waffle on 2015-12-05
Oops, so when I installed I started with 14.04 LTS, but then I update to 14.10 then to 15.04. The problem for me persisted through all versions. Sorry for my confusion...

---

### Post by 1Waffle on 2015-12-06
> **Vladlenin5000 said:**
> 15.04 isn't as LTS, **14.04** is.
The support for 15.04 will end in less than 2 months so I see no point in troubleshooting.
I'm updating to 15.10 right now using 
```
[COLOR=#111111][FONT=Consolas]sudo do-release-upgrade -d[/FONT][/COLOR]
```
I will report back if there are any changes.

---

### Post by SlidingHorn on 2015-12-06
This may be a stupid question, but have you tried continuing the password and hitting enter?  I haven't used an encrypted setup yet, so I don't know if it behaves this way, but a lot of situations in Ubuntu & linux in general don't show your progress when typing in passwords (e.g. sudo).  Just one of those "have you tried turning it off and back on again?" questions that might be worth asking :)

---

### Post by 1Waffle on 2015-12-06
So i've updated to 15.10. Typing the password and hitting enter does nothing. But the num, caps, and scroll locks all turn the light on and off on the keyboard.

---

### Post by 1Waffle on 2015-12-07
bump

---

### Post by 1Waffle on 2015-12-08
Bump

---

### Post by 1Waffle on 2015-12-09
So I was digging around on youtube and found this: [https://youtu.be/2oKOtACAgrU](https://youtu.be/2oKOtACAgrU) I skipped twords the end and saw how the first screen is supposed supposed to work. It looks like he has a cursor at this screen. Could this have something to do with me using AMD graphics drivers? (I had issues with cursor before because of an old Intel video card) But then again, I have no way to type into the box, and hitting enter does nothing.

---

### Post by 1Waffle on 2015-12-11
(BUMP)So I noticed today when I turned my computer on, at the first screen if I hit control alt f1, it takes me to what is normally a tty, but it takes me to an indefinately blinking cursor.

---

### Post by 1Waffle on 2015-12-13
(Bump) Anyone have ideas on what to do next?
I'm also only getting a blank screen when I try to switch to tty ctrl-alt-f1.
Is there a possible problem with my graphics drivers?

---

### Post by 1Waffle on 2015-12-16
So I noticed from even the desktop doing ctrl+alt+f(1-6) no longer takes me to tty just an indefinitely blinking cursor.
Also If I hit from the first screen ctrl+alt+del it will reboot my computer.

---

