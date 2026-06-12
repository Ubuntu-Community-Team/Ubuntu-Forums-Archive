---
title: "How can I increase the font size at bash terminal?"
date: 2022-03-15
forum: General Help
---

### Post by rennersf on 2022-03-15
Dear, my Ubuntu Server (latest version) is running into VirtualBox Machine. However, the font size is small. I'm not able to see the letters very well. How can I increase the font size at bash terminal?

---

### Post by TheFu on 2022-03-16
Bash is a shell, not a terminal.

Which terminal program are you using?  There are about 20 of them commonly used. I prefer a true xterm, but most DEs come with a bloated terminal - say lxterm, gnome-terminal, or something similar.  From Windows, puTTY is popular. They all work fine.  Most of those terminals will have a font-chooser either in the menus or through a well-known <cntl>-+ larger method.  xterms have a popup menu called VT Fonts, which is accessed using the <cntl>-right-click (hold it until the menu appears), then select the font you like.

Also, if you are running Ubuntu Server (no GUI at all), then I truly hope you are using a different workstation and ssh into the server from another box with a real terminal and full X/Windows select/paste capabilities.  If not, then you are doing it the hard way.

Virtualbox has a way to increase the size of the screen if you are truly at a console. It is in the virtualbox menus surrounding the screen - resize to fit window is one of the options that I vaguely recall. The virtualbox manual, available online will detail the solution. Google finds it easily.

---

### Post by MAFoElffen on 2022-03-17
Adding to what TheFu said...

If you are talking about 'Terminal' as a graphical terminal session application, go into the preferences and change the font and/or font size...

If you are talking about a vTTY or other Console session, then either change the reslotution of vTTY in Grub, reconfigure 'console-setup' or use the Linux utility  'setcon'.

To reconfigure 'console-setup':
```

sudo --configure console-setup

```
In two panel's of the setup, you will find "Font' and "Font size"...

TheFu suggests if you are 'Console Based' to use another app/layer to live in... I mostly used to use Console based session manager's such as Byobu... but now find myself using TMux and Terminator more and more... with 'fg' helping each... Even when using 'i3' as a Desktop Environment... My Ama-Gi Project LiveCD is mostly' Console Based', with an on-demand minimal Desktop as an option...

---

