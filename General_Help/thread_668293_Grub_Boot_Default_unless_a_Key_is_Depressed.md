---
title: "Grub: Boot Default unless a Key is Depressed"
date: 2008-01-15
forum: General Help
---

### Post by charlie. on 2008-01-15
Without wasting any bandwidth on jokes about depression and keyboard psychologists, I'd like to know the following: can you configure grub to boot the default without delay UNLESS a specific key (say, SHIFT) is "down" at the time that grub runs?

To put this another way, grub should only display its menu when the key is depressed.

---

### Post by Thanoulis on 2008-01-15
To minimize GRUB's delay, just edit the /boot/grub/menu.lst:
```
timeout 0
```
As for the keypress menu, i do not think tha GRUB may do this at all...:confused:

---

### Post by dagnabit dang doohickey on 2008-01-15
Change the timeout in the Grub menu.lst file to something short:
```
timeout         2
```


Then find this part of the Grub menu.lst file:
```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```

Uncomment #hiddenmenu:
```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

```


Now, when you boot, unless you press the Esc key withing 2 seconds of seeing a "Grub Loading" message appear on your screen, you'll boot into your default OS.

---

### Post by mokshadaya on 2008-01-15
Yes, the above info is correct.  This is exactly the method that I use so that I can forget that I even have Windows installed on my machine.  :)

---

### Post by charlie. on 2008-01-16
Hiddenmenu doesnt hide grub - it only hides the menu. Grub still waits for "timeout" seconds.

Making the timeout really low (even 2 seconds is low enough because, in my experience, by the time grub actually displays, 2 seconds have passed - particularly on CRT monitors that don't warm up instantly.) is one solution, but it isn't a very nice one because you have to repeatedly hammer "up" or "down" to use grub's menu.

I'm wondering what "timeout 0" *and* hiddenmenu will do. I expect that it will be the same as normal "timeout 0" but that you'll have to repeatedly hammer "esc" instead of a direction key.

---

### Post by dagnabit dang doohickey on 2008-01-16
The goal of using hiddenmenu in this fashion is not specifically to hide the menu (although if the default OS is the booted OS in all but a few odd occasions this can be desirable), but rather to make the Esc key an intercept key. Else, as you have noted, you'll have to use either the Up or Down keys to do the same thing. Maybe its just me, but making a split decision about which key to press (and whether or not to press one at all) within a two second window can become a little frantic at times. So, by delegating Esc as the intercept key, the options get trimmed to one and the upper-left-most key on the board becomes the easy, and only, target.

---

