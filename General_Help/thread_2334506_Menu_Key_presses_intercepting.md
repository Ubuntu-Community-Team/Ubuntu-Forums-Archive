---
title: "Menu Key presses intercepting"
date: 2016-08-20
forum: General Help
---

### Post by chandala on 2016-08-20
I use Ubuntu 16.04. I used current GUI (System Settings/Keyboard/Shortcuts...) to set a shortcut key for lowering the volume.

I'm inside a Google Chrome window with my address bar focused. I press Menu Key and the volume is lowered but Chrome responds too to my key press and displays what it would normally display if I press Menu Key. I pressed Menu key inside a Tilda window and Tilda didn't react. However, I think it's an Ubuntu bug since the Menu key presses aren't intercepted the right way. If they were, Chrome would have nothing to react to.

I could report this bug to ubuntu mailing list but I can't handle/manage that ugly interface so I chose to report it here. If you think this bug should be reported there instead, you're free to do it. As I already said, I am not lazy, just unable to handle mailing lists interface. I use Gmail (and only Gmail), I tried to reply to various mailing lists threads but my brain just can't get it.

---

### Post by howefield on 2016-08-20
> **chandala said:**
> I could report this bug to ubuntu mailing list but I can't handle/manage that ugly interface so I chose to report it here. 

Reporting bugs here isn't likely to get you what you want.

Perhaps an easier route to reporting a bug would be to use the terminal command ubuntu-bug, eg, with the keyboard/shortcuts window open, type

```
ps aux | grep "shortcut"
```

to get the process ID of the application, in the example below that would be 7888

```
hugh@xenial:~$ ps aux | grep "keyboard"
hugh      3499  0.0  0.4 716704 28144 ?        Ssl  08:08   0:00 /usr/lib/x86_64-linux-gnu/indicator-keyboard/indicator-keyboard-service --use-gtk
hugh      7888  0.1  1.4 1076692 88528 ?       Sl   09:31   0:01 unity-control-center keyboard
hugh     11674  0.0  0.0  21296   960 pts/18   S+   09:47   0:00 grep --color=auto keyboard
hugh@xenial:~$
```

```
ubuntu-bug 7888
```

would collect all the information that you need and log you into launchpad.. type in as clearly as you can describing the bug and submit.

You don't even need to get the process ID, if the application has a window which in this case it has, you can use

```
ubuntu-bug -w
```

You will be prompted to click on the relevant window, then the system will generate the info required for the bug report, log you in to launchpad.. ect.

---

