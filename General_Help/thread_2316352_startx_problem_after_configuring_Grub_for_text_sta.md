---
title: "startx problem after configuring Grub for text startup"
date: 2016-03-07
forum: General Help
---

### Post by David_Partridge on 2016-03-07
Trusty Tahr with Lubuntu desktop installed.

I set GRUB_CMDLINE_LINUX_DEFAULT="text", and system comes up fine in text mode, but startx just gives:

xinit: connection to X server lost
waiting for X server to shut down (EE) Server terminated successfully (0). Closing log file
 [IMG]http://www.htpcbeginner.com/wp-includes/images/smilies/frownie.png[/IMG]

What am I doing wrong please?

Thanks
Dave

---

### Post by Bashing-om on 2016-03-07
David_Partridge; Hello.

(l)ubuntu uses 'lightdm' as the display manager, to start that GUI from terminal :
```

sudo service lightdm start

```

Aside: the command 'startx' is only applicable for certain configurations, and lightdm is not one of these setups .

[INDENT][INDENT]all in the proper process
[/INDENT][/INDENT]

---

