---
title: "Critical Processes?"
date: 2007-10-30
forum: General Help
---

### Post by bks on 2007-10-30
I noticed that I have a number of processes running that I don't think I need, but I just wanted some thoughts on what I should or shouldn't disable. Namely I'm looking at the evolution processes and python. Thanks.

---

### Post by mannih2001 on 2007-10-31
If you are not using evolution (including the functionality it provides for the calendar applet), you should be able to deactivate it with the session manager.

Python is needed for a couple of panel applets and for the update manager (AFAIK).

BUT: These processes don't cost you a thing. They are not using any CPU (as your screen shot demonstrates) and the kernel will swap them out of physical memory if other processes need the resources).

---

### Post by nowshining on 2007-10-31
as for the keyring thing if u have it I removed it by deleting the file myself. :) if u want to lessen the RAM gnome uses BUT NOTE that u will get lines when moving windows, etc.. like wireframes..

open up gconfig editor or open up a terminal and type gconf-editor and naviate to
/apps/metacity/general/reduced_resources

and on reduced_resources check it. :) no need for a reboot as it has already taken effect however u can if u want to make sure.

---

### Post by bks on 2007-11-03
Thanks all.

---

