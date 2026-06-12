---
title: "Boot VM-Image Natively"
date: 2008-01-03
forum: General Help
---

### Post by Nirva on 2008-01-03
Hay,

just for fun, I would like to try to install Gentoo, because I want to find out if compiling everything yourself really  is faster and I think I will learn a lot from it.
But for practical reasons, I would like to this in a VM-Image.  So I can browse the internet etc in my  host, while installing Gentoo in VM.

Now my question is :Supposed I complete the installation, is it possible for me to boot this installation NATIVELY ( so not in VM ) by copying or editing this VM-Image ?

Thanks for your time

edit : typo

---

### Post by g2g591 on 2008-01-03
I'm not sure, but I'm installing Gentoo on another partation, by using (K)ubuntu's terminal, to unpack the stage3 and portage tarball (possibly on the cd), all the commands on the install guide work just fine from Ubuntu/ the Gentoo chroot. So while the install runs, I can use Kubuntu and all its apps just fine. This method probabily would be faster than running the cd in VM, as you don't have the overhead of running 2 os'es, so compileation would be faster

---

### Post by jespdj on 2008-01-03
No, I don't think so.

When you are running an operating system in a virtual machine, then all the hardware will be virtualized. So the OS in the VM will not have direct access to your video card, harddisk, network card etc., and it won't know what the real brand and model is of those things. It will be using drivers for the virtual, not the real devices.

When you would run the OS in the VM natively, it would suddenly see hardware that looks completely different (because it would see the real hardware instead of the virtual hardware). If it has set up device drivers for the virtual devices then those will not work with the real devices, and in the case of a distro like Gentoo, it will certainly not be optimized for your real hardware.

So you can first play with it in a VM to learn how it works, but if you want to run it natively, you'll have to set it up from scratch again.

---

