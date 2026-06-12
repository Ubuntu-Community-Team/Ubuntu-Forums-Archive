---
title: "Help Getting Ubuntu to work on my HP pavilion a1700n desktop"
date: 2008-03-31
forum: General Help
---

### Post by Brad70 on 2008-03-31
I have been getting an error message when I try to boot my ubuntu 7.10  kernal. it says "out of range-try 1024x768 60hz". I have a feeling that if I could just change the setting to what it reccomends it will work, however I don't know how to change it. I read about the $sudo dpkg-reconfigure xserver-xorg. but i dont know where to enter this code at. I have been playing around in the loading screen before I boot and noticed that if i hit 'c' a <grub> appears on the left side of my screen and if I then hit 'tab' a list of words comes up there. Also when I do try to boot the kernal-generic and this error comes up if i hit ctrl+alt+f1 a black screen appears with white text saying "crypt setup: source device not found" and if I hit enter it does something and then "11.336000 sd 4:0:0:0 [sdb] assuming drive cache: write through" comes up about 3 or 4 times on the screen. I don't have a clue what any of this means or how to use the information I have found about similer problems. can some one direct me to a detailed explination of how to fix this "out of range error" thanks ahead of time
Bradley
O and I am dual booting with windows vista. and I installed with the text based cd, putting the complete OS onto and hitachi usb external memory device 160GBhttp://ubuntuforums.org/images/smilies/guitar.gif
:guitar:

---

### Post by cmnorton on 2008-03-31
This sounds like you've already installed Ubuntu. If you have, choose the recovery option. When you get to the prompt, run 

dpkg-reconfigure xserver-xorg 

It's probably safe to take all the default answers. When you get to driver, start with VGA. you won't have a great looking desktop, but once you login you can play around with what configuration will work.

---

### Post by Brad70 on 2008-03-31
Ok I selected the recovery option and it did some stuff in the black screen with white text. when it stoped doing stuff i typed 'dpkg-reconfigure xserver-xorg' and hit enter nothing happened. I tried it again and still nothing. so then I typed '$sudo dpkg-reconfigure xserver-xorg' and hit enter and nothing happend.....how will i recgonize when the code is prompting me? it really seems as though my problem is that i dont know how to work with a computer in the black screen with white text mode and so when I type in the dpkg-reconfigure xserver-xorg its not doing anything because mabey im not typing it with the right code? idk if i am making any sense I am really unfamiliar with working on a computer in this screen.

---

### Post by cmnorton on 2008-03-31
When you ran 

dpkg-reconfigure xserver-xorg

you should have seen this error

/usr/sbin/dpkg-reconfigure must be run as root

The only thing left for you to do is look at and edit your xconfig file

/etc/X11/xorg.conf 

with sudo in front of your favorite editor or gksudo in front of your favorite gnome editor. But honestly, if dpkg-reconfigure would not run, it sounds like you have a bad install.

---

