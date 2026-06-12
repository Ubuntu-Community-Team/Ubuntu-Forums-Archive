---
title: "How to boot into an older kernel on Mac iBook G4"
date: 2014-01-04
forum: General Help
---

### Post by rdh61 on 2014-01-04
Anyone know how to boot into an older kernel on a Mac iBook G4? 

  
I know I have 2 kernels installed, but there is no menu to choose boot options from as I only have one OS installed (Ubuntu).

  
Thank you.

---

### Post by Bucky Ball on 2014-01-04
You should still be able to get to the menu list at boot. Try hitting escape or shift at boot or just after.

---

### Post by rdh61 on 2014-01-05
Thanks for your reply. Unfortunately neither esc or shift produced the menu. I tried with each, pressing them intermittently from when I powered on until the log in screen appeared. The only effect was when pressing esc I got a "quiet boot" (no splash).

---

### Post by Bucky Ball on 2014-01-05
How old are the kernels? Which release, if you remember? 

Depending, boot to Ubuntu, open a terminal and:

```
sudo nano /etc/default/grub
```

Find these lines and make them look like this:

```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
```

Reboot. Anything?

---

### Post by rdh61 on 2014-01-06
Kernel versions 3.11.0-3 and 3.11.0-4 for powerpc.

There is no /etc/default/grub file.

I guess I should install grub, right? How?

Thanks.

---

### Post by jeanjd63 on 2014-01-06
Hello,
Maybe you have a old version of grub. 
Try to edit file menu.lst :
sudo  gedit  /boot/grub/menu.lst

If it is ok you modifie :

> 
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
**timeout		X**



## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
**hiddenmenu**

By :
> 
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
**timeout		10**


## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
**## hiddenmenu**

You save and do a :
[B]sudo  update-grub

[/B]Bye

---

### Post by Bucky Ball on 2014-01-06
With a kernel that recent don't think old grub, but definitely worth a try, just in case.

Do you also have a Mac OS on this machine? That could be using Boot Camp to boot and not grub, but you should still be able to find the /grub config file in Ubuntu in one of the two places given so far.

---

### Post by rdh61 on 2014-01-06
Hmm...

No /boot/grub directory either...

No Mac OS or any other OS installed, only Ubuntu.

---

