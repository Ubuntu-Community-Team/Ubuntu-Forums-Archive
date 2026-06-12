---
title: "Installing nVidia GeForce 7900"
date: 2007-12-19
forum: General Help
---

### Post by NobleRooster on 2007-12-19
I am trying to install my nVidia 7900 graphics card again so I can use beryl, but I am having trouble getting the driver to install.

I went to the nVidia wevsite and got the download.  I try to run it in the terminal and get this:

"nvidia installer must be run as root."

Can someone help me with this and tell me how to get it installed?

---

### Post by kpkeerthi on 2007-12-19
[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)
Install using the restricted driver manager. This is the suggested way.

If you prefer the latest driver (off repository) try [envy]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by sirdilznik on 2007-12-19
Use the drivers in the repositories.  You will need to enable "Restricted Drivers"  Then look for the package called "nvidia-glx-new".  Install that package through synaptic (or whatever frontend you use).  If you really want to do a manual install I can help with that too, but you're better off going through synaptic

---

### Post by NobleRooster on 2007-12-19
> **kpkeerthi said:**
> [https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)
Install using the restricted driver manager. This is the suggested way.

If you prefer the latest driver (off repository) try [envy]("http://albertomilone.com/nvidia_scripts1.html")

Thanks kpkeerthi, I have never seen that page and it was exactly what I needed.  I got Beryl working nicely, I included a screenshot too/ :D

[[img]http://img258.imageshack.us/img258/1989/screenshotny4.th.png[/img]]("http://img258.imageshack.us/my.php?image=screenshotny4.png")

---

