---
title: "add/remove hardware busted..."
date: 2007-04-09
forum: General Help
---

### Post by FatCake on 2007-04-09
So I was going to install the VMware Player and the install froze and I was forced to restart my computer. I go to use add/remove hardware again and it gives me the message: 

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. "

So I go into terminal and type out "dpgk --configure -a" and it tells me that I need to be the super user to do something like this. 

Im really new to ubuntu and I just dont know what I need to do...

---

### Post by Maestro23 on 2007-04-09
You need "sudo" in front of your command.

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by FatCake on 2007-04-09
Problem solved. Thanks!

---

