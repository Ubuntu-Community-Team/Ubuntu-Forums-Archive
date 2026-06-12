---
title: "C header files"
date: 2007-04-28
forum: General Help
---

### Post by dandago on 2007-04-28
Hi,

This post might sound a bit stupid, but I've been looking all over the internet for a few days now and don't know where else to ask.

Recently I downloaded Kubuntu 7.04 and installed it over a virtual partition of VMWare. The installation went fine and all. However Kubuntu is so bare... I did download some software myself (e.g. Firefox), but the most important thing appears to be missing. Kubuntu does not seem to include any of the standard C header files, so C development is impossible. I can't seem to find them anywhere for download. Also, I don't understand what's the point of including gcc when there aren't any header files.

Where can I find the header files?

I really can't understand why Kubuntu is so bare anyway. Knoppix has loads of software on it, and it fits on a CD as well.

---

### Post by lloyd_b on 2007-04-28
The C header files are in the package "libc6-dev".  So installing that package will take care of that issue.

However, the fact that the  headers are missing makes me wonder if you have a broken build system.  I'd recommend installing "build-essential", which *should* include "libc6-dev", as well as everything else you need for a working build system.

Assuming you have  a working internet connection, installing the packages is very simple - either use the graphical package manager (Adept, is believe, for Kubuntu), or in a terminal window type "sudo apt-get install {package}".

Lloyd B.

---

### Post by dandago on 2007-04-28
Just to be sure I didn't mess up something myself, I reinstalled Kubuntu. Still no header files.

I now installed build-essential and my problem is solved. Thank you very much.

I still wish that such important things would be bundled with the distribution.

---

### Post by bbala2020 on 2007-11-25
where do i get that build-essential ? my 'add/remove programs' from application menu doesnt recognise the internet connection but my synaptic package manager does. how do i fix this?

---

