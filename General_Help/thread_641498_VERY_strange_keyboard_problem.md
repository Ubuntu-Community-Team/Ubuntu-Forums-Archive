---
title: "VERY strange keyboard problem"
date: 2007-12-15
forum: General Help
---

### Post by Redeyes_Gambit on 2007-12-15
Hi,

I have a very strange keyboard problem. When I try to type an apostrophe, or a quotation mark it only prints on the screen EXACTLY every other time. In other words, if I hit apostrophe 10 times it only shows up 5. 

Then, when I go to delete an apostrophe or a quotation mark the PC speaker (internal) will beep at me once.

This dosen´t happen in windows 98 (dual boot) or, explain this one to me, in XP running in a virtual machine in Ubuntu(???)

I have tried switching out the keyboard with another to no avail, and I´m trying to avoid a USB keyboard because GRUB doesn´t recognise it and I can not choose between OSs at start up.

This computer is running feisty and my keyboard layout is US English.

---

### Post by geraldm on 2007-12-16
You could start from an xterm program, and enter the command xev
This will bring up a square box, which you can move the mouse pointer into.
Then type the keys that you think have problems, and the codes that are returned will appear in the xterm window.

Gerald

---

### Post by zesty on 2008-01-20
I had the same problem and found the answer in this post:[COLOR="Blue"]
[Incorrect keyboard setup - xubuntu 7.10 i386]("http://ubuntuforums.org/showthread.php?p=4176339#post4176339")[/COLOR]

---

