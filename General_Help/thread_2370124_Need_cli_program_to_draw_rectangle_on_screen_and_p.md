---
title: "Need cli program to draw rectangle on screen and print its coordinates"
date: 2017-08-30
forum: General Help
---

### Post by &amp;KyT$0P# on 2017-08-30
Is there a commandline program that lets you draw a rectangle on screen with the mouse and outputs its coordinates to the terminal?  Basically like [FONT=Courier New]scrot -s[/FONT], but instead of taking a screenshot just print the size of the rectangle and screen coordinates of the upper left corner.

Any suggestions would be much appreciated.

---

### Post by dragonfly41 on 2017-08-31
Since you mention scrot .. could a python script help you ..

recently I found pyautogui for building an automation script

[https://automatetheboringstuff.com/chapter18/](https://automatetheboringstuff.com/chapter18/)

[http://pyautogui.readthedocs.io/en/latest/](http://pyautogui.readthedocs.io/en/latest/)

---

### Post by &amp;KyT$0P# on 2017-08-31
Thanks for the reply.  Writing a Python 3 script is an option, but pyautogui seems more focused on automation than drawing on screen.

---

### Post by dragonfly41 on 2017-08-31
Have you seen this example ...

[IMG]https://pyautogui.readthedocs.io/en/latest/_images/square_spiral.png[/IMG]

---

### Post by &amp;KyT$0P# on 2017-08-31
> **dragonfly41 said:**
> Have you seen this example ...
Yes I saw it [here]("https://pyautogui.readthedocs.io/en/latest/introduction.html#examples") -
> This example drags the mouse in a square spiral shape **in MS Paint (or any graphics drawing program)**
(emphasis mine)

I'm looking to draw directly on the screen with manually dragging the mouse.

---

### Post by &amp;KyT$0P# on 2017-08-31
Another user suggested [slop]("https://github.com/naelstrof/slop").  It's not available in the repositories for 16.04, but I was able to build a .deb of [this version]("https://launchpad.net/ubuntu/+source/slop/7.3.49-1") on 16.04.  Seems to work well.

Thanks to all for your input!

---

