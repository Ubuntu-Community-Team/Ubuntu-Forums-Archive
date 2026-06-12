---
title: "Question about low ram laptop"
date: 2007-05-17
forum: General Help
---

### Post by Atreus12 on 2007-05-17
I currently have a laptop with running DSL. The laptop is 600 mhz, 64 mb ram, and 6 GB hard drive. The laptop used to run Win98, but as soon as I got into linux (6 months ago) I knew there had to be something for this laptop. DSL was recommended, and DSL is great (expecially for the new user), but it's missing some program that I use. For example LaTeX. Also, it gets annoying that it doesn't have a 'full' version of vi, you can't split windows. There are numerous other things that make me think that DSL is not the optimal OS for this application.

I thought about installing Ubuntu 7.04 server, and not installing X. But truth be told, I need some 'graphics' abilities.

What I want is to install a debian based OS (I want apt), and to have a terminal focused window manager, but still has the capacity to use an internet browser, view pdf's etc.

Is this even feasable on this system? Would I be better off with Ubuntu or Debian? Is there a window manager that fits these requirements?

Skill level - slightly above beginner, but with decent terminal skills

-Andrew

PS I want apt....but I hear gentoo is easy on system resources. Based on my laptop and my skill level, is this a feasable last resort?

---

### Post by hardyn on 2007-05-17
you are going HAVE to get some ram into that machine for any of the above.
ebay, salvage company... whatever...

---

### Post by Atreus12 on 2007-05-17
so 64 mb ram will not even run an operating system without X?

I'm not going to spend any money on the laptop. It has some proprietary bios/motherboard, and will only accept 'official' HP ram...too much $$$$

---

### Post by Delkster on 2007-05-17
> **Atreus12 said:**
> so 64 mb ram will not even run an operating system without X?

It definitely should. You can probably get X running, too, but you may want to look into some of the lightweight window managers like fluxbox or IceWM (I've never used either, but I have the impression that the former can take a bit of tweaking to get it to your liking). Xfce, which is used by default in Xubuntu, might also work. In any case you'll probably want to avoid memory-hogging applications like Firefox.

One way to do it might be to do a server install of Ubuntu (or just Debian without the big desktop environments, but I don't know what the Debian installer nowadays is like and what kinds of options it offers), and install the stuff you need on top of that. I've set up a bare-bones Ubuntu server on a virtual machine with 128 MiB of virtual RAM for it (if I remember correctly) and with only the bare-bones install without X it took just ~20 megs of RAM right after booting. With 64 megs there won't be much left for disk cache or other fancy stuff, and you'll probably be swapping quite soon particularly if you run anything even somewhat memory intensive, but it should run and might be worth using.

---

### Post by jjalocha on 2007-05-17
I think [Fluxbuntu]("http://fluxbuntu.org/") might be exactly what you need. An Ubuntu based distro built around Fluxbox. There is a development release (based on Dapper?) that is being used quite successfully by many with old hardware, and their first official (Feisty) release is around the corner. They are a nice community too.

God luck!

---

### Post by aysiu on 2007-05-17
If you don't want to go for Fluxbuntu, here's another alternative:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by Atreus12 on 2007-05-17
Thanks for all the info so far. It seems like more information generates more questions ;)

* For a server install (theoretically) which would use less ram, Debian or Ubuntu?

* Are programs specific to icewm? Meaning, will I need to hunt (or add repos) specifically for icewm? I would like to use programs like dillo, evince, and sylpheed.

* How do the repos of debian compare to Ubuntu, and how does the apt behavior compare? In Ubuntu its really easy, just add sources and type aptitude install. Is this equally easy in Debian?

* way out from left field....gentoo? Given my low system resources, is this something I should be looking into?

---

### Post by Delkster on 2007-05-17
> **Atreus12 said:**
> * For a server install (theoretically) which would use less ram, Debian or Ubuntu?
That's probably a matter of preference.

> * Are programs specific to icewm? Meaning, will I need to hunt (or add repos) specifically for icewm? I would like to use programs like dillo, evince, and sylpheed.
No, you can also run Gnome and KDE applications just like you could (generally) with any other window manager as long as you have the corresponding libraries installed. Apt takes care of that part for you.

Evince seems to be quite hungry for memory, though. Xpdf (and gv or something if you need to read PostScript files) might be a more lightweight option although personally I don't like it that much.

Also, in general it's not just the desktop that is a little heavy in Gnome and KDE. That also extends to a lot of the applications, so I'm not quite sure you'll want to be running many of those.

> * How do the repos of debian compare to Ubuntu, and how does the apt behavior compare? In Ubuntu its really easy, just add sources and type aptitude install. Is this equally easy in Debian?
Yes, it is.

> * way out from left field....gentoo? Given my low system resources, is this something I should be looking into?
Given that any interesting performance gains (if there indeed are any) could probably be achieved by compiling and optimizing for your machine... I'd go for "no" because you don't want to be compiling the stuff on that system in the first place.

---

### Post by Atreus12 on 2007-05-17
> **Delkster said:**
> 
No, you can also run Gnome and KDE applications just like you could (generally) with any other window manager as long as you have the corresponding libraries installed. Apt takes care of that part for you.

Evince seems to be quite hungry for memory, though. Xpdf (and gv or something if you need to read PostScript files) might be a more lightweight option although personally I don't like it that much.

Also, in general it's not just the desktop that is a little heavy in Gnome and KDE. That also extends to a lot of the applications, so I'm not quite sure you'll want to be running many of those.


Ok, here's a 'for instance'

I use apt to install a program that natively runs in gnome. Because it has to load the corresponding libraries, is it going to be a memory hog? Because that would be kind of defeating the purpose.

---

### Post by Delkster on 2007-05-17
> **Atreus12 said:**
> Ok, here's a 'for instance'

I use apt to install a program that natively runs in gnome. Because it has to load the corresponding libraries, is it going to be a memory hog? Because that would be kind of defeating the purpose.

Not necessarily, because only the parts of the library that are actually accessed are loaded into memory.

In practice, though, particularly mixing stuff from several desktop environments (or, rather, GUI toolkits) tends to eat into the memory more than staying consistently with one because you'll have the libraries of several toolkits loaded rather than just one.

You'll probably just have to try and find out which ones suit your needs and hardware.

---

### Post by Chetamonye on 2007-05-18
I thought my laptop was inadequate when it came to memory.  64 megs is pretty low.  I am running with 296, but 64 is taken by the graphics card.  I installed xubuntu, but I run fluxbox.  It's much quicker than when win 98se was installed.  

I would second the suggestion of doing a server install, then apt-get fluxbox.  If you are comfortable doing installs, I would suggest a debian server install.  

One thing you might try is a slackware install.  My laptop absolutely screamed when I installed slack.  I would have stayed with it, but I like being able to apt-get programs.

Chet

---

### Post by floke on 2007-05-18
I have an old Satellite pro with 64mb RAM which runs Xubuntu quite happily (alternative install better than LiveCD though)

---

