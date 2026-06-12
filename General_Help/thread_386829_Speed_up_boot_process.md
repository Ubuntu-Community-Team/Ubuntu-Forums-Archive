---
title: "Speed up boot process?"
date: 2007-03-17
forum: General Help
---

### Post by filipebrandao_ on 2007-03-17
I've installed Ubuntu today on a 13GB partition with 2Gb Swap ( My PC have 1gb Ram).
I don't understand why ubuntu takes up to 5minutes to boot :S  Any way to speed up?

---

### Post by hal8000 on 2007-03-17
Which version of Ubuntu? Edgy Eft uses upstart so it should be faster to boot, have a look at the wiki, it may help

[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_permanently_disable.2Fenable_boot-up_services](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_permanently_disable.2Fenable_boot-up_services)

---

### Post by floke on 2007-03-17
Check to see what it's doing during the boot sequence by pressing - I think its CTRL-ALT-F(X - check F1, F2 etc.) - this will bring up the processes. From there you can see where its going slow. 

I had an issue with it hanging for about a minute or so at the 30% or so mark. Turns out it was the network configuration - so I edited the /etc/network/interfaces file to hash out everything apart from the 'lo' connection, and it boots with no delays at all. The whole thing takes about 30 secs.

---

### Post by bernied on 2007-03-17
Misery loves company - [here's](http://www.ubuntuforums.org/showthread.php?t=386820) another thread to watch.

---

### Post by filipebrandao_ on 2007-03-18
Yes I'm using Edgy Eft.

> **Steve.K said:**
> Check to see what it's doing during the boot sequence by pressing - I think its CTRL-ALT-F(X - check F1, F2 etc.) - this will bring up the processes. From there you can see where its going slow. 


When I press CTRL+ALT+F1 , it shows me the process that is ocurring in text mode.All the other F's only show me that little blinking prompt.


So...This is what i get:

Starting Up....
Decompressing linux....DONE.
Booting the Kernel.

(FREEZES HERE!!!!)

Activating Swap           [OK]
........(and continues)

The freezing spot in graphic mode:
[[img]http://img442.imageshack.us/img442/2192/07012007rn6.th.jpg[/img]](http://img442.imageshack.us/my.php?image=07012007rn6.jpg)

---

### Post by filipebrandao_ on 2007-03-18
I have news!
i've edited /boot/grub/menu.lst ( or something like that) to do not run quiet mode and now i can se whats happening in text mode...here is what i got:

Running /scripts/local-bottom                           ok
Running /scripts/init-bottom
Reading files needed to boot...
Setting preliminary keymap...
Preparing restricted drivers...
Starting baisc networking...
Starting kernel event manager...


That's it...it stops here. Only the first process of this list gets the Ok, is there any problem with the others?? 
I have to say that now the progress bar stops a little more to the right than before.
Any guess?


(can you help me out with [my other problem]("http://ubuntuforums.org/showthread.php?p=2317765#post2317765"), please?)

---

### Post by keybuk on 2007-03-21
Install the bootchart package, this will generate PNG files in /var/log/bootchart once the boot process completes.

File a bug, attach one of these charts and also attach the /var/log/udev file.

The bug should be on the udev package.

---

### Post by filipebrandao_ on 2007-03-26
Thanks!!
The problem was because my USB TVBoard! if i disconnect it , ubuntu boots really fast! :D

---

