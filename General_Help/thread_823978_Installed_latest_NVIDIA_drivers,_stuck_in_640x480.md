---
title: "Installed latest NVIDIA drivers, stuck in 640x480"
date: 2008-06-09
forum: General Help
---

### Post by McTwist724 on 2008-06-09
After reading through countless threads related to installation and problems with the nvidia driver, I still cannot seem to find a fix to my problem. Sorry if there is another thread that states this. If so, please send a link my way.

Anyway, I installed the latest nvidia driver (173.14.05) and it installed perfectly. The only problem is that I can go no higher than a 640x480 resolution, when my native resolution is 1680x1050. I tried changing the settings with nvidia, to no avail. I checked out my hardware drivers to see if I had them enabled, but it seems as if I have no proprietary drivers installed. I remember there used to be some accelerated graphics driver in there. 

So my question is, how can I get back to my native resolution and install the proprietary drivers?

Ubuntu 8.04
NVIDIA Driver 173.14.05
7800GT card

I've read and read and installed and reinstalled and uninstalled and did all kinds of installs but it seems I always end up in 640x480 or 800x600.

Help much, peace

---

### Post by Pjotr123 on 2008-06-09
Check this:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 2 )

Installing the restricted driver (you want it!):
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)
(number 2 as well)

---

### Post by cocopuffz on 2008-06-09
it might actually be the way your system is detecting your monitor. I was having this problem for the longest time. I managed to get it to work by using the "plug and play" LCD monitor option and ticking on "widescreen" in the little radio button. It added stuff to my xorg.conf file that wasn't being added by the nvidia configuration utility.

---

### Post by McTwist724 on 2008-06-09
Hell yeah! I got it back to the 1680x1050. I downloaded Envy but I don't want to install the old driver, I want the new, 173.14.05 or whatever. The newest driver on envy is 169.12. Anyway I can change that? And if I use envy to install the driver, will it cause a conflict with the driver I installed using nvidia's installer?

---

### Post by qpieus on 2008-06-09
> **McTwist724 said:**
> Hell yeah! I got it back to the 1680x1050. 

how did you fix it?

---

### Post by McTwist724 on 2008-06-09
gksudo displayconfig-gtk

Type that in terminal and select your resolution. As simple as that.

peace

---

### Post by McTwist724 on 2008-06-14
I just reinstalled the new nvidia driver (173.14.05) with Envy. However, I still have no proprietary drivers. It is a good idea to have these right? Any suggestions?

---

### Post by Pjotr123 on 2008-06-14
> **McTwist724 said:**
> I just reinstalled the new nvidia driver (173.14.05) with Envy. However, I still have no proprietary drivers. It is a good idea to have these right? Any suggestions?

No worries: with Envy you *already* have the restricted driver. The latest one. 

So you can safely ignore the message of Ubuntu, that it has a restricted driver for you: that's only the older version, in the repositories of Ubuntu.

---

### Post by dexter on 2008-06-14
> **McTwist724 said:**
> I just reinstalled the new nvidia driver (173.14.05) with Envy. However, I still have no proprietary drivers. It is a good idea to have these right? Any suggestions?

If you installed these drivers manually, not through the packet manager, they will not show up in the list with proprietary drivers. Only proprietary driver installed through the packet manager are shown.

---

### Post by McTwist724 on 2008-06-14
Ohhhhh ok. No worries then.

peace

---

### Post by MyKal on 2010-01-29
i am having the same issue but i am using kubuntu which for obvious reasons that configure-gtk command will not work 

is there an equivalent command for kde systems??

---

