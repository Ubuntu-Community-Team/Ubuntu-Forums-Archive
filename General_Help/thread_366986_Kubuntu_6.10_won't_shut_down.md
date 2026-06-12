---
title: "Kubuntu 6.10 won't shut down"
date: 2007-02-21
forum: General Help
---

### Post by me1on on 2007-02-21
About a week (or so) ago, Kubuntu started having problems shutting down. When I click the "Turn Off Computer" button, the screen turns black, makes clicking noises a few times (the sound it makes when changing the resolution), and hangs. The only way I know of to get around this is using Ctrl+Alt+Backspace to kill X then turn off the computer from kdm (or just unplugging the computer :().

I don't know what could cause this. The only thing I can think of that I changed was upgrading KDE 3.5.5 to 3.5.6 using the packages at [http://www.kubuntu.org/](http://www.kubuntu.org/). Could this have caused the problem? Does anyone else have the same problem? If anyone has any idea on how to fix this I'd be really happy. :)

---

### Post by markitect on 2007-03-01
i don't use KDE so I might not be much help, but note the time and reproduce the problem.  Then when you boot back up take a look at dmesg and tell us what errors occur around that time period

---

### Post by wxnker on 2007-03-01
Try looking here:
[http://kubuntuforums.net/forums/index.php?topic=10455.0](http://kubuntuforums.net/forums/index.php?topic=10455.0)

The problem and solution there is about a similar error.
Go for the /etc/kde3/kdm/kdmrc solution not the Grub solution.

Regards
wxnker

---

