---
title: "Skip Gnome and go for XFCE?"
date: 2004-11-04
forum: General Help
---

### Post by elwis on 2004-11-04
Is it at all possible to skip GNOME within an Ubuntu install?

The reason I ask is because warty is my love, but I refuse to have two Boxes that are the same, so I have to find something else for my 2nd workstation, which also is quite  old (533 & 512 RAM).

So.. I've spent an hour on distrowatch. Gave VidaLinux 1 hour of my time but hated it. Then i realised I could not live without apt-get, and Ubuntu is the best. 

So, what is the best way to get an Ubuntu + XFCE4 station? Do i have to put in GNOME anyway and then fix it myself or is there an easier way?

Regards

---

### Post by Joeb on 2004-11-04
[QUOTE=elwis]Is it at all possible to skip GNOME within an Ubuntu install?

The reason I ask is because warty is my love, but I refuse to have two Boxes that are the same, so I have to find something else for my 2nd workstation, which also is quite  old (533 & 512 RAM).

So.. I've spent an hour on distrowatch. Gave VidaLinux 1 hour of my time but hated it. Then i realised I could not live without apt-get, and Ubuntu is the best. 

So, what is the best way to get an Ubuntu + XFCE4 station? Do i have to put in GNOME anyway and then fix it myself or is there an easier way?

Regards[/QUOTE]

Enable the Universe repository and install XFCE4 from it (but you'll have to do it after the initial install).

---

### Post by elwis on 2004-11-05
[QUOTE=Joeb]Enable the Universe repository and install XFCE4 from it (but you'll have to do it after the initial install).[/QUOTE]
 Yep, that's what i was afraid of. I hoped there were a way without filling my disk up with GNOME's, but I'll go for that route

---

### Post by diebels on 2004-11-05
Easy to do "apt-get remove remove gnome-* libgnome*", before installing xfce.

I vote for xfce in main, it's very good for old machines and looks almost like gnome.

---

### Post by elwis on 2004-11-05
[QUOTE=diebels]Easy to do "apt-get remove remove gnome-* libgnome*", before installing xfce.

I vote for xfce in main, it's very good for old machines and looks almost like gnome.[/QUOTE]
 I'm with you in that suggestion! I would love to have the choice.. actually. In a "custom install" option or something similar.

---

### Post by Poldi on 2004-11-05
[QUOTE=elwis]Is it at all possible to skip GNOME within an Ubuntu install?
...
are the same, so I have to find something else for my 2nd workstation, which also is quite  old (533 & 512 RAM).
...
[/QUOTE]

well, I have a PII-266 with 128 MByte here and I am running Gnome... admittedly this deoes not feel like the fastest thing on earth, but it is quite usable as a surf-machine.

on the other hand, a P3-700 with only 256 MByte is very productive with Gnome 2.8 over here - did you select the 686 kernel in Ubuntu yet?

nothing against XFCE, but half a Gig of RAM shouldn't make you run away from Gnome.

kind regards,
Carsten

---

### Post by elwis on 2004-11-05
select the 686 kernel? Well, nope, I just run the default install.

And no, GNOME works kind of ok on that machine. But I can't have two boxes that are exactly the same, so I had to run for XFCE :)
I really need to learn the magic from a lightweight desktop, since one of my arguments as a GNU/Linux advocate is the fact that you could get a usable workstation of old machine's. That's not all true with heavy GNOME though.

---

### Post by fng on 2004-11-05
IMHO, it is better for ubuntu and the community that the dev-team specialises in 1 WM/WE.  

I'm not saying there may not be any other WM/WE into ubuntu , but they should be unsupported by the dev team.  Linux is all about choices anyway.  So if you prefer another WM, You are on your own.

Why unsupported?
Now the dev-team can focus on 1 WM for a better and user-friendlier integration. :)

---

### Post by Poldi on 2004-11-05
[QUOTE=elwis]select the 686 kernel? Well, nope, I just run the default install.
[/QUOTE]

just search for '686' in Synaptic. you will find a meta-package that does all the magic and will provide some speedup. this is not part of the CD-based packages, though. you need the internet access and refresh.

kind regards,
Carsten

---

### Post by diebels on 2004-11-05
For myself it's not a big deal. I have good enough hardware for gnome. But there's some millions of really poor poeple in the world with low spec machines that could benefit from running xfce. And it's quite small and not much work supporting it. Maybe not full official support in main, but give it a little more attention in universe, like some packages get. Put in a human theme for it.

---

### Post by Nikola on 2004-11-05
[QUOTE=diebels]Put in a human theme for it.[/QUOTE]

Yeap, if they include xfce better to make it look like Ubuntu gnome desktop. For example, make it to use human gtk2 theme, Ubuntu wallpaper, same splash image as in Gnome,and for xfwm4 theme I'll make it, I've already made xfwm4 Industrial theme, but old style, with lines in title bar, and it's here:

[Industrial xfwm4 theme](http://xfce.lindesign.se/db/viewtopic.php?t=559) 

It's not very dificult to make new version to match Industrial metacity theme used in Ubuntu.

---

### Post by diebels on 2004-11-05
Very good :-) . Team up with some artwork developers. Put a xfce human theme on the [wiki](http://ubuntulinux.org/wiki/UbuntuArtwork)

---

### Post by Nikola on 2004-11-05
I totaly forgot I've already done it, few months ago :)
I've ported it from SmoothGNOME pack (gtk and metacity theme),
which uses Industrial metacity theme.
[Get it in this xfce forum thread](http://xfce.lindesign.se/db/viewtopic.php?t=746&sid=4108abf460efc0067aca0247fd069441) 
It picks up gtk2 theme colours, uses png images for gradients, it needs xfce 4.2.

This is my Xfce desktop in Ubuntu, too see how it looks (with Smooth-human gtk2 theme (click for full scale image):

[[IMG]http://img103.exs.cx/img103/7492/xfce.th.png[/IMG]](http://img103.exs.cx/my.php?loc=img103&image=xfce.png)

I'll change its name to xfwm4-ubuntu and add it to ubuntu wiki ASAP.

---

### Post by diebels on 2004-11-05
Nice work :-)

---

### Post by elwis on 2004-11-05
[QUOTE=Poldi]just search for '686' in Synaptic. you will find a meta-package that does all the magic and will provide some speedup. this is not part of the CD-based packages, though. you need the internet access and refresh.

kind regards,
Carsten[/QUOTE]
I stick with the OT, that was a LOT of i686 packages, am I supposed to mark them all? Suppose I'll have to reinstall nvidia-glx later too...

And That was one nice XFCE theme, I'm running standard Industrial.. can't say i know #"¤ about XFCE yet (like putting shortcuts on the desktop) but I find it very interesting, small footprint!

---

### Post by az on 2004-11-05
To answer the original question

Type "custom" at the boot prompt when installing from cd.  The installation will put a 350 meg base system on your computer.

Boot into your new system and add universe to your repositories.

sudo nano /etc/apt/sources.list

sudo apt-get update
sudo apt-get install x-window-system-core xterm xfce4 gdm menu menu-xdg synaptic 


and whatever else you want...

sudo gdm and you are off!

Good luck!

---

### Post by elwis on 2004-11-05
[QUOTE=azz]To answer the original question

Type "custom" at the boot prompt when installing from cd.  The installation will put a 350 meg base system on your computer.

Boot into your new system and add universe to your repositories.

sudo nano /etc/apt/sources.list

sudo apt-get update
sudo apt-get install x-window-system-core xterm xfce4 gdm menu menu-xdg synaptic 


and whatever else you want...

sudo gdm and you are off!

Good luck![/QUOTE]
 Nice.. I'll remember that next time (I already have GNOME & XFCE on the machine)

Man.. how will I ever be able to go back to any other distro!? I'll end up putting Ubuntu on all of the LAN members at home :)

---

### Post by Nikola on 2004-11-05
[QUOTE=elwis](like putting shortcuts on the desktop) but I find it very interesting, small footprint![/QUOTE]

You can't do that, but you can use Rox pinboard.
Rox is, beside Xfce, my favourite solution for slow pc.
Rox Filer is great file browser, extremly light and fast, and can look very nice if taken care of (change icon theme from default fugly one).
Xfce4 4.2 is awesome, with session manager, app menu, very lightweight, I just can't get used to it's file manager (xffm).

---

### Post by diebels on 2004-11-05
[QUOTE=elwis]that was a LOT of i686 packages, am I supposed to mark them all? Suppose I'll have to reinstall nvidia-glx later too...[/QUOTE]Only linux-image, libc and restricted-modules if you need them. No need to reinstall nvidia-glx.

---

