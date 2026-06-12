---
title: "All input seems unresponsive after installing latest kernel."
date: 2013-05-02
forum: General Help
---

### Post by meteora184 on 2013-05-02
Hey everyone.

I am taking an operating systems course, and part of the materials consist of adding system calls to the kernel, and compiling and running the latest kernels.

I am currently an issue with getting the latest kernel properly installed.

I am running LUbuntu 13.04 on VirtualBox 4.2.6.

I was instructed to download the latest kernel from kernel.org so I downloaded the 3.9 tarball.

I extracted it, and ran make menuconfig in the main directory of the source.

then called:
make
sudo make modules_install
sudo make install

when I reboot the virtual machine, everything seems unresponsive. My virtualmachine no longer seems to respond to any mouse movement or keyboard input. The internet is also unable to connect.

I am unsure if this is an issue with the VM, or with how I installed the kernel, or possibly both.

I am able to press f11, and boot on my old kernel, where everything works.
I am currently piping the make output into a text file as I do recall having some warnings, and will do so with all the other commands as well.

I was wondering what could possibly explain this?


When i finished my make, i did have an issue. it said

WARNING: modpost: Found 1 section mismatch.
to see full details build our kernel with:
'make CONFIG_DEBUT_SECTION_MISMATCH=y'
so I am running that currently. Could this be the reason possibly??

---

### Post by QIII on 2013-05-02
Hello.

I suspect that Vbox is not ready for that kernel if you are getting problems like that.

You might want to cruise the forum at virtualbox.org and see what pops up there.

But keep checking back here, too!

Regards

---

### Post by meteora184 on 2013-05-02
QIII,
I did notice that virtualbox had an update. which I did ignore. So I am definitely gonna try and update that. But currently I am in the process of running make again... so I'll just wait till that's over before I do anything else. -__-

Thanks for the input though I'll definitely keep posted.

---

### Post by meteora184 on 2013-05-02
I ran
make CONFIG_DEBUG_SECTION_MISMATCH=y

[IMG]http://img832.imageshack.us/img832/8761/erroryf.png[/IMG]

and thats what I got. I do not know what farsyn.c does, but thats only a warning.

theres also an error in built-in.o
its in the drivers folder. I really don't know much about this stuff and was hoping someone could help me out.

---

