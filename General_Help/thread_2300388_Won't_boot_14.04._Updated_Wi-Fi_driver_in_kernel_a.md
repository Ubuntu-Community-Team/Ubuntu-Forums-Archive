---
title: "Won't boot 14.04. Updated Wi-Fi driver in kernel and now won't boot"
date: 2015-10-25
forum: General Help
---

### Post by FurmanSK on 2015-10-25
Hi all,

I updated my Wi-Fi driver for my media machine and in doing so I had to compile/build it and install into the kernel based on this guide [http://askubuntu.com/questions/471208/realtek-wireless-adapter-issues-rtl8192ce-and-rtl8192cu]("http://askubuntu.com/questions/471208/realtek-wireless-adapter-issues-rtl8192ce-and-rtl8192cu"). After rebooting I get a kernel panic and instantly think ohhhh crap. I've tried to research it and finally just loaded up liveUSB of ubuntu 14.04 and just loaded a new kernel over. I also tried to do a boot repair thinking it was the issue and to no avail I was stuck. I no longer get a kernel panic but it could be the fact that my grub2 is now messed up and not finding anything. I'm stuck and don't know what to do.

Thanks,

FurmanSK

---

### Post by ajgreeny on 2015-10-25
What do you mean by "just loaded up liveUSB of ubuntu 14.04 and just loaded a new kernel over."?

---

### Post by FurmanSK on 2015-10-26
Thanks for replying ajgreeny. Sorry for not elaborating on that. I loaded up a live USB of ubuntu desktop 14.04 and installed the generic kernel over to my base image, can't remember the command off the top of my head. Not realizing that I had actually been running the server 14.04 instead of desktop because I had issues before getting it to install with mdadm and a raid 5 setup.

---

### Post by Bucky Ball on 2015-10-26
*Thread moved to **General Help**.*

---

### Post by ajgreeny on 2015-10-26
> I loaded up a live USB of ubuntu desktop 14.04 and installed the generic kernel over to my base image, can't remember the command off the top of my head.I am still not sure if you actually installed the kernel into the filesystem of the installed OS using chroot, or just copied it from the live system, so I can't help at the moment with the info you have given.

---

### Post by FurmanSK on 2015-10-27
Hey AJ, sorry, what can I provide to help figure this out? I don't remember if I chroot then did the install of the generic kernel or not, I believe I did actually but I'll find the guide I was  using to prove that. Now what it does is it loads up and comes to a grub prompt and won't let me start the kernel manually. I do an "ls" command in grub prompt and all but Hd5 are ok. I believe hd5 gives me the can't read 0x0. I am at work right now so I can't exactly get the info. I can provide more after 4 EST today.

Thanks and sorry again for not providing enough information.

***UPDATE****
Ok so here is what I used to re-install the kernel.
[http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels](http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels)

Would it matter if this was for the desktop and I was running the server ubuntu?

Thanks.

---

### Post by FurmanSK on 2015-10-27
Here's my boot-info script. Will this help?

[http://paste2.org/WFbKb3O5](http://paste2.org/WFbKb3O5)
[http://paste.ubuntu.com/12984680/](http://paste.ubuntu.com/12984680/)

Thanks,

-Furman

---

### Post by ajgreeny on 2015-10-28
It's a pity you did not tell us this was a raid setup with 5 disks, which means I'm afraid that I can't help you at all as my knowledge of raid systems is a bit lower than zero, zilch, nada.

Sorry about that, but it does seem unlikely to me that adding a wifi driver to a system, whether raid or normal, has had anything to do with this new lack of ability to boot, and thanks for the clarification that you did, indeed, use chroot to install the new kernel.

---

