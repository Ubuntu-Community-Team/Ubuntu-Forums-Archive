---
title: "Keyboard layout problems"
date: 2015-07-25
forum: General Help
---

### Post by LuigiMazzini on 2015-07-25
I was modifying the keyboard input method Russian (fonetic WinKeys) and after a few changes there are no more cyrillic characters when I switch the langugage to russian.
Here's what I did:
- I edited the "ru" file (located in /usr/share/X11/xkb/symbols) in gedit and changed the caracters I wanted to have at a specific key,
- rebooted and executed ```
sudo dpkg-reconfigure xkb-data
``` and everything worked ok.
After that I made some more changes in "ru" file and executed the code above and everything was ok, but after a third editing the russian keyboard stopped working. There are only latine letters, no more cyrillic. I'm sure everything is ok with the "ru" file (I didn't delete anything, just swapped several characters).
I tried to remove and re-add russian (also with other imput options, not only fonetic WinKeys) but there's no more cyrillic.
Please help. :(

---

### Post by LuigiMazzini on 2015-07-26
Okay, if nobody knows what to do - how can I reinstall all the keyboard settings? I believe there are some packages that can be reinstalled... right?

---

### Post by LuigiMazzini on 2015-07-26
I already figured it out myself.

---

