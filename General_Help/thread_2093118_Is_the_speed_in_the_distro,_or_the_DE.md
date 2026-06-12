---
title: "Is the speed in the distro, or the DE?"
date: 2012-12-09
forum: General Help
---

### Post by cbennett926 on 2012-12-09
I recently did a review of a few distro's and I actually have a question after doing so. I noticed that Linux Mint runs substantially faster than Ubuntu, even though Mint is a fork of Ubuntu. Now, is the speed difference because on Mint it was running Cinnamon, and Ubuntu was running Unity?

---

### Post by Bucky Ball on 2012-12-10
[I]Thread moved to **General Help**

Reason:[/I] **The Community Cafe** is _*not*_ a support sub-forum. From its description:

>  The Community Chat area is for lighthearted and enjoyable discussions, like you might find around a water cooler at work.Think of it like this: 

First you have the Ubuntu base system; no apps as we know it, just the bare essentials (like you would get with a minimal install before you install anything you want manually). 

Second: Each flavour drags with it its default applications and other things. This can be a lot or not much.

Third: Each flavour also drags in whatever desktop environment it uses. This can be resource hungry or not.

Apply to other distros as well. You have a base Arch, you drag in the apps and desktop environment. It is the sum of all this which equals resource use. 

For instance, you might have Kubuntu installed, which means the Ubuntu base, the Kubuntu default apps and KDE. Bulky. Now you install xfce4 or lxde and use that instead of KDE, not so bulky, but you still are using the Kubuntu default apps. A hybrid. The choices are seemingly endless ...

Minimal install, no default apps but base only, you add only the apps you require and a lightweight DE; stand back and let it fly@! Install kubuntu-desktop and watch it lose altitude ...

Hope that helps. ;)

---

### Post by cbennett926 on 2012-12-10
> **Bucky Ball said:**
> [I]Thread moved to **General Help**

Reason:[/I] **The Community Cafe** is _*not*_ a support sub-forum. From its description:


Whoops!! I thought this was posted to the Cafe in the first place!

---

### Post by Bucky Ball on 2012-12-10
> **cbennett926 said:**
> Whoops!! I thought this was posted to the Cafe in the first place!

It was. It doesn't belong there as this is a support question so it has been moved to here. ;)

---

### Post by cbennett926 on 2012-12-10
Oh, yay! 

So I've been digging up some research, I ran Linux Mint 14 and was in awe at the speed, I found out it was cinnamon giving the speed and I am now in the process of installing Cinnamon on there.

---

### Post by vasa1 on 2012-12-10
> **cbennett926 said:**
> Oh, yay! 

So I've been digging up some research, I ran Linux Mint 14 and was in awe at the speed, I found out it was cinnamon giving the speed and I am now in the process of installing Cinnamon on there.
Sam Hewitt is also impressed by the speed: [http://www.omgubuntu.co.uk/2012/11/linux-mint-14-with-cinnamon-desktop-review](http://www.omgubuntu.co.uk/2012/11/linux-mint-14-with-cinnamon-desktop-review)

---

### Post by kansasnoob on 2012-12-10
> **cbennett926 said:**
> I recently did a review of a few distro's and I actually have a question after doing so. I noticed that Linux Mint runs substantially faster than Ubuntu, even though Mint is a fork of Ubuntu. Now, is the speed difference because on Mint it was running Cinnamon, and Ubuntu was running Unity?

My best guess is that the speed (or lack thereof) is the result of the window manager in use.

Beginning with 12.10 Ubuntu stopped using Metacity altogether in favor of using "Compiz + llvmpipe", although 'metacity' is still available in the repos and can currently be used with the Gnome "fallback session" which [I wrote about here for 12.04]("http://ubuntuforums.org/showthread.php?t=1966370").

OTOH Mint uses it's own fork of Gnome's new Mutter window manager renamed Muffin for it's Cinammon DE which is lighter on resources than Compiz, but heavier than Metacity which Gnome will stop supporting altogether in version 3.8.

While I was talking about the Gnome 3 classic session here I do explain a bit more about window managers:

[http://ubuntuforums.org/showthread.php?t=2090021](http://ubuntuforums.org/showthread.php?t=2090021)

---

