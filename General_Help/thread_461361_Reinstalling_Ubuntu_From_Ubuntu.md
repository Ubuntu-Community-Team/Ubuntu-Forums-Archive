---
title: "Reinstalling Ubuntu From Ubuntu"
date: 2007-06-01
forum: General Help
---

### Post by Mikey_MW on 2007-06-01
Ok, Ive been using Ubuntu on my compaq laptop for a while now, its just a tad slow. Id like to try to do a low memory installation (using the instructions from this forum) which requires that I install Ubuntu Server. 

Here is the problem. It currently has ubuntu desktop 7.04 (nothing important on it, all back up copies made) but no cd-rom drive. I installed ubuntu with wubi netinstall... but I cant do that again, because I deleted Windows and gave ubuntu the whole hard drive... any ideas?

The specs are:
Pentium III-Mobile 1400 MHZ
256 MB SD133 RAM
120 GB PATA/133 Drive
Intel Integrated Graphics (thats what I think slows it down the most)
Intel Integrated Sound

---

### Post by pbw on 2007-06-02
Why dont you download the iso, mount it and add it to grub. then boot up with that? You'll need to make a small partition for it. But other than that it's pretty straightforward stuff.

Not sure of any howto offhand, but i dont mind walking you through it.

-- pbw

---

### Post by Mikey_MW on 2007-06-02
Ok, I'm partitioning now. I'm going to try and combine a few different tutorials I've found to do it, but thanks for pointing me in the right direction.

---

### Post by jjacobs2 on 2007-06-02
Well it may be too late but couldn't you get the same result by removing some unnecessary packages from synaptic or removing services?  If you're doing a reinstall you might want to consider a light weight distro like xubuntu or fluxbuntu.

---

