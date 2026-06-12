---
title: "Ubuntu on Virtual Machine on Windows Domain Host"
date: 2013-05-05
forum: General Help
---

### Post by DextrousDave on 2013-05-05
Hi All

I am running Ubuntu on VMWare, and the VMWare is installed on a Windows 7 Enterprise machine that is on a Windows domain. My question is:

Will the administrator of the domain be able to track any of the activity on the Ubuntu OS? Is there a way for the administrator of the Windows domain to get access to my Ubuntu OS in any way?

Thank you

---

### Post by Cheesemill on 2013-05-05
Any network activity from the VM such as websites you visit and emails you send can easily be monitored and the OS that it's running can be discovered.

It *shouldn't* be possible to see what's on the VM or gain control of it though.

---

### Post by DextrousDave on 2013-05-06
Yes I agree with the network traffic, just wasn't sure about actual activity on the OS itself, and personal files and folders

---

### Post by Mark Phelps on 2013-05-06
I can only pass along concerns based on my previous employer -- but, using a "work" machine (which is likely here, since the PC is connected to a Domain) and trying to "hide" your activities from the domain admins -- was cause for immediate termination! 

Also, even if it was not a "work" machine, trying to "hide" activities was still grounds for immediate termination.

So, you need to realize that you could be risking your job just to mess around with Ubuntu.  Just be aware of that.

---

### Post by DextrousDave on 2013-05-13
thank you Mark, I agree with you. Best to just be safe and mess around on my own personal computer

---

