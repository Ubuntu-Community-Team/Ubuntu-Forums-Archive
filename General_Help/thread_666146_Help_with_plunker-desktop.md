---
title: "Help with plunker-desktop"
date: 2008-01-13
forum: General Help
---

### Post by Soranus on 2008-01-13
While searching for books from Project Gutenberg, I came across Plucker and tried it on my Tungsten E2. It works great with JPilot and installs ebooks without a hitch. My problem arose when I attempted to install plucker-desktop on Gutsy. I tried to go the long route, but got frustrated when it just wouldn't work, so I tried apt-get. I also tried to dl from [http://packages.ubuntu.com/gutsy/otherosfs/plucker](http://packages.ubuntu.com/gutsy/otherosfs/plucker) with installer, and I tried again the long drawn out way. The furthest I get is to the configuration, no matter which way I go. What am I missing? I've gone back and made sure I had the kernel package, python, gcc, and gtk2. I don't have tremendous experience with Linux, but I'm not entirely lost, either. However, this one has me stumped. What am I missing?

Also, my libwxbase is 2.6, yet after installation, when I issue the command "plucker-desktop", I get the following error:

***
plucker-desktop: /usr/lib/libwx_gtk-2.4.so.1: no version information available (required by plucker-desktop)
plucker-desktop: symbol lookup error: /usr/lib/libwx_gtk_stc-2.4.so.1: undefined symbol: _ZTI8wxWindow
***

Any suggestions at this point would be great!

---

### Post by Soranus on 2008-01-13
Whoops! Make that "plucker-desktop" instead of "plunker-desktop".

---

### Post by Soranus on 2008-01-13
Never mind. I got it fixed. Seems I had two different versions of gtk installed.

---

