---
title: "Odd Gnome-Terminal Behavior"
date: 2013-05-17
forum: General Help
---

### Post by Degraan on 2013-05-17
I've written and aliased a few scripts for launching some basic servers on my machine. I'd like to automate this so they all run when I start the machine, and persist the terminal session so I can monitor output. All of the scripts operate fine when launched individually, but trying to run them with a command like "gnome-terminal --tab -e sh /absolute/path/script" it returns the following error.  "There was an error creating the child process for this terminal". Most of the searches I've found for this error say it's a fstab issue, but that doesn't make sense to me since they run fine when not launching them with the "gnome-terminal" command.

Is there any easier way to launch and persist a few terminal tabs on boot, or does someone know why gnome-terminal would work when launched from the dock but not command line?

---

