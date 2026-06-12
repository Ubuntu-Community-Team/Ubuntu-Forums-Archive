---
title: "Is Xubuntu faster?"
date: 2008-01-18
forum: General Help
---

### Post by ByKeLaO on 2008-01-18
1. My PC isn't exactly low-spec, and In general use, Ubuntu runs fine on my PC, certainly much better than Vista anyway. But it takes AGES to boot up and even longer to log in. Will Xubuntu boot/log in any faster than Ubuntu?
2. And will an upgrade to Hardy Heron speed boot/login times for Ubuntu?

Thanks!

---

### Post by jken146 on 2008-01-18
XFCE is lighter than GNOME, so you will probably notice a difference.  You can always just install XFCE in your current setup to try it out (you choose between desktop environments at the login screen).

I've no idea if Hardy will be lighter on resources than Gutsy, but it would be safest to wait until April when Hardy is released.

---

### Post by aysiu on 2008-01-18
Xubuntu will take the same time to boot up. The bootup process has nothing to do with what desktop environment you run, as far as I know.

---

### Post by Shin_Gouki2501 on 2008-01-18
and if ur still wanna go faster try fluxubuntu ;)

---

### Post by PeterJS on 2008-01-18
> **robinjam said:**
> 1. My PC isn't exactly low-spec, and In general use, Ubuntu runs fine on my PC, certainly much better than Vista anyway. But it takes AGES to boot up and even longer to log in. Will Xubuntu boot/log in any faster than Ubuntu?

The boot up times should be more or less the same across all three flavors. As for the login times Xubuntu is generally faster, but this is largely a function of there just being less of it to load. Try it, find out, worst case is it doesn't help any and you can uninstall it.
> 
2. And will an upgrade to Hardy Heron speed boot/login times for Ubuntu?

Right now? probably not, upgrading to Hardy this early will likely break more things than it fixes, it is still very alpha. By late march the beta's should be reasonably usable, but at that point why not ride it out those last few weeks to the official release. I personally like to upgrade 1 or 2 days before the official release :-\". Usually by then everything that is going to get fixed is, and traffic to the mirrors is low because the release isn't official yet.

---

### Post by ByKeLaO on 2008-01-18
Whoa, inundated with replies within 8 minutes! lol

Well, GNOME runs really blazing fast on this PC, so if the desktop environment has no effect on boot time, I think I'll stick with it.

That said, I think I'm still gonna try out xubuntu in VMWare, just to see if I like it.

Thanks peoples!

---

### Post by aysiu on 2008-01-18
One thing you could try is going to System > Administration > Services and turning off boot-time services you don't need.

---

### Post by ByKeLaO on 2008-01-18
> **PeterJS said:**
> The boot up times should be more or less the same across all three flavors. As for the login times Xubuntu is generally faster, but this is largely a function of there just being less of it to load. Try it, find out, worst case is it doesn't help any and you can uninstall it.

Right now? probably not, upgrading to Hardy this early will likely break more things than it fixes, it is still very alpha. By late march the beta's should be reasonably usable, but at that point why not ride it out those last few weeks to the official release. I personally like to upgrade 1 or 2 days before the official release :-\". Usually by then everything that is going to get fixed is, and traffic to the mirrors is low because the release isn't official yet.


I wasn't planning on installing Hardy on my current install. I was gonna start from scratch in a new partition ;)

> I personally like to upgrade 1 or 2 days before the official release :-\"
Say, that's a good idea. Now you've gone and told everyone, they're all going to do the same :P

---

### Post by ByKeLaO on 2008-01-18
> **aysiu said:**
> One thing you could try is going to System > Administration > Services and turning off boot-time services you don't need.

That's a good idea.
Is it possible to get a boot log that shows me what's taking my PC so long to boot up? That'd be really useful. Then I could use that to disable services I don't need (if there are any).

---

### Post by p_quarles on 2008-01-18
> **robinjam said:**
> That's a good idea.
Is it possible to get a boot log that shows me what's taking my PC so long to boot up? That'd be really useful. Then I could use that to disable services I don't need (if there are any).
Yes. Look for "bootchart" in your package manager. If it's installed, it will automatically make a graphical chart when you boot up. You can find the charts in /var/log/bootchart.

---

### Post by ByKeLaO on 2008-01-18
> **p_quarles said:**
> Yes. Look for "bootchart" in your package manager. If it's installed, it will automatically make a graphical chart when you boot up. You can find the charts in /var/log/bootchart.

Fantastic! Installing now.

I have just noticed something about GNOME that does really annoy me. The main menu takes about 5 seconds to open. Not long I know, but it's a lot longer than in xfce :)

---

### Post by ByKeLaO on 2008-01-18
OK, after rebooting, I can see a 2 services that take a long time to complete (10 seconds):

kthreadd
khelper

What are they?

---

### Post by Comhra on 2008-01-18
Wow!  Ubuntu is just amazing, so flexible, I love it.  I switched in September and Ubuntu just keeps on surprising me.  I never realised that I can run multiple desktop environments until I read this thread.  Got Xfce up and running and it's mega fast.  Found most everything except the dictionary.  Where is it Guys?

---

### Post by p_quarles on 2008-01-18
> **robinjam said:**
> OK, after rebooting, I can see a 2 services that take a long time to complete (10 seconds):

kthreadd
khelper

What are they?
A couple really good guides to speeding up boot time:
[http://darkox-weblog.blogspot.com/2007/10/improve-ubuntu-boot-time-and.html](http://darkox-weblog.blogspot.com/2007/10/improve-ubuntu-boot-time-and.html)
[http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651)

---

### Post by gn2 on 2008-01-18
If booting 7.10 is really slow, this may help: [http://ubuntuforums.org/showthread.php?t=580903](http://ubuntuforums.org/showthread.php?t=580903)

---

### Post by Shin_Gouki2501 on 2008-01-19
hey whats ur boot chart showing?

---

