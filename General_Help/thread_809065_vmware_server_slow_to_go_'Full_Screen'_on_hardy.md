---
title: "vmware server slow to go 'Full Screen' on hardy"
date: 2008-05-27
forum: General Help
---

### Post by svaens on 2008-05-27
Hi all, 

I've been running vmware server on gutsy with no problems, 
I was able to switch to full screen in a blink of an eye, and switch back again in another blink. 

Since I installed hardy (full and fresh) and re-installed vmware server, i've noticed (to my disappointment) that when changing to and from full screen, there is this transitioning process where the screen goes all blank (like as if X was starting for the first time) it flickers a bit, and then I get my full screen showing my client operating system which I am running on vmware server. 
After that, it seems not to run any different. It is just the transitioning process. 

In changing from full screen back to the ubuntu host, it also goes through this X windowing transition processes. 

It is not a critical problem, but annoying enough to make me wonder if there is a way to fix it. 

anyone else seen the same problem??? 

Thanks in advance for any answers or posts!

---

### Post by svaens on 2008-05-29
i just thought i'd bump this.... surely someone has had the same experience?!!!

---

### Post by fjgaude on 2008-05-29
I've not seen it in all my upgrades... I do keep my View menu to have checked Auto Window / Guest. I can't say if that what's does it.

---

### Post by svaens on 2008-05-29
Hi and thanks for the reply. 

Unfortunately that didn't seem to help. 
In fact, I changed it once to (is it? ) fit window... i think, and now it won't go back to the setting it once was... and the guest is all tiny to fit the size of the vmware window.... and even when i go back to the previous setting... the screen size of the guest doesn't change back. 
hopefully when i reboot it it will regain its full size...

anyway.. slow as ever.. a good 5 seconds in-between switching from full mode and to.

---

### Post by bhurley on 2008-08-05
I know this is an old thread but I came across it when I encountered the same problem.

For me the slowness was caused by switching video modes - that is, when you switch between different resolutions, color depths, and probably even refresh rates.  If you can get the video mode of the guest OS and the computer running vmware console to match then switching to/from full screen mode is very fast.

The way I solved the problem was to copy in the /etc/X11/xorg.conf file from my old Gutsy install (in which the video modes did match) and restart X.

---

### Post by svaens on 2008-08-06
Hi, and thanks for your input!

I tried using the settings from my gutsy. 
It didn't seem to fix my problem. 
In the end I (for other reasons) I switched to using VirtualBox instead of VMWare. It seems to use a different method of making 'full screen', 
because it seems X does not need to do any refresh or restart for this.... .
so in consequence, I no longer have the problem with using VMWare. 

However, in switching to console (ctrl-alt-f3), and then back again (ctrl-alt-f7) I still see this slow switching behaviour. 
It was not only in using VMWare. 
I remember earlier days of using linux, where switching to console (and I could have sworn, with gutsy) it was instant. Not anymore. 
sean

---

