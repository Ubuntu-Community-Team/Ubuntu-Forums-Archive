---
title: "Absolute minimally install software distro?"
date: 2012-11-07
forum: General Help
---

### Post by 4DTiger on 2012-11-07
Hello!

Whether this is the right place for posting, i don't know but:

I'm looking for a distro that has the complete minimum installed on it?

I want to be able to install the programs I want and not spend an hour uninstalling tons of software that is useless and not necessary.


Apologies again if this is the wrong place to post!

Cheers!

---

### Post by Lars Noodén on 2012-11-07
How minimal?  You could try Debian or use the netboot cd image for Ubuntu.  Both of those can be small.

---

### Post by 4DTiger on 2012-11-07
barely any programs on it, kinda list a blank slate. I figure the minimal the software, the faster it runs, therefor run programs like minecraft and screen capture.

I want to start my own series, that's why!

---

### Post by 2F4U on 2012-11-07
Try Archlinux. The base install is just that, a kernel and some software to allow you to boot. Everything else is up to you whether you install it or not.

---

### Post by rubylaser on 2012-11-07
> **2F4U said:**
> Try Archlinux. The base install is just that, a kernel and some software to allow you to boot. Everything else is up to you whether you install it or not.

+1 for Arch, but there will be a learning curve with it.  Otherwise, just use the netinstall image as Lars suggested.  It will be perfectly fine for running a Minecraft server.

---

### Post by cwsnyder on 2012-11-07
It depends on what package manager you wish to use to install your Minecraft and supporting packages.  Ubuntu minimal install literally doesn't install any applications which you don't ask for except the Linux GNU core terminal apps.  Think apt-get without the GUI.  If you want a GUI, you are also going to have to install all of the dependencies for the GUI, or it will break.  They might also not have the dependencies needed to get your screen capture working.

You are heading for what is called 'dependency hell.'  Unless you are comfortable working on command-line Linux, I would recommend Arch (as already suggested), Slackware, or Gentoo Linux for at least 6 months before attempting this project.

If you don't want to spend 8-12 months on the project, just download your favorite flavor of Ubuntu and remove the top-level applications to minimize the impact on Minecraft and go from there.

---

### Post by mastablasta on 2012-11-07
ubutnu minimal should be just fine. here is anice how to: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by raja.genupula on 2012-11-07
> **mastablasta said:**
> ubutnu minimal should be just fine. here is anice how to: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)


+1 to Ubuntu Minimal

---

### Post by wheeze on 2012-11-07
> **raja.genupula said:**
> +1 to Ubuntu Minimal

+2

It's the only way to fly!

---

### Post by snowpine on 2012-11-07
Most distros (including Ubuntu) have this capability.

However I think you may be operating under a flawed assumption that the number of applications installed determines how fast Minecraft will run. All it affects is how much hard disk space is used (which is cheap these days), unless the applications are actually loaded into RAM (which is also cheap these days) or currently in use by you (in which case, yes, having multiple apps currently in use means they must compete for CPU cycles which would certainly affect the performance of other apps like Minecraft).

---

