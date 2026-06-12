---
title: "Installing Latest nVidia Drivers"
date: 2008-01-15
forum: General Help
---

### Post by waspinator on 2008-01-15
Hi,

I'm trying to install the latest nVidia drivers but the nVidia "installer"( if you can call it that) is giving me problems. It wants me to install them without running X, and since I'm pretty new to linux I'm not even sure how to do that, and would prefer not to.

Right now if I type ```
cat /proc/driver/nvidia/version
``` in terminal I get ```
NVIDIA UNIX x86 Kernel Module  100.14.19
```

I checked nVidia's website and they have a newer driver available (a lot newer it looks like)

Version: 169.07
Operating System: Linux x86
Release Date: December 20, 2007

I've got 3 questions.

1. Why doesn't ubuntu update these drivers automatically in "update manger" OR
2. Why isn't there an easy installer for drivers (.deb package) on nVidia's site (they have rpm and yum ... I thought ubuntu was more popular then fedora)
3. How do I install these drivers as easily as possible, and without using things like ENVY or Automatix

I'm new to linux, so maybe I didn't choose the right distro for beginners. Should I be using fedora instead?

Hopefully this can somehow be done,

Thanks

---

### Post by santaslittlehelper on 2008-01-15
> 1. Why doesn't ubuntu update these drivers automatically in "update manger" OR
I think that got something to do with Ubuntu's release police or what not, not risking breakage, but that's really a guess, someone will know better. In some ways Ubuntu don't seem very bleeding edge.
> 2. Why isn't there an easy installer for drivers (.deb package) on nVidia's site (they have rpm and yum ... I thought ubuntu was more popular then fedora)
I think that might be something to ask nvidia about, proprietary and all that jazz.
> 3. How do I install these drivers as easily as possible, and without using things like ENVY or Automatix
It's not really easy on Ubuntu at least I don't think so, you have to go though some hops to avoid conflicts. 
However if you can do with the drivers that ships with Ubuntu it's quit easy.
> I'm new to Linux, so maybe I didn't choose the right distro for beginners. Should I be using fedora instead?
There's lots of distributions out there so it's hard to say, if you ask me, my advice would be give fedora a try and see what you think.

If you don't need the newest drivers (e.g. the current drivers don't support you're card) then there might not be to much point in going through the mess.
I believe 169.07 are the current beta's and got a funny bug that makes the GPU fan spin to a max. So If you decide to install I would go with 169.04 for now.

This is not to tell you what to do, it's you're computer and I am using 169.04 myself because I feel like it.
If you what to you can have a look here - [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

### Post by cdenley on 2008-01-15
New drivers don't usually get added to an already released version. The new version will be in [hardy]("http://packages.ubuntu.com/hardy/misc/nvidia-glx-new"). Just because nvidia released it doesn't mean it will work properly on ubuntu.

---

### Post by oldos2er on 2008-01-15
Reboot into recovery mode, then you can run the .run file with "sh ./NVIDIA-Linux-xxxxx.run" .

---

### Post by waspinator on 2008-01-17
Thanks for all your help.

For now I think I'll stick with the provided drivers. I'm too scared to mess something up.

I hope that in the near future, hardware companies and Ubuntu (and Linux in general) will work closer together to provide easier ways to install drivers.

I took a look at fedora, but I feel that Ubuntu has a bigger and better future right now. I'm moving all my family's computers (10 in total) from Windows XP/Vista to Ubuntu. Sticking with one distro will decrease my technical support issues.

Thanks, and wish me luck with my transition.

---

### Post by bodhi.zazen on 2008-01-17
Well, installing the Nvidia driver is not hard at all.

You can :

1. Use the Ubuntu drivers. These are nvidia-glx and nvidia-glx-new. These drivers will update automatically as you are asking.

Why do you need the newest, latest, greatest from Nvidia ?

2. Manually install it. This requires you drop out of X.

from there you :

```
sudo sh /path/to/NVIDIA*.run
sudo /etc/intit.d/gdm start
```

Three commands (including the one to drop out of X). No big deal, not really complex, IMO. Why are you so adverse to using the command line?

3. Use Envy. Envy allows you to do this in X, although you need to restart to use the new driver. Envy is the way to go if you do not want to drop out of X.

4. Use Automatix. I would warn you though that Automatix is not supported here and *may* cause breakage. On the other hand, so can the newest latest Nvidia driver :rolleyes:

5. No need to dis Fedora. It may not be for you, and that is fine, but Feodra is a fine distro and has some advantages. With my hardware (Nvidia card), the Fedora Nvidia driver works with dual monitors out of the box (not true with Ubutnu where I need to install the Nvidia driver).

---

