---
title: "libc6, install ATI drivers"
date: 2012-12-10
forum: General Help
---

### Post by ivotkl on 2012-12-10
Hello. I have tried what was suggested here and [there](http://ubuntuforums.org/showpost.php?p=12398441&postcount=4).

According to [Ubuntu Packages](http://packages.ubuntu.com/search?suite=precise&searchon=names&keywords=glibc), last version of libc6 is 2.15. However, to install ATI drivers I am asked to get 2.2 or 2.3.

I've seen Package clisp-module-bindings-glibc, that "adds the glibc bindings". Its version is "1:2.49-8.1: amd64 i386".

Any ideas?

---

### Post by oldos2er on 2012-12-11
Post moved to its own thread.

---

### Post by Mark Phelps on 2012-12-11
Why are you installing ATI drivers this way in the first place?

Usually, you just use "additional drivers" and do it that way, as that will handle all the dependencies.

Also, why are you installing ATI drivers in the first place?

Ubuntu installs the open-source Radeon drivers by default if you're using an ATI or AMD chipset, and unless you're doing intensive #3D gaming that needs hardware acceleration or having overheating problems on an AMD GPU, there is no value in installing those drivers.

---

### Post by ivotkl on 2012-12-11
Hello Mark, thank you for your reply.
 
I see nothing supported when going to additional drivers and yes, I am having overheating problems on an AMD GPU.

---

### Post by Mark Phelps on 2012-12-12
OK then, look through the info in the link below and see if that helps:

[http://www.howtogeek.com/howto/17495/how-to-add-proprietary-drivers-to-ubuntu-10.04/]("http://www.howtogeek.com/howto/17495/how-to-add-proprietary-drivers-to-ubuntu-10.04/")

---

### Post by ivotkl on 2012-12-12
I' ll explain myself better. I have no additional drivers support for current PC. I knew those steps already and tried them.

---

