---
title: "X11 and cyrillic font"
date: 2007-01-16
forum: General Help
---

### Post by cssutto on 2007-01-16
I have been running dapper on a new ThinkPad for a week and it has run like a charm.

Suddenly,  when booting, it refuses to load X11.

I get the message that /usr/share/X11/fonts/cyrillic is not in the path.

It then tells me what is in the path.

I cranked up by older ThinkPad which has Dapper on it and checked and the same path has the fonts that my new machine says are not the correct fonts.

In other words, they have the same fonts in that path, but the old machine, which I am using to post this, runs and the new one does not.

Can anyone tell me how to fix the problem?

Thanks.

CSSJR

---

### Post by bigblackpapa on 2008-02-26
I have the same problem...

I'm not at home now. I have found this but i haven't tried it. I hope it's the solution :) :
[http://www.geekandproud.net/archives/2007/04/27/1069/fixing-fonts-on-ubuntu-edgyfeisty-upgrade/](http://www.geekandproud.net/archives/2007/04/27/1069/fixing-fonts-on-ubuntu-edgyfeisty-upgrade/)

The solution is to edit /etc/X11/xorg.conf and change:
Section "Files"
    FontPath "/usr/share/X11/fonts/misc"
    FontPath "/usr/share/X11/fonts/cyrillic"
    FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath "/usr/share/X11/fonts/Type1"
    FontPath "/usr/share/X11/fonts/100dpi"
    FontPath "/usr/share/X11/fonts/75dpi"
    # path to defoma fonts
    FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

into
Section "Files"
    FontPath "/usr/share/fonts/X11/misc"
    FontPath "/usr/share/fonts/X11/cyrillic"
    FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath "/usr/share/fonts/X11/Type1"
    FontPath "/usr/share/fonts/X11/100dpi"
    FontPath "/usr/share/fonts/X11/75dpi"
    # path to defoma fonts
    FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

The order of "X11" and "fonts" in the paths has changed. That's it!

---

### Post by bigblackpapa on 2008-02-26
It's because of the last Updates.

You have 2 solutions:

1.1 Boot is safe-mode
1.2 Execute:
        sudo qt-language-selector --mode select
1.3 Choose English - United stated

OR

2.1 Remove the updated package:
        sudo apt-get remove language-pack-kde-en

For more info:
[http://ubuntuforums.org/showthread.php?t=695073](http://ubuntuforums.org/showthread.php?t=695073)

Personnaly i did the first solution.

---

### Post by bigblackpapa on 2008-02-27
Oh i forgot to say something. You have to execute "startx" before the step 1.2

---

