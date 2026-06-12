---
title: "[SOLVED] playing command at gnome startup fails. Please HELP!"
date: 2007-12-12
forum: General Help
---

### Post by realthor on 2007-12-12
Hello, this is driving me crazy. I am trying to run this command at gnome startup:

gconftool-2 -s --type=string /apps/compiz/general/allscreens/options/lower_window_key "<Super>space"

This is because I can't set the lower window key in Compiz config and seems that in gnome configuration editor I need to set this at every login so that it has effect. Anyway, it seems to have also no effect if I put this in sessions > startup programs. I guess it gets executed as if I change this command to XINE for example it opens up xine next login. 

If I play this manually in terminal it always has effect. What am I doing wrong. I even created a file containing:

#!/bin/bash
sh -c 'gconftool-2 -s --type=string /apps/compiz/general/allscreens/options/lower_window_key "<Super>space"'

which I put in startup but the same happends.

Please help me, I can't find any solution.

---

### Post by p_quarles on 2007-12-12
A couple questions:
1) Is it just me, or is there an extraneous space in the word "window"?

2) When running this as a script, did you make the file executable?

---

### Post by realthor on 2007-12-12
oh, that is just a typo. The command is correct here as long as I can play it manually and it works.

As about the bash script it is executable.

I wonder why played from a terminal works every time while from startup it never works. Should it have some permissions set differently?

---

### Post by p_quarles on 2007-12-12
My guess is that there's a Compiz setting that's overriding the command. That would explain why you  can get this work manually (after Compiz is fully loaded), but are not seeing the correct effect when you put it in the session startup.

The solution would be to use the sleep command to delay the command for a few seconds (~10).

---

### Post by realthor on 2007-12-12
Solved this in Compiz (CCSM>Preferences>uncheck Enable integration with the desktop environment).

Thanks anyway. (How am going to mark the thread solved?)

---

### Post by p_quarles on 2007-12-12
Click on the "thread tools" button at the top of the page, and you'll see the option to mark it solved.

---

### Post by drs305 on 2007-12-12
> **realthor said:**
> Thanks anyway. (How am going to mark the thread solved?)

Go to the top right of the original post. Click Thread Tools. There is an option to mark the thread solved in the options.

---

