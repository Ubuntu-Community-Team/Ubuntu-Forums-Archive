---
title: "How to delete or disable Avg scan by command line?"
date: 2013-08-22
forum: General Help
---

### Post by akiNeko on 2013-08-22
Hi all,

I installed Avg scan a few days ago. but I want it Not to start automatically when a computer boots.
I've been search a way to prevent it from launching up automatically or uninstall it but in vain.
Is there any way I can do those?

Thanks in advance.

---

### Post by ian-weisser on 2013-08-22
Uninstalling is very easy. Open Software Center, find the package, and click "uninstall".

Preventing boot operation is also easy, but depends on the startup method.

For example: 
If avg has a startup script in /etc/init.d, use the command **sudo update-rc.d -f avg remove** to eliminate startup operation.
This will properly remove the startup runlevel links...if the script is called 'avg'.
To restore startup operation by recreating the startup runlevel symlinks, use the command **sudo update-rc.d avg defaults**

---

### Post by akiNeko on 2013-08-23
Hi, Thank you. I could mange to uninstalled it. :)

---

