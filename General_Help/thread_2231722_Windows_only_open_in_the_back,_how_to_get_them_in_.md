---
title: "Windows only open in the back, how to get them in front?"
date: 2014-06-27
forum: General Help
---

### Post by 171742 on 2014-06-27
Hello,

right this. I got ubuntu 14.4. lts, it worked in the beginning. Now every time I open a program the window only shows when I click the button on the side, whcih before moved a bit.

What to do?

Thanks!

---

### Post by ajgreeny on 2014-06-27
Open the appropriate .desktop file in /usr/share/applications using your text editor and look for the lines
```
StartupNotify=true
Terminal=true
``` and make sure they have the word **false** at the end of those two lines.

If using Ubuntu and nautilus you will need to open the files from terminal with ```
gksudo gedit /usr/share/applications/*program*.desktop
``` as you will not get that choice with a right click in nautilus.

This was the solution I found using Xubuntu and thunar where several applications always opened without focus, and whilst it is not quite the same as your problem, it is similar and unity may deal with those .desktop files focus in a different way..

---

