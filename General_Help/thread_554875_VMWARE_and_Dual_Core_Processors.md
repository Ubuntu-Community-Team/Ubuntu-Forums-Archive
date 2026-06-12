---
title: "VMWARE and Dual Core Processors"
date: 2007-09-19
forum: General Help
---

### Post by Scott Olson on 2007-09-19
Hello All,

I have successfully installed the trial version of VMWARE and am currently running a virtual machine on a Windows 2003 server Host Operating System.  The Hardware has two dual cores.

When I review the settings for the virtual machine in the VMWare Server Console, I noticed that I am only allowed to increase the number of CPU's to 2 and not 4.

When I look at task manager (Performance Tab) I find that there are only 2 CPU History Boxes.

Does this mean that VMWare is not recognizing the 2nd core?

Is there a setting that I need to change?

Your help is greatly appreciated.

Cheers,
Scott:mrgreen:

---

### Post by Scott Olson on 2007-09-20
Hello All,

Well, as it turns out, you cannot use more than 2 cpu's without installing the ESX Server.

As such, ESX server sits on "bare metal" (I love that term) and acts as its own operating system.  The performance gains are obvious if it does not sit on top of another OS.

Therefore, I would need another box to install ESX server in order for me to enable multiple cores on the virtual machines.

Cheers,
Scott:popcorn:

---

### Post by fjgaude on 2007-09-21
Thanks, we learn something new every day, eh?

frank
[http://yantrayoga.typepad.com/noname/](http://yantrayoga.typepad.com/noname/)

---

### Post by Doc.Caliban on 2007-09-21
Another excellent bare-metal option is XenExpress.   I learned it from scratch on my own about two weeks ago and now have 4 Dell PowerEdge 2950 quad-cores running 4 virtual servers each.  

-Doc

---

