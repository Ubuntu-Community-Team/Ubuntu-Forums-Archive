---
title: "gnome-terminal -e only gives blank terminal"
date: 2007-11-03
forum: General Help
---

### Post by zkeng on 2007-11-03
I am not able to run terminal commands or scripts in the terminal from desktop or gnome-panel launchers anymore.

If i write the commands directly in gnome-terminal it works just fine. For example...

'iwgetid'

..will show my current wireless network.

But a launcher with the following command line only fires up a blank gnome terminal (i have the gnome-terminal set to stay opened after executing commands):

'gnome-terminal -e iwgetid'

The -x option still works for starting graphical applications. For example this command will fire up a (blank) terminal window and then start gedit (but the terminal window stays blank):

'gnome-terminal -x gedit'

I have also tried to execute my old launchers that used to work in Dapper to run mp3gain on my music folder. They still work if I write the commands directly in the terminal, but not when I try to use the launchers.

Help anyone!?

By the way, Im running 7.10 amd64 on Acer Travelmate 7520G and exept from this the system is working fine.

---

### Post by TheBlueCow on 2008-04-07
I'm having this problem as well. Anyone know what's up? Or where to start looking for error messages possibly?

---

