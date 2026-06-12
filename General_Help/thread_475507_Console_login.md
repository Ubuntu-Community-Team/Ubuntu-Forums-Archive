---
title: "Console login"
date: 2007-06-16
forum: General Help
---

### Post by Speekie on 2007-06-16
I've installed just the command-line system. So I login in the console (no gdm/kdm). But the login prompt is a bit screwed up:
```

* Starting ACPI services...                                                                                              [ OK ]

* Starting system log daemon...                                                                                          [ OK ]

* Starting kernel log...                                                                                                 [ OK ]

Ubuntu 7.04 pingu tty1

pingu login:  * Starting Common Unix Printing System: cupsd                                                              [ OK ]

* Starting mouse interface server gpm                                                                                    [ OK ]

* Starting Music Player Daemon:                                                                                          [ OK ]

* Starting periodic command scheduler crond                                                                              [ OK ]

* Running local boot scripts (/etc/rc.local)                                                                             [ OK ]

```
So the login prompt is somewhere in between the startup messages. It's not really a problem because I can just enter my username anyway (or hit enter and get a new login prompt). But it looks messy. Anybody found a solution for this?

---

### Post by reckless2k2 on 2007-06-16
If I'm not mistaken, this is a simple fix in the menu.lst and add an sync to boot kernel line. I'm sure someone can chime in but it would be the screen size syntax. vga=791 yadda....
please view this link:

[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Howto_Change_Font_Size_During_Boot_Framebuffer_Resolution](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Howto_Change_Font_Size_During_Boot_Framebuffer_Resolution)

reboot and i think that'll help.

---

### Post by cosmospt on 2007-11-11
Hi,

I am also having the same problem with Gutsy.

I tried to add the sync option to kernel parameters without success. 

Anyone can help?

---

### Post by billmeek on 2007-11-17
The prompt is simply being covered up.  See :

[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/75830](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/75830)

Press the Enter key and you'll see the login prompt.

---

