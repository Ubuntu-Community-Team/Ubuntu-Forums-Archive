---
title: "installing old Kernel"
date: 2007-02-11
forum: General Help
---

### Post by glue on 2007-02-11
Is it possible to install an old kernel with Kubuntu 6.10 to see if it works better with my hardware?

---

### Post by energiya on 2007-02-11
You could compile a vanilla kernel, or just install the 2.4 one. I think it's in the repository. DON'T remove or modify your current kernel, because you may need it if something goes wrong.

---

### Post by Arisna on 2007-02-11
Very possible.  I just installed a Dapper Kernel on my Edgy box because I was having some annoying hardware compatibility problems (couldn't reboot machine properly, lots of error messages incorrectly indicating that my fans weren't working).

Here's what I did:

I went to [https://launchpad.net/ubuntu/dapper/+search?text=linux](https://launchpad.net/ubuntu/dapper/+search?text=linux) , which is a search in Dapper packages for "linux".  Many results relate to the Linux kernel.  Specifically, older versions thereof.  For me, 2.6.15 was the last time everything worked well for me.  I have an Athlon k7 processor, so I chose the following package:

[https://launchpad.net/ubuntu/dapper/+package/linux-image-2.6.15-25-k7](https://launchpad.net/ubuntu/dapper/+package/linux-image-2.6.15-25-k7)

You'll need to make the selection based on your hardware, of course.

Also note that I did not bother grabbing the complete image or restricted modules because I don't need any restricted modules.

Hope you find this useful!

Edit:  Actually, the last available version of kernel 2.6.15 seems to be 2.6.15-28, so I'm grabbing it now.  Also, I decided to grab restricted modules anyway.

---

