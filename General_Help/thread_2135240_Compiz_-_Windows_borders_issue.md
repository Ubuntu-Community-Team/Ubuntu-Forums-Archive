---
title: "Compiz - Windows borders issue"
date: 2013-04-13
forum: General Help
---

### Post by GameX2 on 2013-04-13
Hi,


I have a few issues with Compiz.  It is crashing most often then before, like simply opening the Dash will cause Compiz to crash, and restart after a few seconds.  Anyways, I do know that Compiz is quite unstable, I'm dealing with it.

What's really annoying, is that when I start CCSM and try to change a key binding, the windows borders will crash.  Everytime.  I'm talking about this button here:
[http://img836.imageshack.us/img836/4417/gestionnairedeconfigura.png](http://img836.imageshack.us/img836/4417/gestionnairedeconfigura.png)

Same thing happen with GIMP 2.8.  When I move a floating windows, it crashes the borders of the whole desktop (Windows are still moving with ALT/Super key, but the borders are gone), even if I run GIMP in "Single-Windows mode".

It's extremely annoying..  Everything, I have to type "compiz --replace" in the Terminal.
I've tried to reinstall Compiz, but that does not solve the issue.


Alternatively, I have a weird bug, still with Compiz.  It appeared since a while.  When I start an application that require a password, such as GParted, the password prompt now has borders (It shouldn't!  That not normal, and ugly).  Weird...
[http://img22.imageshack.us/img22/940/gparteds.png](http://img22.imageshack.us/img22/940/gparteds.png)

Thanks for the help!

---

### Post by wildmanne39 on 2013-04-13
The border issue on the password looks like you have emerald window decorations installed instead of gtk-window-decorator.

Most issues with compiz are usually issues with the grahics driver, or the settings in ccsm.
Have a look at this link it may help.

[https://help.ubuntu.com/community/CompositeManager#Cube_And_Effects_for_Ubuntu.2C_Xubuntu.2C_Lubuntu.2C_Kubuntu_and_Edubuntu_in_release_10.04.2C_11.10_and_12.04](https://help.ubuntu.com/community/CompositeManager#Cube_And_Effects_for_Ubuntu.2C_Xubuntu.2C_Lubuntu.2C_Kubuntu_and_Edubuntu_in_release_10.04.2C_11.10_and_12.04)

---

### Post by GameX2 on 2013-04-13
Thanks.
I've backed up my current Compiz profile.  I'll try to reset the settings to default, to see how it goes.

As for Emeral, running the command "gtk-window-decorator --replace" restart the decorations, but does not fix the password border.  Emerald is not even installed, according to the output of "emerald --replace".

---

