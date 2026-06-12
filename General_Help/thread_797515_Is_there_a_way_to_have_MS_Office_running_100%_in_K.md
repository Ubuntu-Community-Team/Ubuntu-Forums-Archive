---
title: "Is there a way to have MS Office running 100% in Kubuntu ?"
date: 2008-05-17
forum: General Help
---

### Post by alquimista on 2008-05-17
Hi,

I have MS Office XP, and I need it for my work and to communicate clients. I installed CorssOver office last version; Outlook runs ok, but Word crashes from time and is annoying. Is there a way to have MS Office running 100% in my Kubuntu box? I really would not like to leave Kubuntu because of MS Office problems...

BTW, I know Open Office, but unfortunately it lacks of some functionality I require and already have in MS Office.

I run Kubuntu 7.10 on a Toshiba Satellite A60

Thank you,
Guillermo

---

### Post by lswest on 2008-05-17
you could install XP into a virtual machine (i recommend VirtualBox from [www.virtualbox.org](www.virtualbox.org) ) and then you can choose "seamless mode" (after installing the vbox addons) and have office (seemingly) running in Kubuntu.  Probably your best bet, or to set up a more complex system using ssh and vnc tunneling and vmware server.

---

### Post by Victormd on 2008-05-17
I have MS Word, Excel, and Powerpoint all running with WINE. I wouldn't try to run Outlook, instead, try Evolution. I haven't used them extensively but from what I have used, they work very well.

---

### Post by Monicker on 2008-05-17
You could create a Windows virtual machine (Virtual Box or VMWare), and run MS Office from there.  Use a shared folder to share documents between the vm and the linux host.

---

### Post by TuxLove on 2008-05-19
Yeah, use VirtualBox. There's a good installation tutorial here:
[http://blogs.pcworld.co.nz/pcworld/tux-love/2008/04/hidden_linux_virtualbox.html](http://blogs.pcworld.co.nz/pcworld/tux-love/2008/04/hidden_linux_virtualbox.html)

---

