---
title: "Graphic mode doesn't load after login"
date: 2015-03-19
forum: General Help
---

### Post by nicolas-gallegos on 2015-03-19
HI! I've recently installed Ubuntu 14 LTS on my Notebook (DV6950LA) , which has a NVIDIA 7150M/630 integrated card.
The installation seems fine, I got some issues with display (assuming drivers compabilities), so I had to work via terminal only . After some researching,  I could install a NVIDIA driver successfully (at least what I think).  
I got it from Nvidia webpage ( [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) )
Reboot my notebook,  Login screen shows perfect! :)  . Logged in, and that's all... it just stays there, doesn't load anything else.  An empty desktop and mouse pointer, no taskbar , just nothing besides a perfect ubuntu background. 
I can still use it via terminal mode, I have run update , I also did a fresh install  (twice) , but still in the same problem. 
I don't know if it's a graphic card problem, some type of bad installation or any other type of error. 

Any suggestions? Thanks!

---

### Post by dino99 on 2015-03-19
That seems a nidia installation issue. Let it purged first, then install 'nouveau' and reboot when done:

sudo apt-get purge nvidia*
sudo apt-get install xserver-xorg-video-nouveau

you now should get a normal desktop. Install also 'synaptic' to get a userfriendly tool to update/upgrade packages with their changelog.

if you still want the nvidia driver used instead of the free 'nouveau', then from synaptic, install nvidia-304 and reboot

---

### Post by nicolas-gallegos on 2015-03-19
Thanks for the answer! 
I can't install it, for some reason it keeps telling I'm missing depecences (xorg-video-abi-15 ; xserver-xorg-core (>=2:1.14.99.902), and recommends libgl1-mesa-dri (>=9.0) )
I've tried this: 

udo apt-get autoremove sudo apt-get autoclean
 sudo apt-get update
 sudo apt-get -f install

and then I tried again, but still can't install it. 
Sorry for my newbish response :(

---

