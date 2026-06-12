---
title: "cannot open display after reboot"
date: 2018-10-06
forum: General Help
---

### Post by ulrichmuc on 2018-10-06
After reboot, when starting gvim, I get 
   E233: cannot open displayVim: Warning: Input is not from a terminal
When I reboot again, the problem vanishes.
Sometimes I need to reboot more than once to get rid of the problem.

Any ideas?

PS: Ubunto/mate 16.04 LTS. 4.4.0-137-generic #163-Ubuntu SMP  i686 i686 i686 GNU/Linux
but also with earlier kernels

---

### Post by TheFu on 2018-10-06
Does regular vim work?
What about other X11-based programs?
Did you ever use sudo with gvim?

---

### Post by ulrichmuc on 2018-10-06
Does regular vim work? Yes
What about other X11-based programs? Examples? (xterm runs without problems).
sudo gvim works.
echo $DISPLAY gives :0.0

---

### Post by TheFu on 2018-10-06
If you used sudo gvim, the some settings files for gvim  may be owned by root now.  Fix that.

It is always best to use **sudoedit {path-to-file}**.  If you want gvim to be the editor, fine.  **export EDITOR=gvim** to the bottom of your shell initialization file.  Dont use a GUI editor on a system that doesnt have any GUI, like most  linux servers.

---

