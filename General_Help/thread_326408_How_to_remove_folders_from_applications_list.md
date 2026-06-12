---
title: "How to remove folders from applications list?"
date: 2006-12-27
forum: General Help
---

### Post by Cows on 2006-12-27
Well i recently installed wine and I installed a windows game. Now wine created a folder in the applications list on the top left corner of the screen. So now my list looks like this:

Applications:
- Accessories
- Games
- Graphics
- Internet
- Office
- Sound & Video
- Transgaming > Transgaming Cedega ( This is a folder , I want to delete it )
- Wine > Programs > .... ( This is another folder created by wine, I want to delete this also )

I tried deleting wine but it still stayed there. What I did was:

- Opened up terminal
- typed: sudo apt-get remove wine
- typed: sudo apt-get autoremove
- went to my home folder , enabled view hidden files , and deleted .wine folder

and the wine folder was still in the applications list.

Now with cedega is the same thing but I can't even delete the application:

- open terminal

cows@CowsComp:~$ sudo apt-get remove cedega
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package cedega is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
cows@CowsComp:~$ 

so this is probably not the right 'remove < application name>'

any ideas.

---

### Post by KenSentMe on 2006-12-27
Go to System - Preferences and then choose Menu something (don't know the english words, i run Ubuntu in Dutch). There you can add or remove programms to your menu or add/remove folders.

---

### Post by Cows on 2006-12-27
Menu Layout in english. Ty I got it =].

---

