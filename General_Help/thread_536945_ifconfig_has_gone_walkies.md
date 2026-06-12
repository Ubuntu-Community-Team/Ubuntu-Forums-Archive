---
title: "ifconfig has gone walkies"
date: 2007-08-28
forum: General Help
---

### Post by b0ng0 on 2007-08-28
I tried installing Vector Linux over the weekend and selected my /home partition in Ubuntu to be mounted as /home in VL. I decided I didn't want Vector so I erased it.

The problem is that for some reason when I loaded up Ubuntu it was using Xfce cursors, some icons had been uninstalled, the terminal was giving me a weird message and there were all sorts of weird documents on my desktop...

So far i think I have cleaned up my Ubuntu install quite well but for some reason when I type ifconfig into the terminal it says it is not installed. I have tried reinstalling it through Synaptic (which thinks it IS installed) and it comes up with the same "not installed" message in the terminal. I have a feeling it is to do with the $PATH but I really don't know...

---

### Post by prince_niceguy on 2007-08-28
do a echo $PATH  in the terminal

# echo $PATH

if the path has /sbin then there should not be any isssue. Try locating ifconfig using

# locate ifconfig

or

# which ifconfig

whichever directory comes up put it in the path. It can be set in .bashrc in your home folder.

---

