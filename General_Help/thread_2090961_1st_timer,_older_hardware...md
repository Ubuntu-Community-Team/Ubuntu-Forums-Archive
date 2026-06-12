---
title: "1st timer, older hardware.."
date: 2012-12-04
forum: General Help
---

### Post by exit151 on 2012-12-04
Hey all.  I'm a first-timer here, but a long time user of linux in general.  (Been a Fedora user since Core4).  My house has a number of rigs in it, a mix of mostly Windows PC's but I have two servers running Fedora, and a fedora laptop as well.  

Today's post is about, well we'll call it server #1.  Server 1 runs a version of Fedora known to have an issue (Core 11), and recently I found myself on the receiving end of it.  I've always liked 'that' flavor, but the problem I face is that it's getting too new for the hardware I run.  I tried installing a 'slightly' newer release than what I ran, but it's giving me all sorts of grief trying to get it installed for some reason (been going through it on their forums) and frankly, just getting tired of it.

I've known about this project for quite some time, and it has a reputation for being a good, solid OS.  Trouble is, I don't know if it'll run, and even if so, what the latest/best version to put on the machine..

The machine?  It's a Tyan Thunder i7501 dual Xeon 2.4 (I think, maybe 2.8) rig with 2GB RAM.  It's by todays standards old, but still manages to do everything I need it to.  One of the downfalls (least on fedora) is it's antiquated ATI Rage XL onboard video.  I'm a GUI kind of person who terminals when necessary.  It doesn't need to be flashy (in fact, with the limited video it CAN'T be too flashy, rofl), just needs to work.  I googled my server and ubuntu and only one search result came up, someone with an unspecified version who, at the installer prompt just saw the machine rebooting over and over.  

What, if any release/version could/should I try, if any?  

As for what the server will do (if that matters much), well..  mostly it's used for offline testing of my websites.  Once in awhile a server application will come along, I fold@home when it's idle, which admittedly.. Is most of the time, lol.  Just need something stable that will run well.

---

### Post by chadk5utc on 2012-12-04
I personally have had great luck with Ubuntu or any Debian based distro on older hardware, and there are a number of other Window managers that have a smaller install footprint than Gnome or KDE. The machine you describe should run fine I would think. Ubuntu also has a minimal install option though no GUI I think comes in around 150megs or so and try some of the other window managers? Seems their are also a few mini distros around like DSL(DamnSmall) linux around 50-100megs best I can remember, that have GUI and are fairly easy. On another note video cards are cheap too if you have an open pci slot or usb for that matter???

---

### Post by Kirk Schnable on 2012-12-04
Xubuntu (XFCE desktop interface) and Lubuntu (LXDE desktop interface) are both designed to be very lightweight distributions.

---

### Post by snowpine on 2012-12-04
If you are generally pleased with Fedora 11 then I think you would love CentOS. It's basically Fedora 12 but with very long-term support.

---

### Post by SlugSlug on 2012-12-04
I am a new fan of [http://cinnamon.linuxmint.com](http://cinnamon.linuxmint.com)  sine I can't stand the unity DE

---

### Post by 2F4U on 2012-12-04
My guess would be that, considering your graphics card, going for Ubuntu with Unity might not be a good idea. Since this machine is intended to be used as a server, my suggestion would be to install Ubuntu's server version, to be precise, Ubuntu 12.04 LTS server.

[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

It comes with 5 years of support and seems to support Xeon processors. The initial install comes without any GUI, but you can install any GUI that is available in the repositories.
If you want to stay in the RedHat world, CentOS or ScientificLinux would be good choices. They come with even longer support.

---

### Post by SeijiSensei on 2012-12-04
> **snowpine said:**
> If you are generally pleased with Fedora 11 then I think you would love CentOS. It's basically Fedora 12 but with very long-term support.

+1 for CentOS

If you're using to mucking around on machines running RedHat-flavored distros and using yum/rpm for packages, you'll probably find CentOS an easier transition than Ubuntu.

---

### Post by exit151 on 2012-12-04
Thanks for all the comments, really appreciate it!
lightweight isn't really a factor, just the low/ancient video card.  I liked the look of Unity (actually reading up on the unity for fedora project for one of my newer rigs) and cinnamon/mint as well, though it would have the same issue as Unity on this given box.  That said, it's really exciting to see some freshness and really awe-inspiring GUI's come into the linux world.

In regard to the statement about sticking in the RedHat world.  That's a very fair point - And I wasn't aware CentOS had the stability that Fedora doesn't.  That said, part of the fun (and frustration, right?!) is learning new things.  I'm not saying I'm departing Fedora by any means, there are still rigs running it, I just think maybe it's time to try something different.  I think I'll go with the Ubuntu server 12.04 LTS for this box.

Again, thanks for all the posts and comments, it was very helpful!

151

---

