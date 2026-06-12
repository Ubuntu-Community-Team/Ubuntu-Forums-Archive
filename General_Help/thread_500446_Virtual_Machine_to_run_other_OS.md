---
title: "Virtual Machine to run other OS?"
date: 2007-07-13
forum: General Help
---

### Post by enlightening on 2007-07-13
I came across this on cnet   [http://news.com.com/2100-7344_3-6176175.html](http://news.com.com/2100-7344_3-6176175.html)     I was drawn in by the virtulaizatoin abilities, I am interested on running XP and LInux (I believe at the same time (not sure)), as of right now I dual boot, so this would be interesting to get to work.  How would I go about virtualizing another OS?
If this is in fact possible, any input would be appreciated.

Thanks

---

### Post by dfego on 2007-07-13
It's certainly possible.  Some popular software for virtualization are [VirtualBox]("http://www.virtualbox.org/") and [VMWare]("http://vmware.com/").  I've recently been using VirtualBox extensively, and can vouch for it being an excellent program, even though it can be a bit shaky sometimes.  Not to mention it has an open source version. :)

Now, in order for virtualizatoin to work *well*, you'll have to have the appropriate hardware.  If you happen to have a newer Intel processor with built-in virtualization extensions, you're set.  If you don't, you very well still might be able to use it, but it won't run quite as well.  The key to remember is that you would be running two full operating systems at the same time, so you need to have enough resources (processor cycles, RAM, hard disk space, etc.) for both.

---

### Post by HermanAB on 2007-07-14
If you have never used virtual machines before, then I suggest that you start off with the free VMware Server.  It is mostly pain free to install and it works really well, with any client OS.

Once you have fooled around a bit, try Qemu (Virtualbox), Xen and others.  Each has its strong and weak points.  VMware is sloooow (about half native speed), but it always works and provided that you have a modern machine, it is OK.  The others can beat VMware in the speed department, when they happen to work.

What I like about virtualization is that it makes it very easy to test things.  I have basic installations of WinXP, Win2003, RHEL5, Mandriva 2007, Ubuntu and others and can make a copy of one of those, then install and experiment with stuff till it breaks - delete the image and start over, or go back to a previous version that I saved a few hours before.  Restoring an image from a DVD just takes a few minutes, versus one or two hours to install a machine from scratch.  The time saving is huge.

On a garden variety 2 to 3GHz machine with 1 to 2GB RAM, you can run several virtual machines at the same time, each with 384MB RAM allocated to it, so you can really go nuts with client and server setups, without having a big lab full of machines.  You can also download pre-installed 'appliances' from the VMware web site - these are simply tarballs of a VMware directory, and that way you can play with programs that are otherwise very difficult to install, like CRM, Email and Spam filters and then you can pick the one you like and deploy it in the blink of an eye, instead of spending days scratching your head trying to get the damn thing to go.

'Hope that helps!

Herman

---

### Post by enlightening on 2007-07-14
thanks for your help, I'll give the programs a try and hopefully it will work as I expect.

---

### Post by jespdj on 2007-07-14
I am running Ubuntu 7.04 (64-bit) and I have installed VMWare Server with the instructions here: [How to install Vmware server From Canonical commercial repository in Ubuntu Feisty](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html).

I have installed Windows XP Home Edition in a virtual machine in VMWare and it works really well - in full screen mode, you don't even notice that it's running in a virtual machine.

The only thing that does not work really well is 3D graphics. When Win XP runs inside the VM, it uses VMWare device drivers. The VMWare graphics driver does support accelerated graphics, but not full 3D graphics acceleration.

For most software this is no problem, but Windows games that need complete 3D graphics support it is probably not going to work well.

---

### Post by M$LOL on 2007-07-14
Virtualbox is awesome. I just installed it in 64bit Feisty, and Windows 2K installed in ten minutes.

---

