---
title: "VMWare 6 Feisty guest +paravirtual kernel + Wine =&gt; VMWare crash"
date: 2007-05-18
forum: General Help
---

### Post by daspooky on 2007-05-18
Hello all,

This is my setup:

- Windows XP host operating system running VMWare Workstation 6
- Ubuntu Feisty guest operating system, upgraded to the version 6 virtual hardware

- I have enabled paravirtual kernel support in the virtual machine's settings
- I have updated my Wine version to the latest one (0.9.37)


Now the problem:

Everytime I try to run "winecfg" VMWare crashes with the error "Internal Monitor Error", and the virtual machine shuts down. This error also occurs when I try to run Photoshop through Wine (I didn't test with other software yet).

I noticed this doesn't happen when I run the Ubuntu guest without paravirtual kernel support. 

I searched all over the net and WINEHQ but couldn't find anything about any incompatibilities between Wine and VMI. Does anyone have a clue what is going wrong?

---

### Post by veloce on 2007-05-19
> **daspooky said:**
> Hello all,

This is my setup:

- Windows XP host operating system running VMWare Workstation 6
- Ubuntu Feisty guest operating system, upgraded to the version 6 virtual hardware

- I have enabled paravirtual kernel support in the virtual machine's settings
- I have updated my Wine version to the latest one (0.9.37)


Now the problem:

Everytime I try to run "winecfg" VMWare crashes with the error "Internal Monitor Error", and the virtual machine shuts down. This error also occurs when I try to run Photoshop through Wine (I didn't test with other software yet).

I noticed this doesn't happen when I run the Ubuntu guest without paravirtual kernel support. 

I searched all over the net and WINEHQ but couldn't find anything about any incompatibilities between Wine and VMI. Does anyone have a clue what is going wrong?

Why are you using Wine under a virtual ubuntu on a windows host?  Why would you not just run the windows program under windows?

---

### Post by daspooky on 2007-05-19
I knew someone would ask this question. The point is it is a work laptop, and we're not allowed to install whatever we want in the host OS. As I'm am using this laptop every evening at home for private purposes, I made an Ubuntu Virtual Machine, and use this VM for these purposes.

The thing is, wine should be able to run in an Ubuntu VM, it does when disabling paravirtual kernel support. So I'm still curious to find the solution to this problem.

---

### Post by veloce on 2007-05-19
My guess would be a bug in the paravirtual kernel - isn't it still experimental?

I'd work around it by using a windows vm to run windows software.  I've done this - windows vm under windows for similar reasons to yours. 

Sorry I can't be more help.

---

### Post by daspooky on 2007-05-19
> **veloce said:**
> My guess would be a bug in the paravirtual kernel - isn't it still experimental?

I'd work around it by using a windows vm to run windows software.  I've done this - windows vm under windows for similar reasons to yours. 

Sorry I can't be more help.

Indeed, I think it is still experimental. Your solution of a windows vm is also a good alternative, but in the meantime I'm just running the Ubuntu VM without paravirtual support. I'm not even sure if enabling paravirtual kernel support makes any difference anyway :)

---

