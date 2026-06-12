---
title: "A Bunch of (error messages?) or garbage during boot"
date: 2015-08-18
forum: General Help
---

### Post by Alduins_Khajiit on 2015-08-18
EVERY TIME I boot into Ubuntu, during boot I get a bunch of random garbage text or error messages or something (see black screenshot). something is out of whack here. If I hit the down arrow after text stops loading, the screen turns purple and display more garbage and the password field continues to fill up just from the down arrow hold (see purple screenshot). and I have to backspace until the characters from the down arrow is erased It started doing this a week ago. It NEVER done this before and now it happens EVERY TIME I boot up Ubuntu


[ATTACH=CONFIG]263931[/ATTACH][ATTACH=CONFIG]263932[/ATTACH]

---

### Post by grahammechanical on 2015-08-18
There are not random and they are not error messages. Although there may be an error message or two somewhere in that print to screen. They are system messages. They are normally hidden by a splash screen. And it seems that you getting a screen full at a time. Part of the kernel boot parameters are the words: "quiet splash." If we remove those words from the Grub boot parameters then we do not get a splash screen and we get to see all the Linux system messages.

---

### Post by Alduins_Khajiit on 2015-08-18
How do I fix it and put it back to normal?

---

