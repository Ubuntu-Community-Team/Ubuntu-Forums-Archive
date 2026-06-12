---
title: "Deluge doesn't start!"
date: 2008-05-24
forum: General Help
---

### Post by jellylogix on 2008-05-24
When i try and run deluge in Ubuntu Hardy, the tab in the taskbar shows up, saying that it's starting, but then after a few seconds it goes away and NO DELUGE. the process isn't even running anymore.

---

### Post by ModelM on 2008-05-24
Open a terminal & type "deluge" to run it from there. When it crashes, you should be able to see the error messages it leaves behind in order to diagnose what's going on.

---

### Post by Anduu on 2008-05-25
Something to note...

On occasion Deluge crashes...when it does it doesn't release it's hold on your network connection and it cannot be started again until the connection is closed.

To do this you can restart or type killall python in a terminal.

---

### Post by ceraunius on 2008-05-26
I also have the same problem.
I think that is something with python.

I get this error running deluge from terminal:
IndexError: list index out of range

Can anyone help?

Thanks :)

EDIT:

Solution on: [http://ubuntuforums.org/showthread.php?t=571252](http://ubuntuforums.org/showthread.php?t=571252)

-go to /usr/share/deluge/plugins
-sudo rm -r ExtraStats

:D

Worked with me.

---

