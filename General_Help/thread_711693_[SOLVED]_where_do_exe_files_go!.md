---
title: "[SOLVED] where do exe files go!"
date: 2008-02-29
forum: General Help
---

### Post by japephillips on 2008-02-29
I am still new and struggling. I am used to looking for exe files after winstallation and clicking on them, and also to saving programme downloads, installing etc. but thus having a programme package i can backup or transport.
with linux i have been downloading via package managers, either add/remove (ubuntu) which usually installs but doesn't leave a file I can copy to a disc  as backup or install elsewhere
or if i use 'synaptic' it downloads and does something but doesn't drop an exe icon or similar for me to open with
If i just download a tar  file directly  i can save it of course and then extract the files but they don't seem to 'instal'l always
what files should i be clicking on to get an install, what and where are the equiv of an exe filed?
there are all sorts of bins and usr/bins and none seem to hold what i want
so i still don't know if things are installed or where to find them
i reread that and it makes sense to me, hopefully it will to you!

---

### Post by PeterJS on 2008-02-29
Exe are windows executables, the windows package format is acutally Msi, but very few people know that because they're rarely used. The exe's you're talking about are programs that have the incidental side effect of leaving the system with more software than it started with and aren't actually packages. This is a really bad way of going about things, it's quite messy, but it's easy. What you're looking for are the deb packages, package files installed through the package management system are cached in */var/cache/apt/archives/*.

---

### Post by japephillips on 2008-02-29
Thanks. So if I want to copy programme files to CD and then put them on another machine or use after another install, I can save and update that folder and it will have all the information needed to re-install?

---

### Post by PeterJS on 2008-02-29
There's more to it than just that, there's also the package index which tells they system what versions are available and how they relate to each other.  The index is some where in /var/lib/dpkg, but the list of installed packages is also in there, I've never dug around in the core of apt enough to separate the two.

You need the index to describe the relationship between the packages in the cache, without the index you'd have to do the dependency resolution by hand, which would be a pain. Backing your cache up would save you bandwidth on things that haven't changed, but they get stale quickly.

---

### Post by japephillips on 2008-03-01
Having dialup and a poor landline I have to think of these things! I need to be able to 'store' programmes one way or another, even if I download them using a friend's broadband from time to time i still need to get them onto my machine.
I can't see a way to 'point' synaptics at , for example, a device such as a flash drive or CD.
I think my best course is to use google to find them and then save programmes as archives, then try and work out how to install them, launch them. That bit has got me lost at present.
Is there a tutorial that you can reccommend for this please?

---

### Post by PeterJS on 2008-03-01
If you're looking to ferry in packages from else where you might want to lookin to APTonCD:
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

I've seen it recomended before but haven't used it myself. The way it works it that it grabs a set of packages and then builds them in to a self contained repository on a CD.

---

### Post by japephillips on 2008-03-01
that looks good, i shall try it, thanks a lot!

---

### Post by japephillips on 2008-03-01
It is brilliant Peter, excellent solution, downloaded and saved what I want in less than ten minutes! You *can* make Synaptics load from it rather than the 'net if you choose and you may also add your own downloads.

Now i am going to try and make it work from a flash drive ...

---

