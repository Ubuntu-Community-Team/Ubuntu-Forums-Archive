---
title: "Genral Issue With OpenGL Driver (extended to an apt-get issue)"
date: 2015-11-06
forum: General Help
---

### Post by fabian.dettenriede on 2015-11-06
Hello everybody,

I know, this issue has been argued multiple times and there might be a solution, but I personally have not managed to make it work on my system. Any help, any comment, any recommendation is highly appreciated.

That being said, I suppose it is obsolete to say that I am fairly new to the Linux/Ubuntu community. For my studies, I recently took over a desktop computer from a colleague running a 64bit Ubuntu 14.10. It might not be the most modern computer but still fairly high-tech (from my point of view). However, I have been experiencing laggy behaviour especially when switching windows, tabs, clicking on links, etc. Also - that's how I got suspicious - when opening Matlab, I noticed that it couldn't read some libraries associated with OpenGL leading to software rendering within Matlab. This might not be an issue for Matlab itself, but since I am working with large datasets and visualization of 3d flow simulations, I will eventually need the full graphic resources. It also does not make sense to have a fully-capable computer and using only 5% of its capacity while complaining about laggy behaviour :-)

So I did some research trying to find a way to resolve this issue. Multiple solutions seemed to exist, one stated here: [http://askubuntu.com/questions/450555/very-slow-graphics-performance-after-upgrade-12-04-14-04](http://askubuntu.com/questions/450555/very-slow-graphics-performance-after-upgrade-12-04-14-04). Apparently, it is a driver problem with NVIDIA cards (which I have). So I tried to reproduce the (3-line) solution recommended by that guy, which lead my to yet another problem.

I generally run into problems using apt-get no matter what software I want to acquire. It always ends up saying, that it couldn't fetch some data and an error 404 occured. Also, I cannot download any software using the Ubuntu Software Center, because it says "Requires installation of untrusted packages" and stops the installation process. These might be different problems, I just figured if they are related, it might be helpful for finding the actual problem.

So from my research online, I figure the issue for apt-get not to work comes from the impossibility to resolve a URL or find the proper repository. As soon as I am editing the "sources.list" I get freaked out being afraid to crash the system :?

It all comes down to these questions:
1) Why is apt-get not working?
2) Is it related to the Ubuntu Software Center not working?
3) Is it really an NVIDIA driver issue for the system to be laggy or is it just a broken OpenGL library (link)?

I already thought about a clean install of the system, which might resolve all these issues at once. However, my colleague still has some data and software (running) on the system. Also, I saw that a new LTS version will be released in a few months, and I think that would be a good time to jump onto an LTS version of Ubuntu.

I would very much appreciate any kind of help and/or (productive) criticism.

Thanks already for your time and consideration.

Fabian

---

