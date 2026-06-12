---
title: "Can't install Virtual box in heron"
date: 2008-05-05
forum: General Help
---

### Post by kingleer on 2008-05-05
Greetings, 

I've got the 32 bit version of Ubuntu 8.04 installed on my computer. 

I tried to install virtualbox 1.60 by following this guide 

[http://ubuntuforums.org/showthread.php?t=770745&page=6](http://ubuntuforums.org/showthread.php?t=770745&page=6) 

It didn't install though. 

I checked /var/log/vbox-install.log, and got the following error: 

> 

/etc/init.d/vboxdrv: 311: /usr/lib/virtualbox/src/build_in_tmp: not found
 

How do I fix this? I kinda need help with this as quickly as possible, but thanks in advance.

---

### Post by kingleer on 2008-05-05
I found a solution in this thread. 

[http://ubuntuforums.org/showthread.php?t=782102&highlight=virtualbox&page=2](http://ubuntuforums.org/showthread.php?t=782102&highlight=virtualbox&page=2)

> 
I installed VBox-OSE first (in Hardy Heron) by

sudo apt-get install virtualbox-ose virtualbox-ose-modules-2.6.24-16-generic

followed by

sudo usermod -G vboxusers -a <my name>

This will install VBox-OSE and adjust your kernel.

You can remove it via Synaptic. Don't forget to also delete the hidden file .VitualBox in your home folder.


---

### Post by martin_lindhe on 2008-05-27
In response to your first post.

If you wish to use VirtualBox 1.60 in Hardy, just install the provided .deb from the virtualbox website.

When Hardy updates the kernel, you will need to re-install the .deb, because one step it does is to compile a required kernel module for your current linux kernel.

If you install virtualbox, later upgrade the Ubuntu kernel and later on tries to start VirtualBox and get the following error:

/etc/init.d/vboxdrv: 311: /usr/lib/virtualbox/src/build_in_tmp: not found

Then re-installing the .deb should take care of that for you.

PS. Hardy comes with VirtualBox 1.54 or something.

---

### Post by grumpymole on 2008-06-06
There is a bug in 1.60.  Simple workaround in the [ticket]("http://www.virtualbox.org/ticket/1613").

Cheers

---

