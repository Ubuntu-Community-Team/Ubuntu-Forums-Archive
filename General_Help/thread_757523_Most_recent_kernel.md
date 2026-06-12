---
title: "Most recent kernel?"
date: 2008-04-17
forum: General Help
---

### Post by Th3Professor on 2008-04-17
My uname -a shows that I'm on linux kernel 2.6.22-14 (-generic).

According to [http://www.kernel.org/](http://www.kernel.org/) the current stable kernel, as of today, is:
2.6.25

Was there a release after ".22-14" and before ".25"?

If there was, would my Ubuntu "auto-updates" feature automatically update the kernel?

Should I go ahead and figure out how to manually change to the ".25" or let Ubuntu automatically do it for me (if it will, that is)?

EDIT:
Does anybody use Morton's "-mm" patch with Ubuntu? (Why? (Curious to know if it'll make a positive difference.))

(I am on Ubuntu Studio, though I only use the real-time kernel when using the hefty multimedia apps, otherwise I use "-generic" for generic uses.)

---

### Post by ryanhaigh on 2008-04-17
There would indeed have been a .23 and .24 version, in fact the next version of ubuntu due out later this month will be using a ,24 version. Ubuntu doesn't have the VERY latest kernel and generally wont upgrade the kernel after a major release except for security fixes. The reason is that testing needs to be done to determine the stability and function of the kernel(and the rest of the os) which is why we have had alpha, beta and rc releases of hardy recently.

Debian (from which ubuntu is derived) uses very old releases in their stable branch as these have been tested comprehensively, ubuntu is a little more bleeding edge but not as much as some other distros might be.

Generally there is little NEED to upgrade to the latest kernel unless you are using hardware only recently supported (there are probably other reasons too) but that doesn't mean you can't just WANT to...many people I know do this.

---

### Post by kutjara on 2008-04-17
> **Th3Professor said:**
> My uname -a shows that I'm on linux kernel 2.6.22-14 (-generic).

According to [http://www.kernel.org/](http://www.kernel.org/) the current stable kernel, as of today, is:
2.6.25

Was there a release after ".22-14" and before ".25"?

If there was, would my Ubuntu "auto-updates" feature automatically update the kernel?

Should I go ahead and figure out how to manually change to the ".25" or let Ubuntu automatically do it for me (if it will, that is)?

EDIT:
Does anybody use Morton's "-mm" patch with Ubuntu? (Why? (Curious to know if it'll make a positive difference.))

(I am on Ubuntu Studio, though I only use the real-time kernel when using the hefty multimedia apps, otherwise I use "-generic" for generic uses.)

Hardy Heron (8.04) will launch with the 2.6.24-16 kernel, which is the latest version currently used in the beta distribution (barring any unforseen need to move to a -17 or later revision).

While 2.6.25 has indeed been released, it will not be used in Hardy and, in any case, seems mostly aimed at resolving problems with hardware running more than 4GB of RAM. Upgrading to Hardy will not give you the absolute latest kernel, but it will give you a very recent one that has the virtue of being extensively tested with the rest of the OS.

---

### Post by ibuclaw on 2008-04-17
Also to note, as you said in the first post. The Linux 2.6.25 kernel has been released today.
Ubuntu isn't a fresh-off cvs rolling release distribution.

The Ubuntu Team makes stability a priority before version number.
If you take another look at kernel.org. You will also notice that the last official kernel release for the previous kernel is 2.6.24-4...
Hardy is 2.6.24-16.

A full 12 incrementations to the original that are proof of the Ubuntu Kernel team adding in more support and improving the stability of the kernel before officially releasing it to the world.
So considering the work they've done (and it is a bloody good piece of work, trust me). I doubt they'd change to the 2.6.25 kernel anytime soon.

Not to forget the fact that kernel freeze was done 3 months ago. So they wouldn't switch in time for Hardy regardless!

Expect the switch sometime in the middle between 8.04 and 8.10, but don't get your hopes high to see it anytime soon.

Regards
Iain

---

### Post by Th3Professor on 2008-04-17
Thanks for the feedback. :)

My Ubuntu Studio "real-time" kernel (though I only use it in special cases) doesn't seem to be as solid as the "-generic". Any ideas on improvements in future "-rt" kernels, at least for the Ubuntu Studio release?

I don't really feel the need to use the real-time kernel unless using a specific application or group of applications (in the "Studio" meta-package) that otherwise require it.

---

### Post by ibuclaw on 2008-04-17
I think that its just the plain fact that Ubuntu is not tweaked for utilising the realtime kernel.

Personally, I use [64Studio]("http://www.64studio.com/") for all my Recording/Artwork needs. The quality of it is enough to make Ubuntu-Studio wet itself.

The only troubles are that the realtime kernel is a hit and miss when it comes to first booting into it.
You usually have to install it twice. Though this is one of the only annoyances. (You also need a good graphics card and a decent soundcard due to incompatibilities)

It is based on Debian Etch, with a few packages from testing, so it isn't quite as flash as Ubuntu either.

Regards
Iain

---

### Post by Th3Professor on 2008-04-17
Thank you for mentioning 64 Studio. I will *definitely* look into that one. Any systems that are set-up for those purposes interest me.

---

