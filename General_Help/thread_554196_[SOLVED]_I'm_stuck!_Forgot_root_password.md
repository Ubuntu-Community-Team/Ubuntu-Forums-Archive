---
title: "[SOLVED] I'm stuck! Forgot root password"
date: 2007-09-18
forum: General Help
---

### Post by mlanza on 2007-09-18
I'm going crazy here!!!!  I've spent 2 days rebuilding a partitioned PC with Windows and Ubuntu.  I changed my ubuntu root password a couple times and now I can't seem to remember it.  I've spent 3 hours trying various combinations and trying to reset it.  Please, please, please help.  I've read the threads and keep getting stuck.

For example, when I try to boot GRUB in single user mode eventually during the boot I'm prompted for my root password.  So this doesn't work.

Then I tried booting from the Ubuntu live CD and modifying the /etc/passwd and /etc/shadow files according to: [http://www.linuxcompatible.org/thread28427-1.html](http://www.linuxcompatible.org/thread28427-1.html)

I've tried other variations, nothing works.

If I'm changing /etc/passwd and /etc/shadow, essentially blanking out the password, from where is it getting this password info?  I can't understand how it seems to be retaining some password other than "blank" when I've blanked out the "root" password.

When I type "passwd root" it tells me I don't have rights.  When I type "sudo passwd root" it prompts me for a password.

Please enlighten me!!  I am presently unable to use my PC and I have work to do.

Thanks.
Mario

---

### Post by garba on 2007-09-18
boot the live cd, mount your root partition and then chroot into it, you now have a root console, type passwd and that's it

---

### Post by mlanza on 2007-09-18
Wow! That was quick. 

Actually, 30 seconds later I tried something that easily worked.  I booted into "Recovery Mode".  I was able to reset the password here.

Thanks for the quick reply.

---

### Post by K.Mandla on 2007-09-18
Moving to General Help.

---

