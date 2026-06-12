---
title: "Diff between desktop and server edition of Hardy"
date: 2008-06-12
forum: General Help
---

### Post by tnek on 2008-06-12
Hi,

I'm wondering how I can get information on what differs between the desktop and server edition of Ubuntu hardy? The [web page]("http://www.ubuntu.com/") isn't technically oriented enough for me to base my decision purely on it.

I want to install a very basic system for my desktop computer. I'm not interested in Gnome, KDE or XFCE and do not wish to use any of the default applications that come with the normal desktop installations. Rather, I would like to install what I need when I need it. And for window manager I want to use Awesome.

I've thought about choosing another distribution, like archlinux. But if it's possible I would like to continue using Ubuntu. Due to the huge package repository and nice community.

I do have problems getting technical information on differences between kernels and default settings in the desktop and server editions. Could someone please point me in the right direction?

---

### Post by RSingh on 2008-06-12
Well to keep it simple, I would say that the server edition is for servers thus there will be no GUI interface, no desktop, no multimedia applications etc, basically not a option for a normal human/home user.

The desktop edition is the one for a normal user and if you choose the live CD you will get the most basic set of software bundled to cater your needs (multimedia, web browsing etc). The DVD version will give you a more expansive choice of software to install and would be especially good for a user who doesn't want to go through the hassle of downloading more software.
I am not sure if the awesome window manager will be available in the DVD or CD release and you may have to install it separately.
Hope this helps in your choice. :)

---

### Post by blazercist on 2008-06-12
Well, perhaps I can answer some of those questions...

the server version of ubuntu has no gui, so you wont get any desktop environment or any gui frontends or apps.

What you will get instead of the gui apps is server oriented stuff like LAMP etc...

The kernels are basically the same except for some optimizations for server related applications, I cannot get into the specific differences because I really don't know them.  But I'm pretty sure its the same kernel with some minor adjustments in menuconfig that you would be able to make yourself if you decided to compile  your own.


I'm sure you can install a window manager ontop of the server environment and it will operate nicely, I've never done it before because I find that ubuntu (gnome) fits my needs and is pretty zippy.

If you are not interested in a tweaked kernel or server applications and are open to suggestions there is fluxbuntu which is ultra minimal and very fast. Flux is a window manager so its not as heavy and lethargic as a DE like gnome kde or even xfce.

---

### Post by snowpine on 2008-06-12
Hi Tnek, here is a useful guide to installing minimal ubuntu, then building it up from there: [http://psychocats.net/ubuntu/minimal](http://psychocats.net/ubuntu/minimal)
It assumes you are using IceWM but you could just substitute the windows manager of your choice. 
What you are trying is not that uncommon; so you should get some good advice here.

---

### Post by mishathegoat on 2008-06-12
If you're lookin' to install your own window managers, login managers, file managers, and also exclude the prepackaged software that comes with the Ubuntu Desktop, I'd go with Ubuntu Server. Right now, I'm running Fluxbox, XFE, GDM and I love it! All installed on top of Ubuntu Server 8.04

---

### Post by tnek on 2008-06-15
> **RSingh said:**
> Well to keep it simple...server edition is for servers ... basically not a option for a normal human/home user.

The desktop edition is the one for a normal user and if you choose the live CD you will get the most basic set of software bundled to cater your needs (multimedia, web browsing etc). The DVD version will give you a more expansive choice of software to install...

Thank you for your input. However I would like to know a bit more on the technical side of things. :) I want to be able to choose what I want myself. I have my own favorites when it comes to web browser, e-mail application, etc. I want as little bloat as possible, but I still would like to use the package repository of Ubuntu linux.

> **blazercist said:**
> ...server version..no gui..gui frontends or apps...you will get instead...stuff like LAMP...

kernels are basically the same except for some optimizations for server related applications, I cannot get into the specific differences because I really don't know them. But I'm pretty sure its the same kernel with some minor adjustments in menuconfig that you would be able to make yourself if you decided to compile your own.

I'm sure you can install a window manager ontop of the server environment and it will operate nicely, I've never done it before because I find that ubuntu (gnome) fits my needs and is pretty zippy.

If you are not interested in a tweaked kernel or server applications and are open to suggestions there is fluxbuntu which is ultra minimal and very fast. Flux is a window manager so its not as heavy and lethargic as a DE like gnome kde or even xfce.
Thank you for the information. My main goal is to have a slim base without "too many" (abstract, I know) choices made for me automatically. And I would like to run the tiling window manager Awesome. Something about tiling window managers are attracting me to them, I simply have to try one. I know they're not for everyone, but I'll force myself to stick with it for a couple of months and we'll see if I'll be using it in the long run later on.

> **snowpine said:**
> Hi Tnek, here is a useful guide to installing minimal ubuntu, then building it up from there: [http://psychocats.net/ubuntu/minimal](http://psychocats.net/ubuntu/minimal)
It assumes you are using IceWM but you could just substitute the windows manager of your choice. 
What you are trying is not that uncommon; so you should get some good advice here.
Thank you for your input. It made me awere of the mini.iso, which I've installed and building my system from. Something like this was exactly what I was looking for. :)


> **mishathegoat said:**
> If you're lookin' to install your own window managers, login managers, file managers, and also exclude the prepackaged software that comes with the Ubuntu Desktop, I'd go with Ubuntu Server. Right now, I'm running Fluxbox, XFE, GDM and I love it! All installed on top of Ubuntu Server 8.04
You haven't noticed anything odd? It's a pity that it's so hard getting to know the differences in kernels and such. Perhaps there are other differences too and not just the kernal configurations. Who knows? The information seems hard to find anyway. :)

Anyway, I'm using the mini.iso now. Who knows how that kernel is configured. I think it's the normal kernel for desktop systems, but I'm not sure. It seems to be working well for me anyway.

---

### Post by tnek on 2008-06-15
Is there anything we should add to the discussion? Getting to know the technical differences between kernals (and more?) of the server and desktop editions seems hard. I've gone with mini.iso now and it feels like the right choice.

I presently do not consider this thread solved. If some more information would occur I'll mark it as solved later on. I would still like to thank everyone who tried to help me, but as the thread isn't solved I'll do it the old fashioned way: Thank you!!

---

