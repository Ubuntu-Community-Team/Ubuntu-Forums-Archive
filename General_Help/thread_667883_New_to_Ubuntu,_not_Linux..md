---
title: "New to Ubuntu, not Linux."
date: 2008-01-14
forum: General Help
---

### Post by grey.kingsley on 2008-01-14
Hey everyone! I've been using linux for the majority of the time I've spent using computers. The vast majority of that time was spent using gentoo. I recently installed ubuntu on a desktop of mine for a variety of reasons and I just have a few simple questions.

1. On gentoo, using fluxbox, I'm accustomed to having a "slit" stuck on the desktop with widgets allowing me to monitor things like acpi status, load average, disk usage, system temp., etc. I assume there is something comparable under ubuntu. Preferably something always visible, whether it's on one of the top or bottom menu bars or stuck on the desktop(in a vista sidebar manner). Really what I'm looking for are a temperature monitor and a network usage monitor. Any suggestions?

2. It's a relatively old desktop and the graphics card wasn't very good when I bought it. I remember hearing xubuntu was less graphics intensive so I'd like to use it. How do I go about this? Is it simply a matter of installing xfce with synaptic package manager or what?

3. I would really like to start pushing FOSS on my friends, family and strangers. Being the most easy/user friendly distribution IMHO, I'd like to do this by recommending ubuntu. Are there any tutorials or anything where I can go to learn enough about ubuntu so that people I know can come ask me if they have any questions about using it?

Thanks in advance everyone!

-GK

---

### Post by joao82 on 2008-01-14
1- I use gdesklets for that. it's very simple and comes with a bunch of widgets already available.
2- I'm using Ubuntu 7.10 on a desktop with only a 64Mb graphics card. It's good enough, and I can even get the special effects working, but a bit slowly. Anyway I don't need it.
3- [http://ubuntuguide.org/](http://ubuntuguide.org/) this should be fast and painless.

---

### Post by jviscosi on 2008-01-14
> **grey.kingsley said:**
> 1. On gentoo, using fluxbox, I'm accustomed to having a "slit" stuck on the desktop with widgets allowing me to monitor things like acpi status, load average, disk usage, system temp., etc. I assume there is something comparable under ubuntu. Preferably something always visible, whether it's on one of the top or bottom menu bars or stuck on the desktop(in a vista sidebar manner). Really what I'm looking for are a temperature monitor and a network usage monitor. Any suggestions?


You could install Fluxbox and run it instead of Gnome or XFCE; that's what I do.  (Officially, my install is Xubuntu.)  Otherwise Gnome and XFCE both have lots of  applets (including temperature and network usage) you can stick in the panels, and XFCE even has a panel applet that you can use to hold Gnome panel applets.  

EDIT: I should warn you that the Gutsy Fluxbox package is broken in a couple of important ways, so if you decide to run it you might want to download it and compile it yourself.  There are various threads that discuss this.  I can point you at some if you're interested.

Also, [this guy]("http://goodies.xfce.org/projects/panel-plugins/xfce4-wmdock-plugin") has been working on an XFCE panel that swallows dockapps (a la KDE's extra Kicker panel that does the same thing).  It was a little buggy the last time I used it but has probably improved since then.  I think you'll have to compile it yourself but if you used to run Gentoo that's not gonna scare you.  ;-)

I've also used gDesklets for this purpose, as another poster mentioned.  They typically aren't always on top but there is a simple key combination (user-definable, I believe) that will raise and lower them.

---

### Post by RedSquirrel on 2008-01-15
1. conky (text-based) or gkrellm or you could just install fluxbox and use its slit.

2. **xfce4** is the core xfce package. You could install xubuntu-desktop which would give you the Xubuntu distro, but then you'd have to strip out the GNOME services and so on to speed things up. When I played with Xubuntu, I installed it using the Xubuntu iso and a blank hard drive.

If you really want speed, go for a minimal install. This should give you an idea:

[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

EDIT: There are some tips for compiling fluxbox (on Ubuntu) in the link in my signature.

3. [http://help.ubuntu.com](http://help.ubuntu.com) was a good start the last time I looked at it. 

Ubuntu shouldn't be too hard to pick up. ;)

The main difference I can think of is the package manager. Synaptic's GUI interface is easy to use, but after a while you might want to use the command line instead, either apt-get or aptitude. The manpages are helpful.

---

