---
title: "Running UBUNTU in under Microsoft Virtual Server (or VMWare)"
date: 2007-05-23
forum: General Help
---

### Post by nyannios on 2007-05-23
I am trying to run Ubuntu desktop under a virtual machine (under Microsoft Virtual Server).  I can start the install in safe graphics mode, but can't get it to recognize the mouse.  At that point, I can not do anything. Has anyone attempted this and gotten it to recognize the mouse and keyboard?

Thanks
Nikos

---

### Post by Princey on 2007-05-23
> **nyannios said:**
> I am trying to run Ubuntu desktop under a virtual machine (under Microsoft Virtual Server).  I can start the install in safe graphics mode, but can't get it to recognize the mouse.  At that point, I can not do anything. Has anyone attempted this and gotten it to recognize the mouse and keyboard?

Thanks
Nikos

Microsoft server has limited support for Linux and Ubuntu in general. You'd do better with vmware. The server download is free, though you have to register. Registration is free.

---

### Post by gg234 on 2007-05-23
I would suggest use vmware it is very easy to install and check this nice [installation guide]("http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html")

---

### Post by cknight725 on 2007-06-25
I had a similar problem with Virtual Server 2005.  The fix is frustratingly simple:

1. Boot from Ubuntu’s install CD
2. Press F4, then choose “1024×768 16&#8243;
3. Then press F6, and at the end of the line add this: text vga=0×314

---

