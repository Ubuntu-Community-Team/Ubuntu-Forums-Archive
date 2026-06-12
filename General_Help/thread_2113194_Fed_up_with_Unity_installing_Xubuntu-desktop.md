---
title: "Fed up with Unity installing Xubuntu-desktop?"
date: 2013-02-06
forum: General Help
---

### Post by FeraTech on 2013-02-06
I am completely fed up with Unity.

It's the worst desktop environment I've ever used. 

Currently using Ubuntu 12.10 x64

You can really tell it's one of those things that Canonical pushed for due to hype and couldn't care less about functionality.

I install Ubuntu for friends and clients all the time. Unity has led to so many headaches for me it's absurd.

1. Wine applications installed don't show up in the menu at all.
2. If you install a new application and forget what it's called you're screwed... 
3. No easy application menu in case you don't remember what an application is called.
4. Constant error message with actually no information in them.
5. Idiotic Mac based file menu at the top of the screen which occasionally even breaks and doesn't display the menu items.
6. Horrible setup to use on Dual Screens.

Has anybody has any experience just switching to Xubuntu?

I have an encrypted home directory with a Raid1 setup for root.

Not sure if it's easier to just do a clean install or would it be easy to replace Ubuntu with Xubuntu...

I do have over 1.2 terabytes of stuff on there. So I would prefer to just install Xubuntu over Ubuntu.

---

### Post by kanikilu on 2013-02-06
The lesser headache would be to just install XFCE and make it your default session when you login. Even though I use Unity daily, I still installed XFCE and LXDE to play with...

I think it was as simple as: ```
sudo apt-get install xfce4
``` I can't remember if I added the **xfce4-goodies** package or not, but...couldn't hurt.

---

### Post by FeraTech on 2013-02-06
Now if I install Xfce4 and want to get rid of unity. Is there a safe way of uninstalling it and cleaning up my system without breaking my desktop?

---

### Post by kanikilu on 2013-02-06
> **FeraTech said:**
> Now if I install Xfce4 and want to get rid of unity. Is there a safe way of uninstalling it and cleaning up my system without breaking my desktop? Uh...I don't know for sure, sorry.

On a previous system, when I didn't know any better, I just went ahead and installed the **xubuntu-desktop** meta-package, and that effectively replaced the default. I guess there are still technically remnants of the Unity system, but if you're logging into XFCE, it shouldn't really matter.

Anyways, after a quick search, it seems it would not be as simple as removing the **ubuntu-desktop** package, so unless you are willing to risk breakage, or go to extreme lengths to remove things that probably aren't even running anyways, I'd just leave well enough alone...

---

### Post by kanikilu on 2013-02-06
A search brings up this relevant page:

[http://www.psychocats.net/ubuntu/purexubuntu](http://www.psychocats.net/ubuntu/purexubuntu)

I've never tried that myself, so proceed at your own risk, but I've used information from psychocats before, and it hasn't led me astray...

---

### Post by CharlesA on 2013-02-06
> **kanikilu said:**
> A search brings up this relevant page:

[http://www.psychocats.net/ubuntu/purexubuntu](http://www.psychocats.net/ubuntu/purexubuntu)

I've never tried that myself, so proceed at your own risk, but I've used information from psychocats before, and it hasn't led me astray...

This should work. When I tried it last it worked.

---

