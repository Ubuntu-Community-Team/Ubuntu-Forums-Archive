---
title: "XP Virtualization - Parallels vs. VMWare"
date: 2007-06-13
forum: General Help
---

### Post by rscott5 on 2007-06-13
Hi all,

I'm in the process of getting a new Ubuntu machine, 3GB RAM 2.4GHz Core 2 Duo etc. (possibly one of those nifty new Dell XPS 410N?). Anyways I would like to run Windows XP Professional in a virtual environment on my new machine. Here are my questions:

I've used Parallels in Mac OS X to run Windows XP Pro and absolutely love it. Is there anyone here who has used it / could give some feedback about how well it works in the Linux environment (more specifically Ubuntu 7.04)? If it is as good as on OS X then I wouldn't at all mind paying the price to purchase it.

Second, everyone on this forum seems to talk about VMWare whenever they mention running XP virtually. Why is this so popular (aside from it being free)? I've used it once in RedHat, and no offense to anyone, but compared to my experience with Parallels, it felt ugly and slow. It just seemed like Parallels is a lot cleaner looking and a lot easier to get around in, plus Parallels seems to have a ton more features for mouse smoothing, screen resolutions, etc.

Can anyone offer some sort of comparison between the two applications as to which one runs better, looks better, etc. in Ubuntu? Any comments at all would be greatly appreciated.

Thanks in advance for all your help, I know this could be somewhat of an open-ended, debate-causing post, but I'm just trying to get the scoop on Windows virtualization in Linux before I'm knee deep in it myself.

---

### Post by revertex on 2007-06-14
first of all make sure to buy a cpu that supports virtualization extensions, like intel Vanderpool and AMD Pacifica.

I used parallels long time ago and come back to vmware, that seems a superior product at the time.

If you are looking for easynes stuck with vmware or parallels, but if you are interest in real performance you should take a look at KVM module 

[http://kvm.qumranet.com/kvmwiki](http://kvm.qumranet.com/kvmwiki)

---

### Post by smoker on 2007-06-14
hi, i've never tried parallels, but have tried vmware and virtualbox. i would recommend you give virtualbox a try, it is simple to install and setup (i think it might be in the repositories, though not sure), anyway, details of virtualbox can be found here:
[http://www.virtualbox.org/](http://www.virtualbox.org/)

best of luck

---

### Post by revertex on 2007-06-14
Virtualbox lacks a full featured network support for complex network schemas, but works fine for simple virtualization.

It seems virtualbox is a graphical front end to qemu.

---

