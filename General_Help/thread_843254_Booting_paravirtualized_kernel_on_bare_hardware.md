---
title: "Booting paravirtualized kernel on bare hardware"
date: 2008-06-28
forum: General Help
---

### Post by HunterThomson on 2008-06-28
In the boot up log it said:

Booting paravirtualized kernel on bare hardware

Why is it "Booting paravirtualized kernel on bare hardware" I am not runing it in a VM?????? It is my main and only OS on my HDD.

What is going on ? 

I'd like to know more but all I get with google is stuff about VM? 

I would be thankfull for any ideas:)

---

### Post by HunterThomson on 2008-06-28
Well,

I guess that is just what archlinux does??? From what I can tell.... I can't find anything that talks about it directly. I just find indirect remarks... If anyone knows what is up, I would like to know.

---

### Post by swedishsax on 2008-07-13
Hi there,

You're being told that you're booting a paravirtualized kernel on bare hardware. Did that help any? :)

Paravirtualization allows the kernel to run more efficiently when it is being run on a virtual machine (the Guest OS in VMware speak), but it has no effect when running on a real processor. This option is enabled in most distros' kernels since they don't know where you're going to be installing the OS.

The kernel is simply saying you're booting a kernel on a real CPU which you might have intended for running on a virtual machine. It'll still run and AFAIK there are no performance penalties.

/Uffe

---

