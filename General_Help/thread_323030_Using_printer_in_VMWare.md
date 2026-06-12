---
title: "Using printer in VMWare"
date: 2006-12-21
forum: General Help
---

### Post by Ariod on 2006-12-21
Hello,

I'm running Windows 2000 under VMWare and I'd like to use printer in it. First, VMWare gave me an error message that I don't have the permission to use /dev/parport0. So I chmodded it to 666. After doing that, VMWare is giving me the following error:
> Parallel port "/dev/parport0" is used by another program (such as another instance of VMware Server) or driver (such as lp).
Virtual device parallel0 will start disconnected.

What can I do?

---

### Post by Alterax on 2007-10-02
If the printer you have attached to it is being used for your Linux system, then it's absolutely right.  You can't directly connect it to the parallel port.   Not to worry.

What you need to do is share the printer on your Linux box.  The Windows 2000 Virtual box should be set up to connect to the Linux box via the network (it's easier to think of them as two different machines).

Then when you want to print in Windows, print to the networked printer on the Linux box.

---

### Post by dabl on 2007-10-02
Samba is a decent way to share printers and files with a VMWare Player Windows guest on your Linux system.  :)

---

