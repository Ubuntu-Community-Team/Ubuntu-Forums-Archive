---
title: "Keyboard going crazy Ubuntu 18.04"
date: 2018-07-22
forum: General Help
---

### Post by wafflewaffle on 2018-07-22
Hi,

a few days ago I installed Ubuntu as a second OS on my PC. Before I used several distributions including Ubuntu as VM without any problem.
But now as a dual boot config, I have some weird keyboard issues that appear randomly (only in Linux, Windows is behaving fine).
 I already installed Ubuntu twice (first time Ubuntu Mate, second time Ubuntu)

The problem:
At some indeterminate point of time, the keyboard acts as if someone constantly presses alt, cmd or shift. Sometimes it starts writing all caps and I have to press shift to write in lower case. Other times I cant type at all anymore and some other commands are called, e.g. save in the text editor (as if alt or cmd is pressed). In other instances I get strange symbols instead of the latin alphabet when pressing keys. Sometimes it also spams one key continously, as if someone holds the key. 
The mouse is also affected, as it acts like the left mouse button is pressed continously. 
For now I was unable to recreate the problems. They just appear at some point, even when the computer is in idle and I havent touched it at all.

I already tried switching between keyboard layouts when the issue appears, in the hopes of forcing the layout to reset. Without success. 
The onscreen keyoard doesnt work either when the problems occur.
I also tried unplugging the keyboard and putting it back in. When a key is spammed, it continous spamming it despite disconnecting the keyboard.

A part from minimal Ubuntu installation I have cinnamon, nodejs, npm and vscode installed.
Ubuntu is updated to latest patches and I already tried downgrading the kernel to a lower version.

The keyboard I use is a SteelSeries 6Gv2 and does not need any extra software or driver to run.

Any leads or tips what to try are highly appreciated

Regards
waffle

---

### Post by kungfugo on 2018-10-30
I have the same problem.
Occurred first with 16.04.
Persists after 
Upgrade to 18.04 and all forms of updates and upgrades. Also tried reinstalling xserver-xorg-input-all and upgrading the kernel. 

Any ideas appreciated.

---

### Post by regis74 on 2019-01-25
I have had the same issue with 18.04 and now 18.10
tried the above too and didnt solve
however only happens with laptop keyboard when typing fast (if slow it s ok but killing me still)
never at home on external usb keyboard , even when typing fast

---

### Post by regis74 on 2019-01-25
the issue seems tied to chrome i dont have the issue in a terminal window

---

### Post by dragonfly41 on 2019-01-25
Recently I experienced symptoms of berserk keys overwriting editor pages etc. forcing me to shut down,
After searching around I followed one tip (I don't have the url to article) by running this command.

compiz --replace

This seemed to stop the symptoms.
On another occasion I found that my wrist was pressing down on keyboard while I moved the mouse.
This caused repeat key presses.

---

### Post by regis74 on 2019-09-10
> **dragonfly41 said:**
> Recently I experienced symptoms of berserk keys overwriting editor pages etc. forcing me to shut down,
After searching around I followed one tip (I don't have the url to article) by running this command.

compiz --replace

This seemed to stop the symptoms.
On another occasion I found that my wrist was pressing down on keyboard while I moved the mouse.
This caused repeat key presses.

thx dragonfly seems to work quite nicely for me so far. right now trying to write more to check but this seems to prove you right!!

---

### Post by safdar96 on 2019-10-02
> **dragonfly41 said:**
> Recently I experienced symptoms of berserk keys overwriting editor pages etc. forcing me to shut down,
After searching around I followed one tip (I don't have the url to article) by running this command.

compiz --replace

This seemed to stop the symptoms.
On another occasion I found that my wrist was pressing down on keyboard while I moved the mouse.
This caused repeat key presses.


Thank u so much @dragonfly this command fixed my crazy keyboard, but my Ctrl key is stil not working, what should I do about that??!!

---

### Post by coffeecat on 2019-10-02
Back to sleep, old thread. Closed.

---

