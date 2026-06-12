---
title: "[SOLVED] Find out application name in x"
date: 2008-05-16
forum: General Help
---

### Post by tr0k0l0 on 2008-05-16
Hi, how can i find out the actual name of an application that is already running in the system?

example: 

- The applet for the panel called Network Monitor, when i go to the about tab in help, it says that is called "Network Monitor 2.12.1" but what is the actual name? (the binary file name?)

- Another applet called Network Manager, its actual name is nm-applet. 

- The clock and calendar in the panel, what is the name of the binary executable?

i´ve tried to find them with the "top" or "ps" commands with no luck...

Isn´t there an application like xkill or something i could click on an application and find it´s actual name? (the executable?)
or any other way to find it

Thanx very much....

---

### Post by kellemes on 2008-05-16
> **tr0k0l0 said:**
> Hi, how can i find out the actual name of an application that is already running in the system?

example: 

- The applet for the panel called Network Monitor, when i go to the about tab in help, it says that is called "Network Monitor 2.12.1" but what is the actual name? (the binary file name?)

- Another applet called Network Manager, its actual name is nm-applet. 

- The clock and calendar in the panel, what is the name of the binary executable?

i´ve tried to find them with the "top" or "ps" commands with no luck...

Isn´t there an application like xkill or something i could click on an application and find it´s actual name? (the executable?)
or any other way to find it

Thanx very much....

A better alternative for "top" is "htop".
You can use it's menu system to kill apps etc..
```
sudo apt-get install htop
htop
```

---

### Post by pointone on 2008-05-16
The clock applet does not have its own executable. It is contained in a library that is read by gnome-panel.

---

### Post by bodhi.zazen on 2008-05-16
Try 

```
ps aux
```

---

### Post by tr0k0l0 on 2008-05-16
thanx kellemes,, nice app htop, i think it would help...

---

### Post by tr0k0l0 on 2008-09-23
Ok I've found what i was looking for and i will post it here  'cause i think it's very useful...

Well my question was if there existed something that would tell me the name of an application in X, and that would be as easy to use as xkill (for example) and that something is: 
The wonderful **xprop**, is comes by default in many linux distros and it is as easy to use as **xkill** , just execute click on a window and all the information you need will be displayed in your terminal.... in fact there is so much data that the most effective way of retrieving the app name is to filter with: **xprop |grep -i WM_CLASS**. 

Hope it is helpful, Bye

P.D. Pointone you were right, the clock applet returns gnome-panel

---

