---
title: "Use non-pae kernel"
date: 2012-12-19
forum: General Help
---

### Post by Ralph L on 2012-12-19
In [http://ubuntuforums.org/showthread.php?t=2043665](http://ubuntuforums.org/showthread.php?t=2043665) Post #10 the use of a non-pae kernel is recommended for users of old computers.  It is supposed to use less memory and run faster.  I have an old Compaq Presario 2100 that always has cpu usage of more than 50% (doing nothing) and will be at 100% usage very often, leading to sluggish performance.  I am running Ubuntu 12.04.1 Precise Pangolin.

Does anybody know how to set up for using a non-pae kernel in 12.04.1?  Does anybody know of other things that will make the computer less sluggish?  Note that I am already running Gnome Classic (no effects).

Thanks in advance.

---

### Post by Pjotr123 on 2012-12-19
As far as I know, only Xubuntu 12.04 has a non-PAE kernel by default:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/Xubuntu](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/Xubuntu)

Get it here:
[http://cdimage.ubuntu.com/xubuntu/releases/precise/release/](http://cdimage.ubuntu.com/xubuntu/releases/precise/release/)

A clean reinstall is best:
[https://sites.google.com/site/easylinuxtipsproject/reinstallation](https://sites.google.com/site/easylinuxtipsproject/reinstallation)

Good luck! :)

---

### Post by ajgreeny on 2012-12-19
I think Lubuntu 12.04 also has a non-pae kernel, but that will end when 12.10 is all that is used.  There will from that point on be a big problem for anyone wanting to use one of the ubuntu family of OSs, as it will not be possible to install, then add a non-pae kernel.

I don't know what Bodhi 2 uses; pae or non-pae, but it may be worth a look to find out.

EDIT:  I've just looked and it seems that if you want Bodhi 2.1, you will have to install 2.0.1 and then distro update as Bodhi uses the same kernels as Ubuntu.

See [http://forums.bodhilinux.com/index.php?/topic/6485-how-to-install-bodhi-210-on-non-pae-computer/](http://forums.bodhilinux.com/index.php?/topic/6485-how-to-install-bodhi-210-on-non-pae-computer/) for more info

---

### Post by Ralph L on 2012-12-22
Thanks for the responses--especially about Bodhi.  I didn't know it existed.  It might be a better solution for me than ubuntu, where with each new install I spend a long time getting rid of unity.  

I read up some more on pae and non-pae and according to most sites, pae causes at most a 5% performance hit.  It may not be worth the effort to install it, expecially when it looks like no distros may support it in the future.  I also looked a little at what is taking up my cpu time and it is mostly firefox, which I run 99% of the time.  Maybe I can find an alternative to firefox, although I like a lot of the extensions that firefox provides.  I have about 10 of them installed.

Thanks again,
Ralph

---

### Post by sudodus on 2012-12-22
I think the main problem is because a lot of memory (RAM) is used, not the pae capability, unless your cpu lacks it. Many older cpus have pae, and then you can run i686 versions of [KLX]Ubuntu.

And it is the desktop environment and application programs that need memory. As you wrote, Firefox is hungry. I think you can consider some leaner browser, have both installed and use Firefox, when you need its bells and whistles, otherwise use the leaner one.

I have a system with all four official DEs of Ubuntu:

Vanilla Ubuntu 12.04 with the additions of

lubuntu-desktop
xubuntu-desktop
kubuntu-desktop

I use the ultra-light Lubuntu-desktop most of the time.

---

### Post by Ralph L on 2013-03-10
Found this web site that says it has a 12.04 non-pae Ubuntu:  [http://ubuntuforums.org/showthread.php?t=2116112](http://ubuntuforums.org/showthread.php?t=2116112)

---

### Post by sudodus on 2013-03-10
> **Ralph L said:**
> Found this web site that says it has a 12.04 non-pae Ubuntu:  [http://ubuntuforums.org/showthread.php?t=2116112](http://ubuntuforums.org/showthread.php?t=2116112)

I think you can get a non-pae system according to that link. Try it if you like :-)

But if your computer works with pae, I think it will not improve things. A 64-bit system will use more RAM than a 32-bit system, but we are talking about 32-bit pae and 32-bit non-pae systems.

What will improve things is to use software, that needs less CPU power and RAM. This is why I suggested that you look at

- Lubuntu with the ultra light-weight desktop environment LXDE and light-weight application programs
- Xubuntu with the light-weight desktop environment XFCE and medium weight application programs

or to install the corresponding desktops into your current system.

---

### Post by robert shearer on 2013-03-10
Bodhi has a non-pae version. This works fine on older hardware that doesn't have pae support..(Pentium-M et al)
[http://www.webupd8.org/2013/01/bodhi-linux-220-released-with-stable.html](http://www.webupd8.org/2013/01/bodhi-linux-220-released-with-stable.html)

---

### Post by mörgæs on 2013-03-10
According to [this]("http://www.ehow.com/facts_6812430_specifications-compaq-presario-2100-laptop.html") we are dealing with a Pentium 4 M and not a Pentium M, so it does support PAE. You can run any of the light Buntus, for example Lubuntu.

Best is to forget all the non-PAE advice given in this thread and follow the main path, which is PAE for the future. Going non-PAE will not give you any significant increase in speed.

---

