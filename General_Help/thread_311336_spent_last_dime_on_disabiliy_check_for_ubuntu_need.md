---
title: "spent last dime on disabiliy check for ubuntu need quick/easy way get Compiz to work"
date: 2006-12-02
forum: General Help
---

### Post by creepshow on 2006-12-02
spent last dime on disabiliy check for ubuntu need quick/easy way get Compiz to work.  i'm using edgy eft.  i've tried beryl.  had alot of problems.  i tried compiz from the wiki and there was no gnome-window-decorator on my system.  i'm stumped.  i need just a basic rundown on how to get it to work optimally.  i'm using a Geforce 6200 128MB that isn't correctly detected my xorg.  i saw a post recently on how to get it to work.  followed it exactly it was very very recent.  the repo was outdated or it simply didn't work.  

help !  i need to start on other ubuntu matters :)  

thanks

](*,)

---

### Post by creepshow on 2006-12-02
i tried beryl and used the freenode #beryl ubuntu repo for edgy and couldn't get that to work either.  i'm cursed.  the curse of king tut has gotten to me i'm going to croak if i can't get a quick and easy solution for an uber cool composite manager working

---

### Post by nalmeth on 2006-12-02
> i'm using a Geforce 6200 128MB that isn't correctly detected my xorg. 
What do you mean?

Do you have an onboard intel card, your nvidia being pci or agp? 

What has gone wrong with beryl?

Does glxinfo in the terminal tell you 
Direct Rendering = Yes

---

### Post by creepshow on 2006-12-02
its AGP.  i am reinstalling for the 5th time edgy eft.  i will check on direct rendering when its done.  i guess i need simplified directions on how to definitely get compiz to work.  i think it would have worked last time if there was a gnome-window-decorator or manager or something like that or perhaps it was the order they were placed in my Gnome sessions.  i dont know.  nothing at all wrong with Beryl if you or anyone would like to simplify the directions for me in a post that will allow me to update it as it progresses and doesn't give me errors on a new edgy eft install with update universe and multiverse repos and nothing else i'd be wonderfully happy in death and fashion.

---

### Post by nalmeth on 2006-12-02
You won't have direct rendering out of the box. You have to install nvidia-glx to get NVIDIA's proprietary driver. Beyond that, there are a few things that could be stopping it from working.

DO you have an intel integrated onboard graphics card? Because to get direct rendering from my PCI Nvidia card, I had to follow this guide to disable the onboard intel card, and then install the nvidia driver:
[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)

That may or not apply to you, but if after installing and enabling nvidia-glx, you still don't have direct rendering, that may be the cause, assuming you might have an intel card. . 

I followed this guide to setup Beryl+AIGLX on Edgy.  I cannot guarantee its safety or effectiveness for your particular machine. It should be straightforward to follow. . Instructions for installing nvidia driver included aswell.
[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)

Good luck!

---

### Post by LLRNR on 2006-12-02
> **nalmeth said:**
> 
I followed this guide to setup Beryl+AIGLX on Edgy.  I cannot guarantee its safety or effectiveness for your particular machine. It should be straightforward to follow. . Instructions for installing nvidia driver included aswell.
[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)

I second that. I installed Beryl from doc.gwos.org too and it's working great.

LLRNR

---

