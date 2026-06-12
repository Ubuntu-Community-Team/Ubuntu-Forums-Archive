---
title: "XTS-AES full disk encryption via alternative cd"
date: 2008-01-26
forum: General Help
---

### Post by _VWV_ on 2008-01-26
So, I would like to encrypt my system disk with XTS cipher. How do I do that? My plan is to compile a 2.6.24 kernel, and incorporate it into an alternative CD. If I do that, will I be able to use XTS-AES for full disk encryption prior to installation? Sorry, if I sound stupid.. I'm just a noob :-).

---

### Post by kuja on 2008-01-26
Even if you incorporated it, it's hard to say if you would actually get that option (if one is required. If you don't already know how to do that you may very well be better off just doing things manually, perhaps from a livecd. You'd probably have to debootstrap the installation yourself though.

---

### Post by _VWV_ on 2008-01-27
Thanx! I did think that incorporating the needed kernel into an alternative cd wouldn't help, coz I would also have to change the text installer for the XTS-AES option to appear there - that is why I created this topic. 
Also thanx a lot for the debootstrap hint, I've already found some Howto's and they seem to be the solution for my problem.
You really helped a lot. :-) Hope my security paranoia will calm down.
I've got one more question. Is it better to compile a 2.6.24 kernel from my hard-drive based Ubuntu, or should I do it from a live cd?
Thanx in advance.

Edit: to be more precise my plan is as follows: I'll compile a 2.6.24 kernel using this howto ([http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835)) and install it, then I'll put it on a ubuntu live cd with this howto ([https://help.ubuntu.com/community/LiveCDCustomizationFromScratch),I](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch),I) will also put some packages like dm-crypt on the live cd,  then I'll boot from the live cd, encrypt my partitions with dm-crypt, format them, mount them, then I'll follow this howto ([https://help.ubuntu.com/6.10/ubuntu/installation-guide/hppa/linux-upgrade.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/hppa/linux-upgrade.html)). The question is whether it's going to work after I reboot it. How would the kernel know, that the /, /swap and /home partitions are encrypted with xts-aes, and that it should ask for the password... I think I'll see kernel panic..
Ah, I've found this wonderful howto ([http://www.cs278.org/blog/ubuntu-configuration/feisty-debootstrap-encrypted-install/](http://www.cs278.org/blog/ubuntu-configuration/feisty-debootstrap-encrypted-install/)) so it's not gona be a problem.

---

### Post by kuja on 2008-01-27
Sounds like a .lot of work for not enough gain with regards to altering the livecd - I think I'd just copy any needed packages (ie: custom kernel, dmcrypt, etc) onto a thumb driive or another cd-r. It'd probably be easier/less time consuming at any rate.

Good luck with things. 

(I'm conveniently less paranoid ... I'm just using what was on the alternate CD myself ... wish I could use it on my desktop but there's  some sort of conflict and/or bug in the way ...... Seems the Linux nforce4 chipset driver and probably dmmod don't play well together :-()

---

### Post by _VWV_ on 2008-01-29
I'm sorry, didn't get you.
To encrypt my partitions like / and /home I need to run a kernel, capable of that, after encryption I'll install Ubuntu and try to boot it - so to unlock the disk that ubuntu installation should also be based on 2.6.24 kernel... so any way I should incorporate it into  the live CD, and then make a fresh installation from it.. Isn't it? How can I encrypt my disk, if liveCD's kernel doesn't support the needed xts-aes cipher? Sorry my noobness. :-)
Any way, I've already compiled my kernel :-) it works, though it turned out that vanilla kernels doesn't have acx100 drivers... I'll install them later. I think I'll try to encrypt something with new kernel before I  erase everything :-) just to see whether it works or not.

---

### Post by _VWV_ on 2008-01-29
It works! :-) dm-crypt with xts-aes! Nice!!! (though I had to sacrifice all the info on my USB flash...)

---

### Post by kuja on 2008-01-29
Though slightly more convoluted, the other way other than your livecd route would be to have two installations - one that you'd encrypt, the other would be small and only used for setting up the encryhpted partitinon, then either deleted later or kept in case something goes wrong.. That would probably require less work than the livecd route, but it is of course your call.

---

### Post by _VWV_ on 2008-01-29
Yeah, thanks, I've already found that option.. After reading Howto's  I decided to make an install of 7.10 to an external drive, compile 2.6.24 kernel for it, and use it to encrypt my internal disk and install ubuntu via debootstrap.  ([http://www.cs278.org/blog/ubuntu-configuration/feisty-debootstrap-encrypted-install/](http://www.cs278.org/blog/ubuntu-configuration/feisty-debootstrap-encrypted-install/))
ThanX a lot! Your hint's guided me to an appropriate solution. Creating a proper live CD would have been the best solution but it's too geeky for me, I'm not that experienced. 
So, thanX once again.

---

