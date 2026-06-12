---
title: "Ubuntu's vision and me"
date: 2013-01-19
forum: General Help
---

### Post by sunnybubblegum on 2013-01-19
Upon a fresh install of Ubuntu 12.04, my desktop has no sound. I have hunted around for simple solutions on forums, but none of them worked for my computer. It is an HP Pavilion 1730n, from about 2006. The audio card is an onboard HDA Nvidia ALC888.

Yes it's from 2006, but it's still a good computer. I even put a newer Nvidia graphics card in it and I can play the games I like.

In the past I have gotten sound to work with other versions, i.e. 10.10, 11.10.

I've been using Ubuntu for about two years now.

I've noticed Ubuntu, as a company, has been gradually focusing on newer hardware, while leaving a lot of (relatively healthy but older) computer systems to fend for themselves, with lots of forum-searching and work-arounds. With their switch to Unity and its seemingly 3D-only-bound environment, the signs are clear they are aiming for newer hardware.

Here is my question.

Is Ubuntu a good OS for me?
I like many things about it, and I've tried a few other distros.
I would like to keep using my desktop. I think there is nothing wrong with it. It doesn't have a quad-core processor, but for the few games I like to play, for browsing, and for multimedia, it suits my needs.
Will Ubuntu be phasing out users like me, and should I look for a more 'backward-compatible' distro, or is there still hope?

Or, any other suggestions about my sound problem?

---

### Post by sudodus on 2013-01-19
Welcome to the Ubuntu Forums :-)

I think you can still use the good software of Ubuntu, but maybe you should try another flavour, not [vanilla] Ubuntu.

Try version 12.04
- Xubuntu with the light-weight desktop environment XFCE or
- Lubuntu with the ultra light-weight desktop environment LXDE.

Or combine them (installing one of them, and then installing the other desktop environment and have a choice). I run Lubuntu with xubuntu-desktop
```
sudo apt-get install xubuntu-desktop
```
This way I have the very fast LXDE and some extra configuration tools of Xubuntu. For example 'Volume Control for Pulse Audio' ***pavucontrol***

---

### Post by ajgreeny on 2013-01-19
And on my old laptop, an Acer Travelmate 2200, with celeron single core cpu and only 512 MB ram, I also run Lubuntu 12.04. 

I have, however, added many added packages that I need, eg Firefox, Thunderbird, GIMP, Libreoffice, pulseaudio and probably lots of others I've forgotten about, but it gives me the best of both worlds; a fast simple DE but with all the packages I use and can not do without.

Try it; it makes a lot more sense than trying to run unity on a machine it was never meant for.

---

### Post by sunnybubblegum on 2013-01-19
Thank you for your comments.

In fact, I'm glad you mentioned **pavucontrol**, because installing that, in combination with some other factors, got my sound working. (made sure all of my levels in alsamixer were on, restarted my system, and also, plugged my headphone jack into the back of the CPU as opposed to the front)

Why don't they include pavucontrol with the default system if it is so helpful to so many people??

It seems many people benefit from the lighter versions of Ubuntu on ageing systems. While I can get the sound to work on mine for now, I will look into Xubuntu and Lubuntu and see what they have to offer. And I will definitely keep them in mind for the future in case things change/I want to try Ubuntu on a laptop instead.

Do you think Ubuntu will continue to design their desktop support for those users who have ageing/alternative systems?

Thank you both again.

---

### Post by sudodus on 2013-01-19
I'm glad that the sound works now.

> **sunnybubblegum said:**
> 

Why don't they include pavucontrol with the default system if it is so helpful to so many people??

You can't squeeze everything into the space available on a CD (which decides the size of the iso file). So some people have to make a selection ... But we are here to help finding what extra packages/programs may be useful.
> 
Do you think Ubuntu will continue to design their desktop support for those users who have ageing/alternative systems?

Thank you both again.

I think the standard [vanilla] Ubuntu will go on with new and attractive features which will need fairly new hardware. But at the same time Canonical will support the development of the other flavours: Lubuntu, Xubuntu, Kubuntu, Ubuntu Studio, Ubuntu Server etc. I think that Lubuntu and Xubuntu will continue to work well with ageing systems.

---

### Post by sunnybubblegum on 2013-01-19
I really appreciate your support and valuable input. Xubuntu/Lubuntu may be the way to go before long. Out of curiosity, how much longer do you think [vanilla] Ubuntu will generally support desktops of my generation/specifications?

---

### Post by sudodus on 2013-01-19
> **sunnybubblegum said:**
> I really appreciate your support and valuable input. Xubuntu/Lubuntu may be the way to go before long. Out of curiosity, how much longer do you think [vanilla] Ubuntu will generally support desktops of my generation/specifications?
6-7 years old ... well it's a fuzzy region, where it works, but not really well, because the [vanilla] desktop environment eats too much of the horsepower and memory.

But remember that Ubuntu 12.04 has long time support until April 2017. The Xubuntu-specific packages have 'only' 3 years LTS until April 2015, and Lubuntu has no LTS, it is supported until October 2013. On the other hand there is Lubuntu 12.10 and there will be new Lubuntu versions. If you like the old gnome 2 style, and are willing to do some tweaking, there is also *kansasnoob*'s desktop environment according to this link

[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1966370[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1966370")

---

### Post by sunnybubblegum on 2013-01-20
All very good food for thought. Thanks again.

---

### Post by 3rdalbum on 2013-01-20
> **sunnybubblegum said:**
> Why don't they include pavucontrol with the default system if it is so helpful to so many people??


This is the first I've heard of it actually being used to fix audio problems - I suspect maybe the developers don't know about it.

> Do you think Ubuntu will continue to design their desktop support for those users who have ageing/alternative systems?

More recent machines will have priority, but there's certainly nothing to stop you using Ubuntu on your system. Even with Unity! There is a way of turning off animations and transparency in Unity that may help to speed things up if your machine doesn't have much 3D support (read: It has a legacy ATI card, or SiS or VIA). I don't have the link but I did find it on Google, and it helps.

As Ubuntu is looking to run on smaller, less 3D-capable machines such as mobile phones and tablets in the near future, we'll see more optimization of their 3D code which should improve performance, even when your system has no 3D support.

If all else fails, there are still plenty of desktops around that don't require any 3D support at all. KDE, XFCE, LXDE, Mate (although Mate is a bit old and crusty).

---

### Post by ajgreeny on 2013-01-20
Some old machines with non-pae CPU hardware will soon be unusable with the newer versions of all the ubuntu family, as all of them from 12.10 will come with a pae kernel.

I accept that almost all CPUs have been able to support pae going right back to the first pentiums, I think, but nevertheless it could be a problem for some of the really old hardware still in working order.

---

### Post by sunnybubblegum on 2013-01-20
> **3rdalbum said:**
> There is a way of turning off animations and transparency in Unity that may help to speed things up if your machine doesn't have much 3D support.

Is it by using CompizConfig?

> **3rdalbum said:**
> As Ubuntu is looking to run on smaller, less 3D-capable machines such as mobile phones and tablets in the near future, we'll see more optimization of their 3D code which should improve performance, even when your system has no 3D support.

That's very true. And good to remember. Considering Canonical is aiming to get your entire desktop running from your smartphone next, it will have to be lightweight enough in certain respects.

ajgreeny, what are pae and non-pae kernels/hardware?

---

