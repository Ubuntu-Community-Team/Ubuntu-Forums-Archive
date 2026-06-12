---
title: "Compilng Custom Kernels"
date: 2008-04-19
forum: General Help
---

### Post by Wastedyouthfx0 on 2008-04-19
Hello,

Ubuntu has done a great job of sparking my interest in Linux and its made a great D?esktop system for me.  However, I'm interested in learning how it works.  When can I see Ubuntu-from-scratch?

So, when I boot my system, I currently have several kernels to choose from.  At the end of the kernel versions theres an addition like  2.6.24-16.  What does the -16, or -14, or -11 actually mean?  Is it all the same kernel with different option configured in to compile?

Is there a tutorial for compiling your own custom kernel if you wanted support for something that wasn't already in there?  I already see that I can download the source 2.6.24, but it doesn't have a -11, or -16 next to it.  

If I were to download the source and copy the /boot/.config file into the source and compiled a kernel, would I be getting the 2.6.24-16 just like I'm using now?

---

### Post by Bachstelze on 2008-04-19
The Ubuntu kernels and the official (or "vanilla") kernel have different numbering schemes :

In Ubuntu, **2.6.24-16** (with a dash) mreans that it the 16th version of a kernel that was compiled for Ubuntu, by the Ubuntu kernel team, and from sources that were based on the official 2.6.24 sources.

In the official sources, **2.6.24.16** (with a peiod) would mean that it's the sixteenth revision of the 24th version of the 2.6 kernel branch. In other words, it means that there has been changes in the source since the previous revision, but the developers considered that those changes were not important enough to justify moving to a new version.

---

### Post by Diabolis on 2008-04-19
There are TONS of tutorials and sites that talk about compiling your own kernel and the numbers that you see are only version numbers.

Linux kernels are being developed by linux-foundation. They picked up linux kernel development from the 2.6X version. You can read more about them in their official page:
[http://www.linux-foundation.org/en/Main_Page](http://www.linux-foundation.org/en/Main_Page)

[this is a good press release, about who writes and supports the kernel]("http://linux-foundation.org/weblogs/press/2008/03/31/linux-foundation-publishes-study-on-linux-development-statistics-who-writes-linux-and-who-supports-it/")

and

[this is about the version numbering]("http://www.linux-foundation.org/publications/linuxkerneldevelopment.php")

---

