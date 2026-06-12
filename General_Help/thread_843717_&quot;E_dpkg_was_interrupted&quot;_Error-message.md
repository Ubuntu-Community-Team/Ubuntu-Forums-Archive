---
title: "&quot;E: dpkg was interrupted&quot; Error-message"
date: 2008-06-28
forum: General Help
---

### Post by DeKosta on 2008-06-28
Hey i controll a dedicated server that now has Ubuntu 8.04 Desktop on it. Newly installed.

I installed updates but something must have happened because now i get:
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."
Whenever i try to install something, or to download the remaining updates.
So i am pretty much stuck.
I have tried writing 'sudo dpkg --configure -a' in the terminal, but nothing.
And 'sudo dpkg --configure -a && sudo apt-get -f install' but nothing there either.
The problem still remains.

I installed the updates through putty and then logged into the desktop with NXclient and saw there were more updates and when i tried downloading i started getting that message.

Now i dont know what to do.
Appreciate the help i can get!

---

### Post by nikgare on 2008-06-28
> I have tried writing 'sudo dpkg --configure -a' in the terminal, but nothing.

What do you mean "nothing"?
Nothing happens, it iodn't work, it throws up some errors or something else that we're all supposed to guess at?

---

### Post by DeKosta on 2008-06-28
> **nikgare said:**
> What do you mean "nothing"?
Nothing happens, it iodn't work, it throws up some errors or something else that we're all supposed to guess at?
Sorry, forgot to write.
This comes up:
```
:~$ sudo dpkg --configure -a
[sudo] password for admin: 
Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Cannot find /lib/modules/2.6.24-16-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: subprocess post-installation script returned error exit status 1

```
And same for: "sudo dpkg --configure -a && sudo apt-get -f install" to.

---

