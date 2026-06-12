---
title: "Difference from Debian"
date: 2007-08-13
forum: General Help
---

### Post by cprofitt on 2007-08-13
Just curious -- what are the key differences between Debian and Ubuntu?

I am debating which one to make my new OS... after deciding I like the apt-get synaptic approach to software packages.

Thanks.

---

### Post by kerry_s on 2007-08-13
they both use apt-get and synaptic.

ubuntu is debian made easier for new comers, alot of stuff is changed.

debian is a standard setup, nothing is modified or changed from the original source.

they both have there qualties. if you have a newer machine try ubuntu, if your machine is older, go debian, as ubuntu cuts out support for older things.

i use a custom install of debian.

net installer> [http://debian.osuosl.org/debian-cdimage/current/i386/iso-cd/debian-40r0-i386-businesscard.iso](http://debian.osuosl.org/debian-cdimage/current/i386/iso-cd/debian-40r0-i386-businesscard.iso)

kde> [http://debian.osuosl.org/debian-cdimage/current/i386/iso-cd/debian-40r0-i386-kde-CD-1.iso](http://debian.osuosl.org/debian-cdimage/current/i386/iso-cd/debian-40r0-i386-kde-CD-1.iso)

xfce4> [http://debian.osuosl.org/debian-cdimage/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso](http://debian.osuosl.org/debian-cdimage/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso)

ubuntu> [http://ubuntu.cs.wisc.edu/pub/mirrors/linux/ubuntu/releases/feisty/](http://ubuntu.cs.wisc.edu/pub/mirrors/linux/ubuntu/releases/feisty/)

kubuntu> [http://ubuntu.cs.wisc.edu/pub/mirrors/linux/ubuntu/releases/kubuntu/feisty/](http://ubuntu.cs.wisc.edu/pub/mirrors/linux/ubuntu/releases/kubuntu/feisty/)

xubuntu> [http://mirror.anl.gov/pub/ubuntu-iso/DVDs/xubuntu/7.04/release/](http://mirror.anl.gov/pub/ubuntu-iso/DVDs/xubuntu/7.04/release/)

---

### Post by cprofitt on 2007-08-14
What do you install with Debian? When you say custom install?

---

### Post by lunarcloud on 2007-08-14
Install Debian, and you'll spend a few more hours tweaking than you will with Ubuntu. I find that I dont have such a large sources.list file (aka i dont have to add so many 3rd party repositories) with Ubuntu. 

For a project or old bumming compy, I've used Debian. For a desktop I use everyday, (k)Ubuntu.

---

### Post by kerry_s on 2007-08-14
> **indigo196 said:**
> What do you install with Debian? When you say custom install?

I only install the base & then i build up from there.
example:
i do the base install
i log in as root(no gui yet)
apt-get install xorg gdm synaptic (what ever wm i feel like)
reboot(ctrl+alt+delete)
select the wm i installed & login(gui)
open synaptic and continue installing what i want.

a custom install, i pick my own applications that i want to use.
i started my current setup with> 
apt-get install xorg gdm synaptic jwm mc
depending what the need is, you can do without those things. for instance if i want to go really small> 
apt-get install xorg jwm mc
is enough for a working gui setup, i would just use startx to get to the gui & i would use aptitude in terminal to install/remove applications.

---

### Post by kerry_s on 2007-08-14
> **zarquad said:**
> Install Debian, and you'll spend a few more hours tweaking than you will with Ubuntu. I find that I dont have such a large sources.list file (aka i dont have to add so many 3rd party repositories) with Ubuntu. 

For a project or old bumming compy, I've used Debian. For a desktop I use everyday, (k)Ubuntu.

then you have no idea what your doing, ubuntu has the same type of repo as debian, they just have them listed already, but in debian you add the other repos, which is as simple as adding> contrib non-free < to the end. and if you really want to extend it you can add lenny,sid,multimedia,etc...
there are more repos available for debian then there are for ubuntu.
also with debian you only need to install once and it can always dist-upgrade to the latest depending on how new you want.

---

### Post by cprofitt on 2007-08-16
> **kerry_s said:**
> then you have no idea what your doing, ubuntu has the same type of repo as debian, they just have them listed already, but in debian you add the other repos, which is as simple as adding> contrib non-free < to the end. and if you really want to extend it you can add lenny,sid,multimedia,etc...
there are more repos available for debian then there are for ubuntu.
also with debian you only need to install once and it can always dist-upgrade to the latest depending on how new you want.

Thanks... that bakes it that I should use Debian.

Now... how to get Debian to install on my DP965LT MB will be the trick... it currently wants to claim that I don't have a CD after it just finished booting from it. Obviously some lack of support for the controller or some such... google time.

---

### Post by kerry_s on 2007-08-16
> **indigo196 said:**
> Thanks... that bakes it that I should use Debian.

Now... how to get Debian to install on my DP965LT MB will be the trick... it currently wants to claim that I don't have a CD after it just finished booting from it. Obviously some lack of support for the controller or some such... google time.

well i looked at the spec's, nothing jumps out at me other than it's new, bad choice for linux, linux always needs time to work the new stuff in.

[http://www.intel.com/products/motherboard/DP965LT/index.htm](http://www.intel.com/products/motherboard/DP965LT/index.htm)

---

### Post by cprofitt on 2007-08-16
> **kerry_s said:**
> well i looked at the spec's, nothing jumps out at me other than it's new, bad choice for linux, linux always needs time to work the new stuff in.

[http://www.intel.com/products/motherboard/DP965LT/index.htm](http://www.intel.com/products/motherboard/DP965LT/index.htm)


ah... new? Its over a year old... I think the initial release of the chipset was back in June of 2006

---

