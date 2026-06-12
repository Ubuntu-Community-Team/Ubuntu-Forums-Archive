---
title: "Ubuntu not letting me log in"
date: 2007-06-20
forum: General Help
---

### Post by iamlost on 2007-06-20
Hi,
I booted up my Ubuntu install on my dual boot laptop today and it seemed to boot fine, but when i got to the login screen, i put in my details and then it showed me a screen saying something about GDM and it something about it possibly something to do with the drive being full then reset the computer. Is there any solution to this problem.

---

### Post by meatpan on 2007-06-20
Some of the error message details are useful for debugging the problem.  Can you run the boot/login process again, record the error messages, and post them?

---

### Post by taurus on 2007-06-20
Boot into recovery mode from GRUB menu and clean up the archives, freeing up some space.

```
aptitude clean
df -h
```

---

### Post by iamlost on 2007-06-20
The error message was as follows 'GDM could not write to your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case it is not possible to log in.'

---

