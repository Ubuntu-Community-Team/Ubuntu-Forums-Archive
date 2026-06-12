---
title: "Busybox.. Initramf?"
date: 2008-06-26
forum: General Help
---

### Post by Fruddy123 on 2008-06-26
I tried to install Ubuntu on my Lenovo laptop, but right after the loading screen a kind of terminal appears saying something with Busybox and Initramf? 

One more thing.. After this happened, my computer started up with Windows Boot Manager and asked me if I wanted to boot Vista or Ubuntu. I tried to remove the Ubuntu disc, but it still pops up when I'm booting!?

---

### Post by Fruddy123 on 2008-06-27
Bump!

---

### Post by hpdv9500 on 2008-06-27
I have the same problem. Although mine isn't a new install. I was playing around with grub. trying to get a suse like grub for ubuntu. That did not work (gave me a message.suse missing but thats another issue for another thread)

I get that initramf prompt too. If i boot in recovery mode and choose boot in normal mode, it boots and everything works fine! Anyone have any idea whats going on here?

Thanks!

I've tried reinstalling grub - but am having the same prob.

---

### Post by Lipaugus Vociferans on 2009-10-17
Same thing to me, I had a slave disk plugged when updated the kernel and now I CAN'T BOOT WITHOUT IT... if I replug the slave it boots normally but when I remove it, I just get the same busybox, initramfs console whatever that says that the device is not present or delay on root account...blah blah...
There is no way to boot without withot the slave...
Viva Grub2:evil: I DONT HAVE AN IDEA OF HOW TO CHANGE IT...:confused::!:

---

### Post by bhondumal on 2009-12-18
My system also got same problem.
Iwas running ubuntu very well. The morning I put some updates (about 50 out of 368 or so) and installed google chrome beta. everything was running fine till shutdown.
But after that when started again it reaches to the BUSYBOX and stays at a command prompt INITRAMF. In recovery mode it says that the root disk failed to mount, loading shell etc...
I think it has to be removed and installed fresh. All the files there will get lost :(
Any help !!!

---

### Post by glenng on 2009-12-18
I have a similar problem. I dual boot Vista and 9.10 0 -- turned off the computer in the morning and in the afternoon it would not boot to 9.10. However I can boot to Vista.

Got the message: ALERT /dev/disk/by-uuid/0b53aac8-7f0c-4b3e-9431-433be 7e564b2 does not exist. Dropping to a shell!

Is it a mount point in /etc/fstab and can anyone tell me how to repair this problem?

---

