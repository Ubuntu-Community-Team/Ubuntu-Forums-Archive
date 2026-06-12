---
title: "Laptop lid close problems"
date: 2017-06-07
forum: General Help
---

### Post by sE7DNzA on 2017-06-07
Hello!

I recently installed Ubuntu Gnome and have come across several issues. One of them being that, when I close the laptop lid and re-open it, I come across the following screen: 

EDIT: I can't seem to get the attached pictures to work. It's a picture a terminal screen displaying text starting with: 

[ OK ] Created slice User Slice of gdm 
       Starting User Manager for UID 120...
[ OK ] Started Session c1 of user gdm. 
...

[ATTACH=CONFIG]275518[/ATTACH]

I can escape to the log-in screen by using Ctrl-C and Enter, but every time I attempt to log back in, I am brought back to the log-in screen. Here is my basic system information: 

EDIT: Again, can't get picture to work, so: 

Memory 7.6 GiB
Processor Intel Core i7-7500U CPU @ 2.70GHz x 4
Graphics Intel HD Graphics 620 (Kabylake GT2) / AMD Hainan
Base system Ubuntu 17.04 64-bit
Disk 20.8 GB

[ATTACH=CONFIG]275519[/ATTACH]

Also, my laptop (Lenovo ideapad Flex 4) has an AMD Radeon graphics card. When I want to view the corresponding Graphics Card information I am presented with the following: 

EDIT: A terminal with the following terminal command: 
sudo lspci|grep VGA 
I get:
 00:02.0 VGA compatible controller: Intel Corporation Device 5916 (rev 02)



[ATTACH=CONFIG]275521[/ATTACH]

I'm pretty sure it's not supposed to say that when I have a Radeon Graphics card instead of Intel HD. 

Finally, if I find minor bugs and glitches, where would be the best place to report them? For instance, my "Home", "End" keys are a bit glitchy, my mouse cursor is not smooth at all, I have certain minor issues while navigating file explorer, etc. 

Sorry if I'm bombarding a single thread with many questions, an answer to the first one would suffice. Thank you!

---

