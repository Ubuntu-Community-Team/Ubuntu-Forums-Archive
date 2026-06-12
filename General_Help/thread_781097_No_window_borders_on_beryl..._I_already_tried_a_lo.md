---
title: "No window borders on beryl... I already tried a lot of things"
date: 2008-05-04
forum: General Help
---

### Post by Stratok on 2008-05-04
So i see a lot of people has this problem too...
have to add that im new in linux and that i already reinstalled it 4 times...

so my friend has beryl so i wanted to try it.  after some copy paste from internet I managed to install beryl... cube (hexagon in my case) woobly windows, effects to minimize... everything works yust fine, but I have no window borders (managed to configure beryl with some control, super and alt + mouse to manage windows... ) and well ive tryed all this things:

yes, the windows decorator is on, yes it works with compiz
yes my video card is nvidia (5200) so 
Yes, I've added the thhe lines to the xorg.conf
Option         "AddARGBGLXVisuals" "True"
Option         "RenderAccel" "True"
Option         "AllowGLXWithComposite" "True"
Option         "backingstore" "True"
Option         "TripleBuffer" "True"

yes, my default deph is 24

somebody advised me to instal the correct driver for my video card... i downloaded it  from [www.nvidia.com](www.nvidia.com)    nvidia gefoce fx 5200  but I could nerver install it because first it said I need to be loged as root... (i found out the word "sudo " before the comand in the terminal... than it said that the x sesion was on, but if I turn it off i have no screen, anyway i fixed tht and then it says something about some kernel or something... i gave up.)


I even tried:
sudo apt-get remove emerald
sudo apt-get clean
sudo apt-get install emerald

Seems that the problem is someqhere else, Ive read in some forums to start emerald in terminal... and copy paste the error message, but i dont know how to run emerald from terminal xD...

Would be nice if anyone could help me, because some effects like zoom, draw on screen , etc... can be very usefull




=)

---

### Post by gsiliceo on 2008-05-04
THis is your lucky day i have the same graphic card =).

WHy are you installing beryl? compiz fusion is better in every aspect, just wondering. Arent you confusing the packages? 

I solved this problem adding the frequency of my monitor and resolution of my screen to my xorg.conf.
THis is my recommendation for you:
1 .Uninstall every trace of beryl(use synaptic to find all the packages)
> system>administration>*synaptic
2.Install compiz, as you said it works for you.
3.Install the nvidia-settings package and open it 
system>administration or system<preferences i cant remember.
4.Now, that program has the hability to configure your screen settings with xorg.conf /etc/X11/xorg.conf, but it usually does a lausy job, what it does right is getting the correct lines for resolution and monitor frequency, you need to copy this lines from the file xorg.conf preview that it offers and paste it in the same sections in your original xorg.conf, you'll need to open it with sudo.

Adding the monitor frequency to the monitor section, and the resolution to the screen section solved my problems with the decorator. 
Tell me how it goes.

---

