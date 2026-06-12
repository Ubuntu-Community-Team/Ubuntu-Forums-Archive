---
title: "OpenOffice Calc with dark themes"
date: 2007-07-17
forum: General Help
---

### Post by tamias on 2007-07-17
Hi all,

I'm using a dark theme (Neutronium Gilouche, from gnome-look.org) for my desktop and I've performed the fixes for Firefox and OpenOffice. So far so good, but there is one problem remaining: OpenOffice Calc is incapable of displaying colours, whether that be cell bg/text colour, or series on a chart. Everything is just displayed as white on black.

Can anyone help me to get my colours back?

Thanks,
Mark

---

### Post by tamias on 2007-07-17
After a lot of digging, I've learned that OOo is getting confused about something, and enabling the high-contrast 'accessibility mode' due to the dark theme I'm using.

This is despite the option in "Preferences -> Accessibility -> automatically detect high-contrast mode of the operating system" being set to OFF.

Anyone able to help?

Thanks,
Mark

---

### Post by _saiko on 2007-07-18
indeed a similar problem here

would sombody be kind enough to clarify this issue ?

---

### Post by tamias on 2007-07-25
Is the 'high-contrast' accessibility mode flag set by the theme or something else in Gnome, or is it detected automatically from the desktop bg/fg colours by OpenOffice?

If the former, can the flag be over-ridden? If the latter, I guess we'll have to wait for OOo to fix the bug, unless someone knows of another way to force OOo back into normal mode of operation?

---

### Post by tamias on 2007-07-30
It seems that no one knows of a way to get around this in Gnome, short of fixing the bug in OOo.

The issue has been noted (over 7 months ago!) in OOo's bug tracker at [http://www.openoffice.org/issues/show_bug.cgi?id=70501](http://www.openoffice.org/issues/show_bug.cgi?id=70501) so perhaps people affected by this issue could add their vote on the bug page in order to encourage work to be done to fix it.

---

### Post by _saiko on 2007-07-30
well untill somebody decides to fix those issues... i've found a workaround and works :>

[http://ubuntuforums.org/showpost.php?p=3064219&postcount=4](http://ubuntuforums.org/showpost.php?p=3064219&postcount=4)

then just edit your /usr/share/applications/*.theme file to work with this and u're set

---

### Post by tamias on 2007-07-30
> **_saiko said:**
> well untill somebody decides to fix those issues... i've found a workaround and works :>

Thank you so much for this, you are a star!

> [http://ubuntuforums.org/showpost.php?p=3064219&postcount=4](http://ubuntuforums.org/showpost.php?p=3064219&postcount=4)

then just edit your /usr/share/applications/*.theme file to work with this and u're set

Ok, I've tried following your advice, but come up against two problems. Can you be a little more precise?

1. The "env <path> command" syntax you gave appears incorrect, as it always returns 'permission denied'. I've tried "env GTK_RC_FILES=<path> command" but this appears to have no effect when oocalc is used as the command (it still starts under my dark theme).

(For the record, I'm using /usr/share/gdm/themes/Human/gtk-2.0/gtkrc in place of <path>)

2. Could you clarify what you mean by editing /usr/share/applications/*.theme ? I don't have any .theme files in that directory; do you mean editing the .desktop launchers instead?


Many thanks,

Mark

---

### Post by _saiko on 2007-07-30
> **tamias said:**
> Ok, I've tried following your advice, but come up against two problems. Can you be a little more precise?

1. The "env <path> command" syntax you gave appears incorrect, as it always returns 'permission denied'. I've tried "env GTK[COLOR="Blue"]2[/COLOR]_RC_FILES=<path> command" but this appears to have no effect when oocalc is used as the command (it still starts under my dark theme).

(For the record, I'm using /usr/share/gdm/themes/Human/gtk-2.0/gtkrc in place of <path>)

er seems i was a bit hyper when i found the solution and that affected my brain at the time of writing the explanation how i did it :D

it goes: "env GTK[COLOR="Red"]2[/COLOR]_RC_FILES=<path> <command>" :>

> **tamias said:**
> 
2. Could you clarify what you mean by editing /usr/share/applications/*.theme ? I don't have any .theme files in that directory; do you mean editing the .desktop launchers instead?

and again... same brain_typo :D

i meant .desktop launchers, not .theme files XD

just edit the EXEC :>

---

### Post by tamias on 2007-07-31
> **_saiko said:**
> er seems i was a bit hyper when i found the solution and that affected my brain at the time of writing the explanation how i did it :D

it goes: "env GTK[COLOR="Red"]2[/COLOR]_RC_FILES=<path> <command>" :>


and again... same brain_typo :D

i meant .desktop launchers, not .theme files XD

just edit the EXEC :>

Fantastic, that works a treat.

Can I just add something: You can make this more permanent across the system by going to /usr/lib/openoffice/program/ and renaming ooqstart to something else (eg. ooqstartBIN). Then create a bash script named ooqstart which loads the renamed executable in the new environment:

```

#!/bin/sh
env GTK2_RC_FILES=/usr/share/gdm/themes/Human/gtk-2.0/gtkrc /usr/lib/openoffice/program/ooqstartBIN "$@"
```

Remember to chmod +x the script to make it executable!

This means that whenever you launch OpenOffice, whether from a desktop launcher or by double-clicking on a file, it should launch in the alternative theme environment.

---

### Post by craigyjack on 2007-08-07
I am trying to get this working, so that other programs, not just openoffice /openoffice calc will open with a different gtk theme.

i have managed to get this working using the Human theme, but for some reason it will not work with other themes (even though they work fine as a gtk theme in gnome-theme-manager). anyone know why this works with the human theme but not others???

---

### Post by timbosity on 2008-03-07
DUde you are legend!!!!
I was beginning to despair with my dark theme (xfce-dusk) all apps were looking good (a few pages look odd in firefox but nothing too alarming) except for OOo i just couldnt figure out how to see anything!!!
 Thank you :guitar:

---

### Post by EvilOatmeal on 2008-04-02
Thank you very much for this!

I had one problem though.
Using */usr/share/**gdm**/themes/Human/gtk-2.0/gtkrc* didn't work for me,
it did however work with */usr/share/themes/Human/gtk-2.0/gtkrc*

Thank you!

---

### Post by calc on 2008-04-02
This [issue 87147]("http://www.openoffice.org/issues/show_bug.cgi?id=87147") also has some bearing on the problems with using different themes. OpenOffice.org by default inherits the colors from the theme even for document view which means that what it looks like on screen and what it prints out as can end up being two very different things.

---

### Post by timbosity on 2008-04-29
Alright,

This workaround no longer works with Hardy. Does anyone have an idea of how to get openoffice to have a different (read workable) theme from the dark one selected for the system (in my case dusk from xfce). I have no other issues with any other application and would really like to have this pc back to full working capacity... oh yes and in XFCE (on other computer) this isnt an issue.

Anyone?

---

### Post by www.rzr.online.fr on 2008-05-01
A workaround would be a fast theme switcher, that detect you're running a unsuported dark application 

TBC : [http://rzr.online.fr/q/dark](http://rzr.online.fr/q/dark)

---

### Post by stovicek on 2008-07-08
I got tired of searching for a new workaround, so I came up with one on my own. Apologies if someone has beat me to it. I couldn't find one.

I'd go into more detail here, but I spent the last of my evening well past a decent time for bed writing it up before I forgot about it. You can find it here:

[http://www.adamstovicek.com/ubuntu/fixes/openoffice-dark-theme-workarou.html](http://www.adamstovicek.com/ubuntu/fixes/openoffice-dark-theme-workarou.html)

Have a good evening.

---

