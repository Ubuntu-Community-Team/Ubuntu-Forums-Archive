---
title: "[SOLVED] switch to bare bone ubuntu"
date: 2008-04-19
forum: General Help
---

### Post by M4rotku on 2008-04-19
Is there any way that I can easily switch from Ubuntu 7.10 to Bare Bone Ubuntu?  I don't really know what bare bone is, but I read that it is better on slow computers than Xubuntu and the computer in question is uber slow.

Can someone give me a quick how-to guide on switching to it?

Much thanks,
M4

---

### Post by oilchangeguy on 2008-04-19
> **M4rotku said:**
> Is there any way that I can easily switch from Ubuntu 7.10 to Bare Bone Ubuntu?  I don't really know what bare bone is, but I read that it is better on slow computers than Xubuntu and the computer in question is uber slow.

Can someone give me a quick how-to guide on switching to it?

Much thanks,
M4

please give the specs of your computer. and when is the computer slow? on the internet? not on the internet? both?

---

### Post by M4rotku on 2008-04-19
The computer is slow in general.  It is at least 7 years old.  I don't know how to get to the system information in Linux so you will have to tell me how for more details.

---

### Post by oilchangeguy on 2008-04-19
> **M4rotku said:**
> The computer is slow in general.  It is at least 7 years old.  I don't know how to get to the system information in Linux so you will have to tell me how for more details.

the easiest way to get the info would be from the computers bios. you've got to have at least 256mb of ram to even install ubuntu. so given that, the computer shouldn't be that bad. test your internet connection speed at [www.speakeasy.net](www.speakeasy.net) click on speed test, and click on a server nearest to you. i've had a on and off problem with connection speed (i've got cable based internet) and found out the cable from the pole to the house is bad. the cable company replaced the cable, problem solved.

---

### Post by M4rotku on 2008-04-19
How do I access the computer bios?  the internet speed is not a problem, that works fine for all of the gaming that I do.

---

### Post by LaRoza on 2008-04-19
> **M4rotku said:**
> Is there any way that I can easily switch from Ubuntu 7.10 to Bare Bone Ubuntu?  I don't really know what bare bone is, but I read that it is better on slow computers than Xubuntu and the computer in question is uber slow.

Can someone give me a quick how-to guide on switching to it?

Much thanks,
M4

Bare bones? See my blog and the iBook entry. Do you want that?

If you want it to be very light, install Fluxbox or IceWM. You can chose them when you log in under Sessions.

---

### Post by M4rotku on 2008-04-19
If you are refering to the style of your wiki, it looks fine to me, i could live with something like that :)

---

### Post by LaRoza on 2008-04-19
> **M4rotku said:**
> If you are refering to the style of your wiki, it looks fine to me, i could live with something like that :)

Whoops. I meant blog, not wiki. A 'bare bone ubuntu' means no GUI to me.

IceWM is a good lightweight DE that has all the features you probably want. Install Thunar (don't use Nautilus) for file management.

---

### Post by M4rotku on 2008-04-19
This seems complicated, I think i'm just going to switch to Xubuntu.  I can't live without a GUI and if Ubuntu is running at all on it, then Xubuntu will be able to as well.  Thanks for explaining bare bone ubuntu to me.

---

### Post by LaRoza on 2008-04-19
> **M4rotku said:**
> This seems complicated, I think i'm just going to switch to Xubuntu.  I can't live without a GUI and if Ubuntu is running at all on it, then Xubuntu will be able to as well.  Thanks for explaining bare bone ubuntu to me.

You don't need to do another install. 

[code]
sudo apt-get update && sudo apt-get install xubuntu-desktop
[code]

You can then use it when you log in (under Sessions)

---

