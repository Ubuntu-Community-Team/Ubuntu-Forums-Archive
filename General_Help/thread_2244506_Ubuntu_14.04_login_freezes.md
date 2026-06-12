---
title: "Ubuntu 14.04 login freezes"
date: 2014-09-16
forum: General Help
---

### Post by melvin13 on 2014-09-16
I was running Ubuntu 12.04. I downloaded updates and it must have installed Ubuntu 14.04. It requested restart. After the restart it will load until I reached desktop log in. I clicked on log in and nothing happens. When I switched to console it asked for my username and password. I enter it and nothing happens. The log on screen shows Ubuntu 12.04 lts, but in terminal it shows Ubuntu 14.04 I am a beginner with Ubuntu and don't understand a lot about entering what I need in terminal.

---

### Post by Bucky Ball on 2014-09-17
Well, there's no way a regular update would have upgraded the OS from 12.04 LTS to 14.04 LTS so something's amiss. How exactly did you update? In a terminal? If so, what command(s) did you use?

---

### Post by grahammechanical on 2014-09-17
> [COLOR=#000000]When I switched to console it asked for my username and password. I enter it and nothing happens.[/COLOR]

What do you mean "nothing happens?" A console is a command line interface. Once we log in to a console nothing is supposed to happen until we enter commands? Did your password get rejected? What commands did you run? You can try this,

At the boot menu (Grub) select Recovery mode. At the Recovery menu select Resume. Does that get you to a login screen that gets you to a working desktop?

Now, if you still have 12.04 you will see Recovery mode in the list of available options. If you are on 14.04 you will see Recovery Mode inside the Advance Options for Ubuntu sub-menu.

If the login screen is showing 12.04 but the terminal is showing 14.04 then you may have a partially completed upgrade. At that console run

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

and hope for the best.

Regards.

---

