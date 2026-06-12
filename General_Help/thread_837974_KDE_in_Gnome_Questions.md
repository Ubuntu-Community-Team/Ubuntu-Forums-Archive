---
title: "KDE in Gnome Questions"
date: 2008-06-23
forum: General Help
---

### Post by Mongo5000 on 2008-06-23
I've been quite happy with gnome since switching to linux full time, but lately, been curious as to trying Kubuntu now that Im comfortable.

My first taste of using linux was kubuntu, but my noobish brain couldn't get it figured out till sticking with gnome.

So lately i've been debating trying out kde for a bit too see if it works better for me.  I tried installing it in vmware, but it won't install.  Getting I/O errors when installing..... not sure why.

I would rather not get rid of gnome as of yet so was going to install the kde desktop.

What issues will I run into having both?  I've done some reasearch and really should see any issues, but just curious from people that have tried it?

Will the kde aps show when im logged into gnome?

---

### Post by Spaceman9 on 2008-06-23
I have Ubuntu and I installed KDE into it. I also installed Ubuntu Studio into Ubuntu before installing KDE. Ubuntu Studio uses Gnome.

There are 2 ways to get KDE. First is to install KDE from Synaptic. You can keep Gnome this way.  During the install when it asks you if you want GDM or KDM as the default pick GDM since you're only trying KDE out and not changing to it as your default desktop.

The other way to get KDE is to just install Kubuntu from synaptic but you really don't need to do that in this case.

In regard to possible issues, there really shouldn't be any but depending on your hardware who knows. I've never had any problems but that doesn't mean someone else won't. Some apps will be in both  desktops but only a few. Because you have both desktops installed you can run Gnome apps in KDE and KDE apps in Gnome, but really it's better to run most apps in the desktop they were made for..

I like both Gnome and KDE. KDE has more to it and I think is more of a “hands on” do more things from menus” desktop. Gnome is meant to not let the user change all the settings with menus and so needs more to be done at the command line.

When it comes to changing permissions Krusader (file browser for KDE) is lots better than Nautilus for Gnome. With Nautilus you get root access by pressing Alt+F2 and type gksudo nautilus and click Run.

Having said that though I use gnome about 85%  of the time and I can click on Krusader in the Gnome Applications, Accessories menu when I need to change permissions on a file or folder.

I have PCLOS 2007 with KDE on my second drive and just for fun I installed Xfce. Also to see what can be done with Gnome check out [http://distrowatch.com/table.php?distribution=opengeu](http://distrowatch.com/table.php?distribution=opengeu) combines Gnome with e17 and [http://distrowatch.com/table.php?distribution=dreamlinux](http://distrowatch.com/table.php?distribution=dreamlinux) combines Gnome with Xfce.

---

### Post by Zorael on 2008-06-23
> **Mongo5000 said:**
> What issues will I run into having both?  I've done some reasearch and really should see any issues, but just curious from people that have tried it?

Will the kde aps show when im logged into gnome?
I can't help you with the VMware thing, but at least this I can comment on. There should technically be no issues with KDE installed alongside Gnome; it's the same linux running in the background; ergo, the same hardware support. KDE apps will show when logged into Gnome, yes. If you find them cluttering, your best solution would be to open up the menu editor (alacarte), create a subsection ("KDE", "Kubuntu", anything) and move the launchers there.

As for whether to use gdm or kdm when it asks, that merely decides whose (Gnome's or KDE's) settings file for starting X to use. In essence, using gdm will make it show the Ubuntu login greeter theme, and vice versa. Regardless of which you pick, as soon as you've chosen which environment session to use at that login screen -- Gnome or KDE --  it will be set as the previous default, so not picking any such the next time will make it load the previous choice.

I hope that made sense.

---

### Post by editrix on 2008-06-23
I also have both installed. I'm using kdm because I use KDE and mainly its apps. The only issue is I get the Gnome spinning wheel instead of KDE's watch when a program loads.

---

### Post by dracayr on 2008-06-23
You might want to try enlightenment (e17), too. that works parralel with gnome (I'm using it, I can choose wether I want to use gnome or enlightenment each time I log in).

Here's a tutorial how to install it:

[http://ubuntuforums.org/showthread.php?t=546746](http://ubuntuforums.org/showthread.php?t=546746)

dracayr

---

### Post by Zorael on 2008-06-23
> **editrix said:**
> I also have both installed. I'm using kdm because I use KDE and mainly its apps. The only issue is I get the Gnome spinning wheel instead of KDE's watch when a program loads.
Can't this be changed in Kcontrol? Cursor theme under Peripherals -> Mouse -> Cursor Theme, and Launch Feedback under Appearance & Themes?

To change the global X default, enter this in a terminal.
```
$ sudo dpkg-reconfigure --config x-cursor-theme
```

---

### Post by Mongo5000 on 2008-06-23
Awesome advise everyone thanks!

So this was the instructions I was going to follow [here.]("http://www.psychocats.net/ubuntu/kde")  Does it look good?  Should give me the kde aps no?

---

### Post by editrix on 2008-06-24
> **Zorael said:**
> Can't this be changed in Kcontrol? Cursor theme under Peripherals -> Mouse -> Cursor Theme, and Launch Feedback under Appearance & Themes?

To change the global X default, enter this in a terminal.
```
$ sudo dpkg-reconfigure --config x-cursor-theme
```

Wow! Thanks for this. I can't try it at the moment--being on dialup. But I will.

---

### Post by editrix on 2008-06-24
> **Mongo5000 said:**
> So this was the instructions I was going to follow [here.]("http://www.psychocats.net/ubuntu/kde")  Does it look good?  Should give me the kde aps no?

There's many ways to do it. [www.psychocats.net](www.psychocats.net) is a wonderful site, not only for beginners. Because I'm on dialup, I had a friend burn an **alternate** Kubuntu install CD, then I added the CD to my sources list and used it to install Kubuntu. So it depends on what your resources are. But you can always trust what's on [www.psychocats.net](www.psychocats.net). And remember, you don't even need to type! Just mouse over the text and use your middle mouse button or mouse wheel to paste it.

---

