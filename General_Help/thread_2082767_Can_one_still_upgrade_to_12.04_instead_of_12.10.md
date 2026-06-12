---
title: "Can one still upgrade to 12.04 instead of 12.10?"
date: 2012-11-10
forum: General Help
---

### Post by Bennot on 2012-11-10
My daughters version of Ubuntu (10.10 I believe) is no longer being supported. I've read that 12.04 will be supported for 5 years. Is there a way to update to 12.04 instead of 12.10?

---

### Post by latinlightning on 2012-11-10
Yes, you can.

Backup all data before attempting an upgrade. Then, download and burn the 12.04 iso to CD or DVD from here: [http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)

Depending on what kind of processor your current computer has, you can either try the x86 or AMD64 version (almost all newer computers support 64-bit).

---

### Post by Mr_JMM on 2012-11-10
I personally would do this as a fresh install. If you didn't already create a separate partition for /home then back up the /home directory to an external drive first. Then install 12.04 as a fresh install using the DVD you burnt. Again, if you didn't previously, now is a good time to create a separate /home partition. You only need around 10GB for /root but as a personal rule I increase this 1GB for every 100GB drive I have upto 25GB. You could even, if drive is big enough create a second /root partition the same size for testing other distro's or to test the next Ubuntu version before upgrading the main /root.

Sorry, a little more than you needed to know but I think now is  a good time to explore these options and it makes future upgrades much easier and pain free.

---

### Post by ibjsb4 on 2012-11-10
12o4 is a good choice, but I do not think trying to upgrade is.

There's been some major changes.  Gnome2 has been replaced with Gnome3; the Ubuntu desktop has been replaced with Unity.

I would recommend a fresh install.  Or better, if you have room on the HDD I would dual boot.  This would give you a chance to get use to the changes and a way to move your files to the new system.

---

### Post by Bennot on 2012-11-10
thank you. The computer is an IBM X41 and it has a Pentium M processor 1.5 GHz, 1GB RAM. Will it work?

---

### Post by ibjsb4 on 2012-11-10
> **Bennot said:**
> thank you. The computer is an IBM X41 and it has a Pentium M processor 1.5 GHz, 1GB RAM. Will it work?

Should be good.  Video drivers could be an issue, but run the live CD first and give it a test drive before you install.  Also 12o4 has two unity modes.  Default is 3d mode, but if you box can't handel 3d it will drop to unity 2d mode.  So you should be covered  :)

---

### Post by latinlightning on 2012-11-10
Bennot,

I would highly recommend you try Lubuntu 12.04. It's a much lighter version of Ubuntu with low spec computers in mind. I personally installed it on my sisters IBM ThinkPad R52 and it runs nicely.

First, download and burn the iso and try it out before actually installing it. Here's a link to the iso, make sure you get the Intel x86 version: [http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/)

---

### Post by Bennot on 2012-11-10
Thank you so much all of you for all the suggestions, and responding so quickly. I am downloading now 12.04. I am also curious about Lubuntu (never had heard of it), and I may try it. My daughter is only 8 and has been using the classic Gnome desktop, and I would like to keep it that way, as I am not too familiar with Unity. I imagine Gnome can still be used in all these new versions.
I suppose her computer will become too old at some point, I am just hoping it may last at least two more years and I don't need to keep upgrading her system in the meantime. She doesn't use it for any complicated stuff beyond some games, drawing programs, email etc.

---

### Post by latinlightning on 2012-11-10
> **Bennot said:**
> Thank you so much all of you for all the suggestions, and responding so quickly. I am downloading now 12.04. I am also curious about Lubuntu (never had heard of it), and I may try it. My daughter is only 8 and has been using the classic Gnome desktop, and I would like to keep it that way, as I am not too familiar with Unity. I imagine Gnome can still be used in all these new versions.
I suppose her computer will become too old at some point, I am just hoping it may last at least two more years and I don't need to keep upgrading her system in the meantime. She doesn't use it for any complicated stuff beyond some games, drawing programs, email etc.

Ubuntu has changed quite drastically since 10.10. Lubuntu uses LXDE as the default desktop environment. Pretty much anything you can do in Ubuntu you can do with Lubuntu. Programs may have different names but underneath they still perform the same functions as the better known programs for Ubuntu. Here's a brief look at it:
[IMG]https://tekdrops.files.wordpress.com/2012/04/lubuntu-12-04.png[/IMG]

---

### Post by MG&amp;TL on 2012-11-10
> **Bennot said:**
>  My daughter is only 8 and has been using the classic Gnome desktop, and I would like to keep it that way, as I am not too familiar with Unity. I imagine Gnome can still be used in all these new versions.


Just to make things *absolutely* clear, Gnome 2.x is now dead as a dodo (and has been for several versions). Gnome has now moved on to 3.x, which is drastically different.

While there are several options for those wanting the old Gnome 2 look (MATE is an actual clone, and gnome-panel, gnome-fallback, and cinnamon all provide a similiar experience), IMHO now would be a good time to get a modern alternative such as Xfce, or LXDE. You could of course, use Unity or Gnome shell, but as both of these require reasonable hardware and hardware acceleration (thus also ruling out KDE), I would strongly suggest the former two.

---

### Post by Bennot on 2012-11-10
That looks clear and straighforward. I will try both running them from the CDs first. It's going to take me a few days but I suppose it has to be done as she is no longer getting any updates on her system. Thanks again.

---

### Post by ibjsb4 on 2012-11-10
If you decide that unity is too much, then install gnome-classic.  It looks like the old gnome you run in 10.10 and it may run a little faster than unity.  It can be added to 12o4 and chosen at boot (login).  Its in the software center.

Also MG&TL has good points about other choices.  I have installed xubuntu on older boxes with less resources than yours with good results.  And again, the LXDE and/or XFCE desktop can be install to 12o4 and chosen at boot.  They too are in the software center.  No need to burn l/xubuntu cd's to try out the desktops.
[]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal")

---

### Post by ugm6hr on 2012-11-10
As with everyone else's suggestion - a 12.04 Ubuntu derivative sounds like a sensible option.

I would personally suggest Xubuntu (Ubuntu + XFCE desktop).

Be aware that while the underpinnings of Lubuntu (Ubuntu + LXDE desktop) are the same as Ubuntu 12.04LTS, the LXDE components are not going to be supported beyond 18 months.

Hence, the recommendation for XFCE as being very Gnome 2 - like, but supported for a few years from now, and still being developed.

---

### Post by grahammechanical on 2012-11-10
Just to confuse you even further, as your daughter is only eight, have you looked here?

[http://www.edubuntu.org/]("http://www.edubuntu.org/")

You can even try it out online. Look for the link to Edubuntu WebLive.

If it works on that machine then 12.04 of whatever flavour would be the best choice.

Regards.

---

### Post by deserthowler on 2012-11-10
> **Bennot said:**
> My daughter is only 8 and has been using the classic Gnome desktop, and I would like to keep it that way, as I am not too familiar with Unity. I imagine Gnome can still be used in all these new versions.

This transition will probably be less traumatic for your daughter than for you.  Since the demise of Gnome 2, I install Linux Mint Mate 13 on computers for people.  They are happy with it.  Mint is the best knock-off of Ubuntu and Mint 13 is LTS.  I was never happy with Lubuntu or Xubuntu on my P4 but Mate is OK.  Unity 2D is OK but is really slow and hard to customize.  Gnome fall-back will probably not be supported for very long.

Earl

---

### Post by ibjsb4 on 2012-11-10
> **deserthowler said:**
> This transition will probably be less traumatic for your daughter than for you.   Gnome fall-back will probably not be supported for very long.

I was thinking the same thing when it comes to kids  :)

Gnome Classic will be supported for the life of 12o4

---

