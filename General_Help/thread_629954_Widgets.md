---
title: "Widgets??"
date: 2007-12-02
forum: General Help
---

### Post by motermouth on 2007-12-02
I heard of a widgets program called compiz...is that one? I want a program that is good and looks professional like the new windows one, mac one, or yahoo widgets. I need suggestions and i tried gdesklets and it looked cheap...even though its free.

I downloaded compiz and a couple of other ones that should work and in their instructions it says to type `./configure' and then `make' and then `make install'...well my problem is that when i type the make or the make install it says: `make: *** No targets specified and no makefile found.  Stop.' and i can't finish the installation or get it to work!! Whats wrong?? I'm getting kinda sick of linux because it doesn't come w/ everything you need...it seems like ever time you wanna do something you have to download an attachment or something...but if i could just get compiz to work that would be great!!

---

### Post by PeterJS on 2007-12-02
> **motermouth said:**
> I heard of a widgets program called compiz...is that one? I want a program that is good and looks professional like the new windows one, mac one, or yahoo widgets. I need suggestions and i tried gdesklets and it looked cheap...even though its free.

Compiz is actually a window and composite manager so it does a whole bunch of stuff related to the interface. All widget systems require a composite manager to work, of which compiz is the most used, there are other composite managers; xcompmangr, and kcompmgr. But neither of those really only handle compositing and transparency, xcompmgr was only meant as a demo and reference implementation, and kcompmgr has been replaced by Plasma, which is KDE only and not released yet.

> 
I downloaded compiz and a couple of other ones that should work and in their instructions it says to type `./configure' and then `make' and then `make install'...well my problem is that when i type the make or the make install it says: `make: *** No targets specified and no makefile found.  Stop.' and i can't finish the installation or get it to work!! Whats wrong?? I'm getting kinda sick of linux because it doesn't come w/ everything you need...it seems like ever time you wanna do something you have to download an attachment or something...but if i could just get compiz to work that would be great!!There really is no reason to be installing compiz manually, if you're running 7.10 it comes pre-installed and just needs to be configured.

Here's the documentation on installing Compiz on Fiesty (if you need that), and configuring it on both Fiesty and Gutsy:
[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

As for widgets, I would suggest screenlets, they aren't in the standard repositories, but there's usually a thread somewhere on the forum about how to install them.

---

### Post by motermouth on 2007-12-02
ok now i've installed screenlets and i've downlaoded 3 screenlet thingys and put them in .screenlets folder but now how do i add them so that they work or how do I install them?

---

### Post by daengbo on 2007-12-02
The are several widget sets available, including gdesklets (which you don't like), adesklets (also available from the repowsitories), and screenlets. Screenlets need to be downloaded and installed with "sudo make install." There are also widget sets by Yahoo and Google which I understand can be used on Linux with some work. I don't personally use widgets because I find that I don't need or want them.

I don't want to be defensive, but I need to answer this comment:
> I'm getting kinda sick of linux because it doesn't come w/ everything you need...it seems like ever time you wanna do something you have to download an attachment or something.
In all honesty, it's true that you may need to install other things (depending on your needs), but it isn't any different in that way than MS or Apple offerings. I spend much less time installing programs in Ubuntu than I do setting up a new Windows computer.

---

### Post by santiagoward2000 on 2007-12-02
> **motermouth said:**
> ok now i've installed screenlets and i've downlaoded 3 screenlet thingys and put them in .screenlets folder but now how do i add them so that they work or how do I install them?

That's easy! Just open **screenlets-manager** (in Xubuntu is under Applications/Settings, not sure about Ubuntu) or just type:
```
screenlets-manager
```
in a terminal.
This should open a window, where you can select and launch the screenlets you want.
Cheers!

---

