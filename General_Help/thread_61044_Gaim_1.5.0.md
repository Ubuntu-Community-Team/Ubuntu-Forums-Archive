---
title: "Gaim 1.5.0?"
date: 2005-08-30
forum: General Help
---

### Post by Zalbor on 2005-08-30
The newest version of gaim on its own site is 1.5.0, but the newest I can find in the ubuntu repositories is 1.4.0, which has many bugs. Normally I'd think that they simply haven't added the new version yet, and I'd ask why it's taking so long. But a friend who has ubuntu says synaptic shows him gaim 1.5.0. We compared our /etc/apt/sources.list files, and we both have the same repositories:

deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse
deb-src [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe multiverse

deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe multiverse
deb-src [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) hoary-updates main restricted universe multiverse

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

So is it possible for me to install 1.5.0?

---

### Post by fmerenda on 2005-08-30
I have built gaim-1.5 for Ubuntu Hoary, you can download it at:

[gaim-1.5.0](http://www.frankandjacq.com/files/gaim-1.5.0_1.5.0-1_i386.deb) 

it's built with silc support, and built on the i686 platform. I don't know if I did the naming correct, but it will install and run just fine. You may have to uninstall it if you upgrade to breezy/next release of Ubuntu, because it may not be upgraded. Synaptic can help with that also.

to install, just save the file, and then:

sudo dpkg -i gaim-1.5.0*

I hope this helps. I *just* made this last night, because I needed silc support for work!

Take care,
-Frank

---

### Post by taktu on 2005-08-31
[QUOTE=fmerenda]I have built gaim-1.5 for Ubuntu Hoary[/QUOTE]

you wouldn't happen to know of any PPC version now would you? :sad: 
cause compiling gaim just doesn't work for me (probably because of my noobness)

---

### Post by froguz on 2005-09-07
[QUOTE=fmerenda]I have built gaim-1.5 for Ubuntu Hoary, you can download it at:

[gaim-1.5.0](http://www.frankandjacq.com/files/gaim-1.5.0_1.5.0-1_i386.deb) 

it's built with silc support, and built on the i686 platform. I don't know if I did the naming correct, but it will install and run just fine. You may have to uninstall it if you upgrade to breezy/next release of Ubuntu, because it may not be upgraded. Synaptic can help with that also.

to install, just save the file, and then:

sudo dpkg -i gaim-1.5.0*

I hope this helps. I *just* made this last night, because I needed silc support for work!

Take care,
-Frank[/QUOTE]
 thanks fmerenda for the pakage
¿why there isn't a .deb in the official gaim site?

---

