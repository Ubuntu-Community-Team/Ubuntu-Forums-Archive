---
title: "Manually configure build-essential for non-connected pc?"
date: 2008-03-23
forum: General Help
---

### Post by Kouy on 2008-03-23
I have a laptop except for the wireless card isn't working in it but I still like to use it for work and then just use my other computer for home web browsing. There are some programs I would like to install and it's not the actually configuring of them I have having a problem with just the fact that I need the gcc to install any of the packages, but I need to know if there is some way that I can configure build-essential itself without the gcc?

---

### Post by logos34 on 2008-03-23
you don't need to download gcc--it's on the ubuntu live install cd --> /pool/main/g

build-essential needs gcc >4.1.  It's a dependency.

---

### Post by Kouy on 2008-03-23
Oh, really now? Because the thing is I have a fresh install of Ubuntu 7.10 and I'm trying to install PHP5 but when I try to configure it I get the error, "configure: error: installation or configuration problem: C complier cannot create executables." and when I looked I found this page: [http://ubuntuforums.org/showthread.php?t=91073](http://ubuntuforums.org/showthread.php?t=91073) and what I thought I got from that was that I needed build-essentials, but I may be wrong.

---

