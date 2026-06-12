---
title: "Ubuntu 15.10 suspend question"
date: 2016-03-12
forum: General Help
---

### Post by ra7411 on 2016-03-12
I have both Ubuntu 15.10   and Studio installed on the same hard disk. I mostly use  the Ubuntu install. It would be handy if when I restart Ubuntu from suspend,  if it would give the option of choosing between Ubuntu and Studio - it does that when coming out if a shutdown or restart but not when starting up from a suspend.


 Is there any way of setting things up so that Ubuntu will give a choice between the  two operating systems when coming out of suspend?

---

### Post by Bucky Ball on 2016-03-12
In short, none that I know of. To perform the action, even if you did manage to get a menu up, the machine would need to shutdown/restart to boot into the other install ...

Suspend doesn't work the way you are hoping it might. 

You could run one as a virtual machine guest in Virtualbox with the other as host, i.e. in Ubuntu, install Virtualbox, run UStudio as a virtual machine. That way you can access either whenever.

---

### Post by sandyd on 2016-03-12
> **ra7411 said:**
> I have both Ubuntu 15.10   and Studio installed on the same hard disk. I mostly use  the Ubuntu install. It would be handy if when I restart Ubuntu from suspend,  if it would give the option of choosing between Ubuntu and Studio - it does that when coming out if a shutdown or restart but not when starting up from a suspend.


 Is there any way of setting things up so that Ubuntu will give a choice between the  two operating systems when coming out of suspend?

If you want, you can use hibernation instead of suspend.

However, you will need two swap partitions that are **minimum** the size of your computer's RAM. You must have two because if one OS hibernates, and the other OS starts up and tries to use the swap partition that the first OS has stored its RAM to, bad things will likely happen.

---

### Post by Bucky Ball on 2016-03-12
Interesting. Could you elaborate further on a method of coming out of suspend/hibernate and having the option of booting either of two installs please, sandyd?

---

### Post by sammiev on 2016-03-12
> **Bucky Ball said:**
> Interesting. Could you elaborate further on a method of coming out of suspend/hibernate and having the option of booting either of two installs, sandyd?

+1 At times this could be very handy.

Have to add myself to this thread.

---

### Post by sandyd on 2016-03-14
> **Bucky Ball said:**
> Interesting. Could you elaborate further on a method of coming out of suspend/hibernate and having the option of booting either of two installs please, sandyd?

Hibernation requires that you boot up into the OS before the OS restores the RAM from swap. The computer at this time is off, so you will begin the same process when starting as if it were a cold boot. As a result, you can choose the OS at the grub menu before booting into either OS.

---

### Post by HermanAB on 2016-03-14
You need to log out, then suspend if you want the option to switch desktops.  

However, it is perfectly possible to switch user and log in a second time as someone else with a different desktop and toggle between them on the fly, because Linux is a multi-user OS.  That would require you to set up a documents directory with a sticky group so that both of your user accounts can access the same shared data.

---

