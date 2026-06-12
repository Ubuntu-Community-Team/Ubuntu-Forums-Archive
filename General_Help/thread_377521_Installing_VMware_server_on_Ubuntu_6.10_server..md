---
title: "Installing VMware server on Ubuntu 6.10 server."
date: 2007-03-06
forum: General Help
---

### Post by ichiuk on 2007-03-06
Hi,

I've just installed Ubuntu from the ubuntu-6.10-server-amd64.iso on a Dell 2950, with a 4 core Xeon CPU. I am trying to install VMware server, but having problems compiling it for my kernel. The kernel I am running is 2.6.17-10-generic. I've installed linux-headers-2.6.17-10 but when I'm installing VMware I get error messages when it asks me for the location of my header files...

If I use the directory /lib/modules/2.6.17-10-generic/ it tells me it can't find the linux subdirectory as expected.

If I use /usr/src/linux-headers-2.6.17-10/include it tells me "The directory of kernel headers (version 2.6.17-10) does not match your running kernel (version 2.6.17-10-generic). Even if the module were to compile successfully, it would not load into the running kernel."

I'm at a loss, I've been searching the forums for an answer but can't fine one. Does anyone know the solution?

TIA...

---

### Post by zvacet on 2007-03-06
Try with linux-headers 2.6.17-10-generic.

---

### Post by jocko on 2007-03-06
Install the metapackage linux-headers-generic (note that there is no version number in the package name). it will make sure you get the correct headers for your kernel.

---

### Post by ichiuk on 2007-03-07
Thanks for the replies...

If I do apt-get install linux-headers-generic it tells me the package is not found.

If I try just linux-headers then it offers me the following packages...

linux-headers-2.6.17-10
linux-headers-2.6.17-10-server

I've tried installing them and I just the error from VMWare saying they don't match my running kernel... :(

---

### Post by ichiuk on 2007-03-08
Good news :-)

I've found this script, which sorted it all out for me...

[http://users.piuha.net/martti/comp/ubuntu/server.html](http://users.piuha.net/martti/comp/ubuntu/server.html)

Very handy...

---

