---
title: "Repository support for 5.10..."
date: 2008-05-14
forum: General Help
---

### Post by ardvark71 on 2008-05-14
Hi....

I have an older system that didn't quite handle Ubuntu and Kubuntu 6.06 as fast as needed so I'm wondering if I install Ubuntu 5.10, do the repositories still support this old of version? If so, what is the trick of getting the additional repositories to come up in Synaptic without all the error messages?

Thanks!

---

### Post by p_quarles on 2008-05-14
The end-of-life for Ubuntu 5.10 has come and gone. The repositories no longer exist, and running it is a security risk. 

If I were you, I'd look into to alternate strategies for reviving this old system. I've installed minimal systems (still fully functional, though) on extremely low-spec computers, and it works fine. Install something like kde-core or gnome-core instead of the standard Ubuntu desktop. Better yet, use a lighter window manager like Openbox or IceWM. You are likely to get better performance this way than using the full Ubuntu 5.10 environment.

---

### Post by FakeOutdoorsman on 2008-05-14
What are the hardware specs on this machine?

---

### Post by ardvark71 on 2008-05-14
Hi...

Thanks for your replies!

System specs are:

Pentium III 600 mhz processor on an AOpen AX6BC motherboard
384 MB's memory
10 GB Western Digital hard drive
Radeon 7200 PCI 3D video card
Netgear FA311 network card
winmodem 

Thanks for letting me know on the repositories...too bad though:(

Best Regards...

---

### Post by p_quarles on 2008-05-14
> **ardvark71 said:**
> Hi...

Thanks for your replies!

System specs are:

Pentium III 600 mhz processor on an AOpen AX6BC motherboard
384 MB's memory
10 GB Western Digital hard drive
Radeon 7200 PCI 3D video card
Netgear FA311 network card
winmodem 

Thanks for letting me know on the repositories...too bad though:(

Best Regards...
You call that "an older system"? ;)

That will run a more recent system just fine if you start off with a command-line installation. The alternate installation disk offers you this option. Once you have the base system installed, install the environment of your choice. For KDE, e.g., you would run this:
```
sudo apt-get install xserver-xorg kde-core kdm
```

---

### Post by ardvark71 on 2008-05-14
> **p_quarles said:**
> You call that "an older system"? ;)


Compared to my HP notebook (Turion 64, 1.8 Ghz, 1 GB memory, Radeon Xpress 200M 128 MB,) absolutely! 

Does the command line installation you mention allow for a more specific kernal for the Pentium III, rather than the 386?

Best Regards...

---

### Post by p_quarles on 2008-05-14
> **ardvark71 said:**
> Compared to my HP notebook (Turion 64, 1.8 Ghz, 1 GB memory Radeon Xpress 200M 128 MB,) absolutely!
Heh, yeah it's definitely not top-of-the-line, but I've installed current versions of Linux on considerably less powerful computers, and still got them functional. 

> Does the command line installation you mention allow for a more specific kernal for the Pentium III, rather than the 386?
Unless you want to compile your own, your choices would be i386 or Generic (what I would recommend). There isn't a significant architecture difference between a PIII and, say, a Core Duo. 

Basically, without the fancy effects and background services that the full desktop packages give you, you'll see good performance with this thing. Again, though, to get the most out of this machine you should look at a window manager.

---

### Post by CREEPING DEATH on 2008-05-14
> **ardvark71 said:**
> System specs are:

Pentium III 600 mhz processor...
384 MB's memory

I've run full Ubuntu 7.10 on a machine with those specs, no problems.  Even installed using the GUI, but the HDD was already partitioned and it was using swap.

CD

---

### Post by ardvark71 on 2008-05-14
> **p_quarles said:**
> Heh, yeah it's definitely not top-of-the-line, but I've installed current versions of Linux on considerably less powerful computers, and still got them functional. 


Unless you want to compile your own, your choices would be i386 or Generic (what I would recommend). There isn't a significant architecture difference between a PIII and, say, a Core Duo. 

Basically, without the fancy effects and background services that the full desktop packages give you, you'll see good performance with this thing. Again, though, to get the most out of this machine you should look at a window manager.

Thank you, p_quarles! When I get a hold of some CD's, I'll burn a copy of the alternative install, and give it a shot :KS

Best Regards...

---

### Post by ardvark71 on 2008-05-14
> **CREEPING DEATH said:**
> I've run full Ubuntu 7.10 on a machine with those specs, no problems.  Even installed using the GUI, but the HDD was already partitioned and it was using swap.

CD

Interesting. Even when I had 5.10 installed on the same system a year ago (when it was still supported,) I could feel the weight of it even though it ran good. :confused:

Best Regards...

---

### Post by mandrill on 2008-05-14
> **ardvark71 said:**
> Interesting. Even when I had 5.10 installed on the same system a year ago (when it was still supported,) I could feel the weight of it even though it ran good. :confused:

Best Regards...
Puppylinux will run like a banshee on that system.....

---

### Post by FakeOutdoorsman on 2008-05-14
> **p_quarles said:**
> You call that "an older system"? ;)

That will run a more recent system just fine if you start off with a command-line installation. The alternate installation disk offers you this option. Once you have the base system installed, install the environment of your choice. For KDE, e.g., you would run this:
```
sudo apt-get install xserver-xorg kde-core kdm
```

I totally agree that a custom install is the way to go.  I do it on all of my Ubuntu installs no matter the hardware.  Yesterday I made a post detailing how to quickly get a base system running Openbox (a Windows Manager) from the alternate disc.  [Re: Good Install But Sluggish]("http://ubuntuforums.org/showpost.php?p=4954853&postcount=13").

> **mandrill said:**
> Puppylinux will run like a banshee on that system.....
Yes, Puppy Linux will run quickly, but it's also superior in it's ugliness.  You custom Ubuntu install will be a better experience in my opinion.

---

