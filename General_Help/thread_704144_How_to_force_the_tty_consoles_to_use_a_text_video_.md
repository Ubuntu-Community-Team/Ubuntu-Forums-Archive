---
title: "How to force the tty consoles to use a text video mode ?"
date: 2008-02-22
forum: General Help
---

### Post by syraxes on 2008-02-22
Hello, 

I have added "vga=0"  to the kernel parameters in grub , but it looks like the system is using a graphical mode anyway :  after kernel boots there is an obvious change in the text mode compared to the mode displayed for grub's menu.   And the mode seems to be a graphical one because the characters are larger than the default.    

Also, I have tried with different  fb modes like 769,791,792,768. All of these react in the same way : black screen until X starts , and the tty consoles are unoperable (black screen  when pressing ctrl-alt-f? ).   So, I really want a simple, fast text mode on the ttys . 

So :  how can I force the vga=0 to be obeyed , preventing the system from using some default graphical video mode for the tty consoles ?   


(Ubuntu 7.10 ,  ATI Radeon 9550 , wide 19" monitor )

---

### Post by syraxes on 2008-02-22
Please disregard my initial question.

It turns out that I've misunderstood my problem : the big/bloated video mode is text , not graphical.   I guess that the kernel replaces the standard (BIOS) console font with a different one ... 

With consolechars I've been able to set the font to something that I like . 

Now all I have to do is to discover how to load the desired font at startup....    
( /etc/console-tools/config seems to be a promising place to tweak )

---

