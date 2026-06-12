---
title: "Nvidia Optimus GPU"
date: 2014-12-25
forum: General Help
---

### Post by RocketPenguin on 2014-12-25
It has been quite a long time since i have used Ubuntu, and even longer since i have posted here. With that said, i am a tad bit rusty, and may have forgotten a thing or two, so please do bear with me. 

I have just freshly installed Ubuntu 14.10 on my SSD alongside Windows 7. My Laptop is an Asus N61J, with an Nvidia GT325M CUDA GPU with Optimus Technology, along with an Intel HD GPU. What i would need help with, is selecting which driver to install for the Nvidia. I did a little bit of research, and i read something about Nvidia drivers not supporting dual GPU? And something about BumbleBee (Don't know if that partains to me)? In the Additional Drivers list, i am given multiple options for what driver i want. Do I want any of those? Do I need a third party driver? How do I use both of my GPUs on Ubuntu? In windows, i can select what program uses which GPU. How would this be done in Ubuntu?
If any more info is needed, just ask.
Thanks for your time!

---

### Post by Bashing-om on 2014-12-25
linux junkie; Hello,

I often see nvidia-prime recommended.
Check out:
```

apt-cache show nvidia-prime

```

Let us know how it goes.

[INDENT][INDENT][INDENT]maybe yes
[/INDENT][/INDENT][/INDENT]

---

### Post by RocketPenguin on 2014-12-25
> **Bashing-om said:**
> linux junkie; Hello,

I often see nvidia-prime recommended.
Check out:
```

apt-cache show nvidia-prime

```

Let us know how it goes.
[INDENT][INDENT][INDENT]maybe yes
[/INDENT]
[/INDENT]
[/INDENT]


All that command did was give me an output ;_; 

> Package: nvidia-prime
Priority: optional
Section: admin
Installed-Size: 102
Maintainer: Alberto Milone <alberto.milone@canonical.com>
Architecture: amd64
Version: 0.6.7
Replaces: hybrid-graphics
Provides: hybrid-graphics
Depends: lightdm (>= 1.9.1) | gdm | kdm | sddm, upstart, bbswitch-dkms, pciutils, lsb-release, lsb-base (>= 4.1+Debian11ubuntu7)
Conflicts: hybrid-graphics
Breaks: ubuntu-drivers-common (<< 1:0.2.89)
Filename: pool/main/n/nvidia-prime/nvidia-prime_0.6.7_amd64.deb
Size: 11450
MD5sum: 62bfb1c43e6de71795f0b184dca093ec
SHA1: 5b84dc5e3da10518a35b743b5bb0355b1c01ad08
SHA256: 7ed232f9b0d924b82a02ea1a4e107d07c0a8cdb11e715ce16c14fd60f545be0a
Description-en: Tools to enable NVIDIA's Prime
 This is a set of tools which will enable
 NVIDIA's Prime on MUXless systems.
Description-md5: 398e4a566cef42e9b12f88c78ffad0c2
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Supported: 9m

---

### Post by RocketPenguin on 2014-12-25
Well did a bit of reading, and found the differences between Prime and BumbleBee... BumbleBee suits me better, as i can choose which app gets what, without having to log in and out. Prime looks great too, when i am on batter, log in on Intel, and visa versa. However, my Intel GPU is decent enough, and so i only use the Nvidia for certain tasks. With that said, i installed BumbleBee, and it works fine so far. Thanks for your help!

---

### Post by Bashing-om on 2014-12-25
linux junkie; Great.

Glad ya got it sorted out.

If this little matter is now concluded;

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

That be the beauty of open source
[INDENT][INDENT][INDENT][INDENT]choice
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2014-12-25
For those interested in this subject there is also this

[http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html](http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html)

Regards.

---

### Post by RocketPenguin on 2014-12-25
> **grahammechanical said:**
> For those interested in this subject there is also this

[http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html](http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html)

Regards.
Ooh hay, i might just get prime then... BumbleBee is weird, and i don't really like it :-?

---

### Post by Bashing-om on 2014-12-25
linux junkie; Yeah;

Seems that Nvidia-prime works better in 14.04.
Remember, one had to purge BumbleBee prior to installing Nvidia-prime .

Conflicts, conflicts
[INDENT][INDENT][INDENT]all these conflicts - 
[/INDENT][/INDENT][/INDENT]

---

### Post by RocketPenguin on 2014-12-25
> **Bashing-om said:**
> linux junkie; Yeah;

Seems that Nvidia-prime works better in 14.04.
Remember, one had to purge BumbleBee prior to installing Nvidia-prime .

Conflicts, conflicts[INDENT][INDENT][INDENT]all these conflicts - 
[/INDENT]
[/INDENT]
[/INDENT]

SO should i stick with BumbleBee, or use Prime?

---

### Post by Bashing-om on 2014-12-25
linux junkie; Hey;

Nothing says you can not purge BumbleBee, intall Nvidia-Prime and see for yourself which you prefer.
With care can always be reverted to what you choose.

[INDENT][INDENT]use what works best for you
[/INDENT][/INDENT]

---

