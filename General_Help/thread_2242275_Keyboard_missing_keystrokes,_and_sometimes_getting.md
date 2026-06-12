---
title: "Keyboard missing keystrokes, and sometimes getting stuck in 'repeat'"
date: 2014-08-31
forum: General Help
---

### Post by mrule on 2014-08-31
Hi,

Sometimes when I boot my machine, the keyboard does not work. It misses keystrokes, and sometimes seems to get stuck in a key-down state, where a single key will just be repeated. Usually, I can just reboot the machine until this stops. Since rebooting does seem to eventually fix this, I feel like it is a software and not a hardware problem. Does anyone have any idea how to fix this issue in Ubuntu? The keyboard is an apple aluminum keyboard.

---

### Post by ibjsb4 on 2014-09-01
I have never done an apple keyboard, but I would think that they can collect dirt just like the cheap plastic keyboards that I use.  In which case I take apart and clean.  This may be possible with your keyboard, you could research that.

---

### Post by mrule on 2014-09-01
Thank you for your reply, i think this is a good thing to check. 

Unfortunately, it is unlikely to be dirt in the keyboard, because the keyboard works without errors on other machines, any and all keys can display the missed keystroke or repeating keystroke behavior, and the problem is sometimes completely but temporarily resolved by rebooting the machine.

---

### Post by ibjsb4 on 2014-09-01
Got several hits on a forum search, maybe something here will help.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=apple+aluminum+keyboard&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=apple+aluminum+keyboard&sa=Search&cof=FORID:9)

Good Luck

---

### Post by mrule on 2014-09-22
As far as I can tell, all of the hits in the first three pages of the google search you linked concern problems that are different from the problem I describe. The key bindings are stable, and function as I want them, when the keyboard functions at all. My problem is essentially an intermittent failure of the keyboard that is sometimes resolved by rebooting. So far none of the forum posts that I have located really pertain to this issue, and I'm not sure how to start troubleshooting.

---

### Post by tgalati4 on 2014-09-22
How many USB ports are on your computer?  Have you tried all of them?  Is the behavior the same using each different port?  It's possible that one of your ports is not putting out a full 5 VDC needed to power the keyboard.  Rebooting will allow the voltage regulator to cool down and provide full current (1 amp split between two ports).  When it heats up, current flow drops and you get strange behavior.  Remove all USB devices except the keyboard.  Test the 5VDC using a voltmeter.

---

