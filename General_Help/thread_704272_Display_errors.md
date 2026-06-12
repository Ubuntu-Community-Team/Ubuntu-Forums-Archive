---
title: "Display errors"
date: 2008-02-22
forum: General Help
---

### Post by dirtyerny on 2008-02-22
So I just installed gutsy yesterday, and when I login I expected to have to download some drivers for my video card(evga 8800gt) but it tells me I don't need any when I go to display drivers. So I try and enable desktop effects, but it won't allow me to. So I figure that I do still need the drivers for my vid card, so I go to the option on administrative menu where it says something like screens something or other,  basically it's about selecting the correct monitor and display drivers. So I go to the video card  drivers and select the nvidia ones (I think i't's the nv drivers), and reboot and it tells me I have to go in low graphics mode, so I login try changing the drivers back to the original ones but nothing changes when I reboot and login. So I go back to the same menu item for the drivers and monitors and try and select my monitor(samsung 226bw) from the list so I at least use a decent resolution. So I choose my and logout and now it has like made like 4 replicas across the screen of everything, kind of hard to explain. When I login there are four username boxes across the screen and nothing is legible. I am able to login, but not abe to do anything since the "screens" overlap eachother and blur everything out. So I'm asking for a way to reset everything so I can use a good resolution and have the proper display drivers so I can use desktop effects. I don't know why this is such a problem, a few months ago when I had my evga 8800gts gutsy asked me to install the drivers right off the back and I was able to use desktop effects with no problems, though I was using a 15' monitor at the time. Help is much appreciated.

---

### Post by pointone on 2008-02-22
Try running "sudo dpkg-reconfigure xserver-xorg -phigh" from the command line to revert to the original settings.

You want the "Restricted Drivers Manager" to try installing the proprietary NVIDIA driver for your card. If this doesn't work, you could always try using Envy instead.

---

### Post by dirtyerny on 2008-02-22
> **pointone said:**
> Try running "sudo dpkg-reconfigure xserver-xorg -phigh" from the command line to revert to the original settings.

You want the "Restricted Drivers Manager" to try installing the proprietary NVIDIA driver for your card. If this doesn't work, you could always try using Envy instead.
That's the thing, Restricted Drivers manager says I don't need any drivers. I still haven't fixed the problem yet, but now when I try and install something from synatic or through the console it tells me to insert the cd. Why won't it let me download it?

---

### Post by soldats on 2008-02-22
well first you shoud check your sources.list file. its located in /etc/apt/sources.list. you should comment out the lines pertaining to the cd install and uncomment the lines for the repos like "multiverse, universe, etc" that should let you download without the cd. on top of that i would strongly urge you to not use envy as it may break your system. then you can try and get the propriatary nvidia drivers.

---

### Post by ZeroZ400 on 2008-02-22
It wants the cd because thats the first place it looks for sources according to the sources.list.  To fix it, do this
```
sudo gedit /etc/apt/sources.list
```
You need to comment out the line that says
```
deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
```

To comment it out, put a # at the beginning of the line.

---

### Post by dirtyerny on 2008-02-22
> **soldats said:**
> well first you shoud check your sources.list file. its located in /etc/apt/sources.list. you should comment out the lines pertaining to the cd install and uncomment the lines for the repos like "multiverse, universe, etc" that should let you download without the cd. on top of that i would strongly urge you to not use envy as it may break your system. then you can try and get the propriatary nvidia drivers.
There was nothing on there, about the cd but I did comment out multiverse and universe. I actually just installed envy before I saw your post xD. Though it has fixed my problem and everything seems to be working. Thanks for the help everyone.

edit:
ah, yes. It was hiding at the top, missed it. Thanks.

---

