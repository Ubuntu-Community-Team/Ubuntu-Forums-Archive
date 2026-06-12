---
title: "What is the difference between the system console the linux console and the virtual c"
date: 2021-02-01
forum: General Help
---

### Post by thehappybilly on 2021-02-01
so there are three different articles on wikipedia describing what seems to be to be the same thing,


1: [https://en.wikipedia.org/wiki/System_console](https://en.wikipedia.org/wiki/System_console)


2: [https://en.wikipedia.org/wiki/Linux_console](https://en.wikipedia.org/wiki/Linux_console)


3: [https://en.wikipedia.org/wiki/Virtual_console](https://en.wikipedia.org/wiki/Virtual_console)


I don't understand what the difference is between the system console the linux console and the virtual console, i checked wikipedia and there are 3 different articles seemingly describing the same, or semi same thing.






so i just wanted to ask this question and see what people think, thanks.

---

### Post by Holger_Gehrke on 2021-02-01
A system console is not specific to any OS, it's a feature that a lot of them have. The Linux console is a system console on Linux and the ability to have multiple virtual consoles or virtual terminals is a feature of this Linux specific implementation of a system console (and it's not uniquely a feature of Linux). Or at least that's how I would describe the difference between those terms.

Holger

---

### Post by grahammechanical on 2021-02-01
Not to mention tty and terminal. tty = TeleTypewriter.

A lot of the names go back to the very old days and have been carried forward to our times. In the old days when computers were room sized they were accessed/programmed through a combination screen and keyboard. A terminal/console.

Linux is able to emulate in software more than one tty. In the not so old days before the desktop environment was developed Linux could run one application on tty1 and another application of tty2. We can access these terminals by pressing Ctrl + Alt and then a function key. It is my understanding that nowadays the Linux kernel loads on tty1. Which is why we sometimes see some printouts. Then Linux switches over to tty7 and loads the desktop environment and the login screen. When we shutdown the desktop environment closes on tty7 and switches back to tty1 for the Linux kernel to exit. Which is why we sometimes see some printouts when we shutdown.

As we sometimes need to use the command line we can load a software terminal called a virtual terminal. Also known as Gnome terminal or simply as the terminal.

[https://www.howtogeek.com/428174/what-is-a-tty-on-linux-and-how-to-use-the-tty-command/](https://www.howtogeek.com/428174/what-is-a-tty-on-linux-and-how-to-use-the-tty-command/)

Regards

---

### Post by Keith_Helms on 2021-02-01
Terminal console?  I remember the console typewriter!  (Not to mention das blinkenlights)

---

