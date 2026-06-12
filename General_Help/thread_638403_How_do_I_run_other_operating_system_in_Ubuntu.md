---
title: "How do I run other operating system in Ubuntu?"
date: 2007-12-12
forum: General Help
---

### Post by ardchoille42 on 2007-12-12
I have heard that you can run other operating system, and other Linux distros, within Ubuntu. Is that true? If so, how is that done? What do I need to install or set up?

---

### Post by .nedberg on 2007-12-12
Install VMWare Player, VMWare Server or Virtualbox. They can all run different OS's. Player doesn't let you make new virtual machines though.

---

### Post by ardchoille42 on 2007-12-12
> **.nedberg said:**
> Install VMWare Player, VMWare Server or Virtualbox. They can all run different OS's. Player doesn't let you make new virtual machines though.

Thank you very much.

---

### Post by c0mp13371331337 on 2007-12-12
Aside from compatibility layers such as Wine, it is possible to run an entire operating system within Ubuntu (Or most any OS for that matter) with the help of a Virtual Machine.

I spent some time using VMWare, which was okay, but VirtualBox integrates a bit tighter with gnome and has just as many bells and whistles as the free ($) version of VMWare.

```
sudo apt-get install virtualbox
```

Make sure to enable Universe and Multiverse repos if you haven't already, just in case.

Once you've got that installed, you'll want to create a new virtual machine, then turn it on, making sure that you've mounted the installation directory of whatever distro you're looking to install (you can even mount .iso images without burning to CD first).  After the media's been mounted, just configure the virtual machine to boot from that media, and assuming it's the correct, OS-install type media, it will go through the boot/install in the VirtualBox window as if you were booting up a computer.

---

### Post by ardchoille42 on 2007-12-12
> **c0mp13371331337 said:**
> Aside from compatibility layers such as Wine, it is possible to run an entire operating system within Ubuntu (Or most any OS for that matter) with the help of a Virtual Machine.

I spent some time using VMWare, which was okay, but VirtualBox integrates a bit tighter with gnome and has just as many bells and whistles as the free ($) version of VMWare.

```
sudo apt-get install virtualbox
```

Make sure to enable Universe and Multiverse repos if you haven't already, just in case.

Once you've got that installed, you'll want to create a new virtual machine, then turn it on, making sure that you've mounted the installation directory of whatever distro you're looking to install (you can even mount .iso images without burning to CD first).  After the media's been mounted, just configure the virtual machine to boot from that media, and assuming it's the correct, OS-install type media, it will go through the boot/install in the VirtualBox window as if you were booting up a computer.

Wow, thank you for the information :)

---

### Post by slimx3m on 2007-12-12
is there a way where i could open my windows from a different partition in ubuntu?
i don't think so, but any ideas???

because i know that after install VMware i could install another OS and run it from there, but how about if i would like to call an existing OS in a different partition, is that even possible?

---

### Post by fjgaude on 2007-12-12
If, for example, you install Ubuntu, then VMware, and then WindowsXP in  VMware, you have at your sight Ubuntu and anything Ubuntu is connected to, through other partitions, and even down a LAN or WAN. Amazing.

---

### Post by slimx3m on 2007-12-13
so, if i had Ubuntu installed and MS XP also... whenever i make my VMware i could not call that XP from a different partition because it is not a existing VM?!  is that right???

---

### Post by Zipster90 on 2007-12-13
I'll verify the other poster's recommendations of Virtualbox. On my machine, it seems that Virtualbox is way faster than anything I've used from VMWare, and it's also ridiculously easy to set up. The only real tweaking you have to do is give you user account permission to use the vboxusers group and you're done. I love it.

---

### Post by eriqjaffe on 2007-12-13
> **slimx3m said:**
> so, if i had Ubuntu installed and MS XP also... whenever i make my VMware i could not call that XP from a different partition because it is not a existing VM?!  is that right???Actually, it is possible to have a virtual machine point to an XP install on another physical partition.  I've done it myself.

[http://advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

...those directions are for VMWare Player, however.  Not sure about VirtualBox.

---

### Post by fjgaude on 2007-12-13
> **slimx3m said:**
> so, if i had Ubuntu installed and MS XP also... whenever i make my VMware i could not call that XP from a different partition because it is not a existing VM?!  is that right???

From within VMware you can access any files on any partition on your system, seeing all in windows that you size to fix your needs.

The easiest way I've found is to install Windows into the VMware Server after VMware has been installed. Such gives you complete control over both Ubuntu and Windows. All files are accessable from either OS. And it is fast, quick, full-featured.

---

### Post by Flare183 on 2007-12-13
VMWare Player or Virtual Box are your best bets. But the only way to create a VM without the VMWare Server is to use this: [http://www.easyvmx.com/]("http://www.easyvmx.com/").


But in Virtualbox you can them files without that website.

---

### Post by fjgaude on 2007-12-13
Gosh, VMware server is free and you get it through Synaptic. You get an eternal license from vmware web site... for me it has been the best of all options.

---

### Post by slimx3m on 2007-12-13
> **eriqjaffe said:**
> Actually, it is possible to have a virtual machine point to an XP install on another physical partition.  I've done it myself.

[http://advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

...those directions are for VMWare Player, however.  Not sure about VirtualBox.

thnx, i will give a try to this

---

### Post by slimx3m on 2007-12-13
> **fjgaude said:**
> From within VMware you can access any files on any partition on your system, seeing all in windows that you size to fix your needs.

The easiest way I've found is to install Windows into the VMware Server after VMware has been installed. Such gives you complete control over both Ubuntu and Windows. All files are accessable from either OS. And it is fast, quick, full-featured.

thnx for the info.  but i already know that.  what i was trying to do is to have a VM calling an existing OS on a different partition.  and again, than for your help and info.

---

### Post by HermanAB on 2007-12-13
Note that with VMware, you can also convert a Windows based machine from a physical to a virtual machine and back again: [http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)

which is sometimes a handy trick.

Cheers,

Herman

---

### Post by slimx3m on 2007-12-14
> Note that with VMware, you can also convert a Windows based machine from a physical to a virtual machine and back again: [http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)

which is sometimes a handy trick.

Cheers,

Herman

yeah, i saw that.  but i guess that if you are going to convert something it could only be windows, because that is the only app that they have there.

---

