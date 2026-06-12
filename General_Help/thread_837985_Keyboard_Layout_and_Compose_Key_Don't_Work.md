---
title: "Keyboard Layout and Compose Key Don't Work"
date: 2008-06-23
forum: General Help
---

### Post by bunnyfly on 2008-06-23
Hello, I am having trouble with the Keyboard Preferences dialog...lots of bugs seem to exist around it? If anybody could help me with one or all of them, I would GREATLY appreciate it! Here are four (possibly related) bugs that I have recently come up against which are causing me grief:

First - I have set my compose key to right alt...I believe this is default. But it doesn't work, unless I go into the preferences, uncheck and then recheck right alt as the compose key...then it works until I reboot.

Second - I have recently decided to learn the Colemak keyboard layout, and so I added Colemak to my layout list...(I have USA and USA Colemak now) However, even though it's there, it won't let me select it as default. I click on the select circle, but it remains USA as the default!

Third - I thought I would go into layout options and saw that I would like to keep the default "both alt keys together" to switch layouts. I tried it - and - it didn't work. So, I unchecked and rechecked it - it still does nothing. So I choose alt-capslock as my layout switcher. This works - but only from USA to Colemak! In Colemak, suddently both alts together work, but the alt+caps doesn't! Weird.

Fourth - in Colemak, the capslock key becomes backspace (which it's supposed to do)...however it still functions as capslock as well! So if I type "help<BS>lo woo<BS>rld" I get "helLO WOrld"

Are the keyboard preferences in Hardy (Ubuntu in general?) alpha or just overlooked and not programmed to function yet? Is my setup "wrong?" Am I doing something incorrectly or confused as to how this is supposed to work?

I'm using an up to date Hardy 8.04 with a Logitech diNovo cordless keyboard (although I don't think my keyboard has anything to do with it...I used to have a  Toshiba laptop that had the compose key bug as well in Gutsy and Feisty, so I think it's an Ubuntu thing)

Thank you so much,
[chloe]

---

### Post by bunnyfly on 2008-06-27
Anybody?

---

### Post by bopomofo on 2008-08-08
> **bunnyfly said:**
> First - I have set my compose key to right alt...I believe this is default. But it doesn't work, unless I go into the preferences, uncheck and then recheck right alt as the compose key...then it works until I reboot.

I am having precisely this problem. I came here looking for an answer, only to find the same question...


After looking at Launchpad, I found the following:

[https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/198420](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/198420)

Gavin Hamill  wrote on 2008-05-08:
> 
Update: If I check the 'Separate layout for each window' box, I am able to then select the Default radio button. After this, the keyboard layout is preserved across a reboot.

I just found this, so I won't know if it works until after I reboot.

---

### Post by bopomofo on 2008-10-12
> **bopomofo said:**
> I won't know if it works until after I reboot.

The answer seems to be: No. :(

---

