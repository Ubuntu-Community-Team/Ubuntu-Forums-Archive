---
title: "terminal right clik options"
date: 2018-02-08
forum: General Help
---

### Post by j3984 on 2018-02-08
ubu 14.04 fox
is there a way to create a right clik paste option when you open a terminal and have a couple choices pop up that you store permanently there..??

---

### Post by yetimon_64 on 2018-02-08
I am seeing two separate aspects to your question. Firstly I must ask ... "What terminal are you talking about ?" Gnome-terminal, xfce4-terminal, mate-terminal etc or are you referring to the teletype terminals (tty terminals) that are accessed by the key combination "ctrl+alt+F**#** where **#** is a number 1,2,3,4,5 or 6" ?

The first part of your question ...
> **j3984 said:**
> ubu 14.04 fox
is there a way to create a right clik paste option when you open a terminal...
Gnome-terminal,xfce4-terminal and mate-terminal (distro supplied GUI terminals) here, on 14.04 Trusty with multiple DEs, all have a right click copy and paste option already, nothing needs to be added for copying/pasting. 

Now for if you are referring to the tty terminals. The tty terminals don't have mouse support generally and definitely no right click support, but there is a possible work around. You can install the package "gpm" with the command "**sudo apt-get install gpm**" ("gpm" is "general purpose mouse", don't include the quotes in the terminal when installing) for highlighting with the left mouse button and pasting code/text between tty terminals using the middle mouse button. This copy/paste option in the ttys using gpm is very limited, it seems restricted to the ttys and seemingly can not copy/paste back to/from the GUI; you can work around that by saving to and copying from a file when transferring to/from the GUI from a tty terminal.

 > **j3984 said:**
> ...and have a couple choices pop up that you store permanently there..?? I have never found a way to add custom options to the right click menu in any GUI terminals. As noted even with "gpm" installed there is NO right click menu available in the tty terminals (if you are referring to those type of terminals).

 Wait for further advice from other helpers with this aspect of your question.

---

