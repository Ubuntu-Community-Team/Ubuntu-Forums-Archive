---
title: "ubuntu wont boot after 1st time"
date: 2007-05-03
forum: General Help
---

### Post by opie12 on 2007-05-03
What i have installed is ubuntu 7.04. I have it installed on a dell dimension e310. I installed it and it worked for the first time only. But after that i tried to switch users 2 the admin and it never loaded again. I see the loading bar screen and then it just goes to a black screen and doesnt do anything. I ran a memory test for 1.5 hrs and that didnt help with anything. What should my next move be?


another problem is that when the boot menu comes up when i turn on the computer to pick what OS i want i can only see half of it. The box is on the bottom of the screen and it is cut off. How can i fix this

if you can help me in anyway with this i would greatly appreciate it.

thanks

---

### Post by hal8000 on 2007-05-03
After loading Ubuntu and you see a black screen, can you login at an alternate console?
Try pressing ctrl-alt-F1  then login with your username and password.
If you can get to a console type 

less /var/log/messages
less /var/log/Xorg.0.log

and look for clues.


When you get to the Grub screen, press Esc to enter text mode, press e to edit your Ubuntu boot line
and append vga=ask to the end of your ubuntu boot line. You can press scan to see a list of video modes,
once you find one that works, you can edit /boot/grub/menu.lst to apply changes permanently. I have vga=794
on my menu.lst as exactly the same thing happened to me on booting.
HTH

---

