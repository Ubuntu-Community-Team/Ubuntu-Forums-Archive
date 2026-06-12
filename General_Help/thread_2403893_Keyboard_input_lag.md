---
title: "Keyboard input lag"
date: 2018-10-17
forum: General Help
---

### Post by myronas14 on 2018-10-17
Hello...

I installed Ubuntu 18.04 recently and I couldn't help but notice that the there may be some sort of keyboard input lag, to be specific, I notice that the Caps Lock key turns off and on with a minor delay which causes me to capitalize two letters instead of one, like this: 'HEllo'
It gets very annoying honestly, I seem to be able to type rather fast without problem so i am not sure if it's just the Caps LOck (See? this is what happens)

Whatever the case, I am new to Linux so i don't have the slightest idea as to what could be causing it, this has never happened while I was in Windows, my keyboard is an old one, a PS/2 Dell AT102W from 1996, works just fine in Windows no problem which is why I think that Ubuntu is at fault here

I would greatly appreciate it if somebody could help me solve this issue, i've looked for other people facing similar issues but I couldn't really find any matching my case
Thanks in advance.

---

### Post by dino99 on 2018-10-17
Is that keyboard protected against dust and small debris ? You can return it upside down to see if something is falling or use pulsed air if you have some .

---

### Post by Autodave on 2018-10-17
1996? Does that still have the DIN plug (little round one) on it?  You may want to at least try (borrow) a USB keyboard if so.

---

### Post by myronas14 on 2018-10-17
Can't be, I already said that it has no issues with Windows, though to be sure I did what you said and nothing comes out, although it's from 1996, it's actually like-new since whoever had it took super good care of it
This has to be an issue with Ubuntu, i am just not sure what. And yes it's a PS/2 keyboard but I ain't gonna give it up for a USB one because Linux cannot handle it correctly, there has to be something that I can do, if Windows can do it, then so can Linux

---

### Post by Holger_Gehrke on 2018-10-17
X11 keyboard handling follows the lead of old mechanical typewriters. Caps Lock is released on **release** of the Caps Lock key. Windows releases the lock on the **press** of the key. That might be the difference you're seeing. If that is the problem, the [Arch Linux wiki]("https://wiki.archlinux.org/index.php/Xorg/Keyboard_configuration#Switching_state_immediately_when_Caps_Lock_is_pressed") has a work-around that should also work on Ubuntu.

Holger

---

