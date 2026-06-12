---
title: "Problems with NVidia drivers in Edgy"
date: 2006-11-04
forum: General Help
---

### Post by EmyrB on 2006-11-04
Hi,

I am having great difficulties with Edgy (64bit) to install nvidia-glx through apt and automatix. When I run the command apt-get install nvidia-glx, I get the following error: -

The following packages have unmet dependencies:
  nvidia-glx: Depends: nvidia-kernel-1.0.9625
E: Broken packages

Did a search on this forum and loads of people have the same problem, but guess what nobody is answering their questions.

So I have 2 questions I would like the answer to: -

1). Why is the kernel-kernel-1.0.9625 missing?
2). To install the official NVidia drivers from NVidia, I have to install the driver with out the xserver running. I used to be able to change the runlevel's in Dapper but as Edgy is using ustart, I cannot find inttab to edit. So how do I get to a command line without xserver running?

Cheers from a not so happy Edgy user :(

---

### Post by EmyrB on 2006-11-04
Scratch this one, I just commented out 2 repo's in my sources.list and then did and apt-get update and then tried to install the nvidia-glx again and it all worked :D

---

### Post by geoken on 2006-11-04
Which repos did you have to uncomment? I'm having the same problem.

---

### Post by EmyrB on 2006-11-04
Hi geoken,

I commented out the following in my sources.list :-

deb [http://compiz-mirror.lupine.me.uk/](http://compiz-mirror.lupine.me.uk/) edgy main-edgy
deb [http://compiz-mirror.lupine.me.uk/](http://compiz-mirror.lupine.me.uk/) edgy main-edgy main-edgy-amd64

Not sure if you are using them?

But go through your sources.list and only have the original repo's uncommented and try again. It might have something to do with any repo's you have that have compiz or beryl in them.

Hope this helps you!

Cheers

EmyrB

---

