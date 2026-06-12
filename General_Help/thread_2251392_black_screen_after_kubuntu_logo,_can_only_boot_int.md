---
title: "black screen after kubuntu logo, can only boot into a terminal"
date: 2014-11-04
forum: General Help
---

### Post by joomla1 on 2014-11-04
I'm running a fully updated Kubuntu 14.04.01 and last night after closing lid on my Asus x5500LD it won't take me to the KDE login screen again.
I have an encrypted home directory on a partition of its own.
If I remove the quiet and splash options in grub, I can boot into a terminal as my own user but if I try to boot normally, I see the Kubuntu logo and after that, just black. I've waited 20 minutes for something to happen there but it doesn't. 
What's wrong?

---

### Post by joomla1 on 2014-11-04
Turns out the problem was that the kdm package somehow got uninstalled. I found that name when I was looking for how to start kde from the terminal and it said it wasn't installed!

sudo apt-get install kdm

That did the trick, along with a restart, I'm back to the GUI !

---

