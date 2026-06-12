---
title: "Power button?"
date: 2008-05-03
forum: General Help
---

### Post by FloydianX on 2008-05-03
OK, I'm fairly new to Ubuntu - so there will probably be an obvious fix to these but I can't find any.
Problem 1:
For some very annoying reason, there's no longer an option to restart or turn off my computer. When clicking the icon, it brings up all the other usual options - log out, lock screen, switch user, suspend, hibernate. But the two most important ones are no longer there. The icon has also completely disapeared from the login screen. 

Earlier today I decided to try xfce (currently using Gnome), I didn't really like it so uninstalled it. That's obviously the cause as I've done nothing else of interest today. 
Oh and I'm using ubuntu 8.04.

Problem 2:
I accidentally removed the wireless internet icon from the panel. When I tried to re-add it there was no option. Now when I restart the computer (having to just hold down the power button because of problem 1) I can't connect to the internet. The key-ring opens up automatically on start-up as per usual asking for my wireless password. But then nothing happens. I can't seem to find where to select my wireless network. When I click configure a warning pops up saying 'The Interface does not exist'.

Sorry if I'm being vague, still new to this. Thanks for your help.

---

### Post by FloydianX on 2008-05-03
Hmm, as for the wireless problem. I just found this
[https://bugs.launchpad.net/ubuntu/+source/gnome-nettool/+bug/206353](https://bugs.launchpad.net/ubuntu/+source/gnome-nettool/+bug/206353)

Its pretty much that :/
> By the way, the network-admin tool does not show any wireless networks under "Network name (ESSID)"; the drop-down box is empty (just a thin flat bar, actually).

Thats happening for me too. For me my wireless was working fine right until today when I decided to try and faff around with the desktop environments... and accidentally removed the wireless icon from the panel.

---

### Post by FloydianX on 2008-05-03
OK I finally found the solution to problem 1. But the wireless problems are still there. Seems to be related to that bug.

---

### Post by qhaz on 2008-05-04
. . . so what was the solution for Problem 1?  Please share.

---

### Post by FloydianX on 2008-05-04
Sorry, should have said.
System > Administration > Login Window.
Then on the local tab make sure the 'Show actions menu' option is selected.

It turns out that when I uninstalled xfce it kept the xfce style login window, so I changed that back manually. For some reason when I changed it, it unselected that option without me noticing. Hell I didn't even know what it did so I never touched it. It never occurred to say that I'd done that as all I'd done was change a login window style. But hey ho, sometimes it's the small things which can have the big consequences. :P

---

