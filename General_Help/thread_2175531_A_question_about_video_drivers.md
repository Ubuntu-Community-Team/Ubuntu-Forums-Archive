---
title: "A question about video drivers"
date: 2013-09-19
forum: General Help
---

### Post by muckijeste on 2013-09-19
Hey all;

I'm using Ubuntu 12.04 LTS on an ASUS X55VD-SX208 laptop which has both the Intel Integrated Graphics and the upgraded Nvidia Geforce GT610M. Now, with hybrid graphics laptops like this one, Windows utilizes the Intel driver for the desktop and 2D environment, however when there is a need for 3D acceleration, the control automatically goes to the Nvidia card. So my question is; how does it work on Linux? How can I check if I have installed the Nvidia driver properly? Am I using the Intel driver in the desktop environment? How about in the 3D environment? I'd be happy to see the answers to these questions.

Cheers

---

### Post by Bashing-om on 2013-09-19
muckijeste; Hi !

The situation is not entirely helpless; See:
[http://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphics](http://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphics)
[https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

[INDENT][INDENT]where there are solutions there are no problems
 [/INDENT][/INDENT]

---

### Post by muckijeste on 2013-09-20
Hey Bashing-om, again :D

Okay so just to recap:
1. How does it work on Linux?
Linux utilizes the Intel driver by default for all applications. However, there is software called "bumblebee", which allows running certain programs with the high-performance Nvidia card.
2. How can I check if I have installed Nvidia drivers correctly?
This can be checked by running the "[COLOR=#333333][FONT=Ubuntu Mono]lspci -vmk | grep -A 8 -B 2" [/FONT][/COLOR][FONT=arial][SIZE=2][COLOR=#333333]command. In my case, it prints out both the Intel and Nvidia drivers, so I'll guess everything is installed correctly.[/COLOR]
[COLOR=#333333]3.[/COLOR][COLOR=#000000] Am I using the Intel driver in the desktop environment?
Yes, Intel driver is used in the desktop environment by default.
4. How about the 3D environment?
By default, Intel drivers are used for the 3D environment. However, the Nvidia card can be utilized by running the program from the terminal with the prefix "optirun" (bumblebee must be installed).

Have I got everything correct here?

So as an example, I wanted to launch Google Chrome using the Nvidia card, however this is the output from the Terminal:
[/COLOR][/SIZE][/FONT]```
l33t@l33t-X55VD:~$ optirun google-chrome
[  525.570038] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) No devices detected.


[  525.570105] [ERROR]Aborting because fallback start is disabled.

```

I have looked up on Google and have found various posts about this. Here's what I've tried so far:

Uninstalling bumblebee, installing linux-headers-generic, reinstalling bumblebee, rebooting -- didn't work.
Modifying certain files configuration files by, for example, replacing the driver name "nvidia-current" with "nvidia" and many more -- didn't work.

All the workarounds on the internet seem to be based on those. Do you have any idea how I could get my card working?

Cheers

---

### Post by Bashing-om on 2013-09-20
muckijeste; Hey ! .. you have done your home work !
You appear to be doing things properly, however;
I do not run "BumbleBee" so, can not address your query.
May I suggest that you open another thread .. - to gain the visibility to those who do know - specific to  BumbleBee.
As the original question has been answered; Please close this thread as "solved".

It is a matter of who knows;

[INDENT][INDENT]solutions do exist
[/INDENT][/INDENT]

---

### Post by Yellow Pasque on 2013-09-20
Make sure you're running at least nvidia 304.88

---

### Post by muckijeste on 2013-09-21
I'll mark this as solved because, well, it's not actually solved, but it's a workaround...

I have normally started Call of Duty 4 through Wine and it seems to have a playable 40-60FPS framerate, which definitely couldn't be achieved by the Intel adapter. That works for me, I don't need the Intel adapter at all so...Thanks for the help guys

Cheers

---

