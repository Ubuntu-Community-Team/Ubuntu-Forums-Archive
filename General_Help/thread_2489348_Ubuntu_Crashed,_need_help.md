---
title: "Ubuntu Crashed, need help"
date: 2023-07-26
forum: General Help
---

### Post by CowDoctor on 2023-07-26
Dear Friends,
Please forgive my lack of experience and skill with Linux.  My older desktop computer just crashed.  Here is the message I am getting:
/dev/sda2: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
            (i.e., without -a or -p options)

BusyBox v1.so.1 (Ubuntu 1:1.30.1-7ubuntu3) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

Due to my inexperience I have not been able to figure out what to do next.  Nothing that I have tried has worked.  Please help, and please be very detailed about what steps to take, as what is obvious to you may not be so to me.
Yours hopefully,
Joe

---

### Post by Bashing-om on 2023-07-26
Hello jjsnyder - Ho-kay :D

The advisory:
> 
/dev/sda2: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.

is very direct. However, how to do so is not.

We need to run that file system check (fsck) - manually.
to do that - the bestest way in my opinion is from a liveUSB.
Hense:
Boot the install USB in the "try ubuntu" mode - that is the "live environment".
Once the desk top loads execute the key combo ctl+t to gain a terminal interface.
Here in this interface run command:
```

sudo fdisk -lu

```
to *know* what the target is for the file system checks/repair. In the output under the "Boot" heading is a star to denote the partition that contains the boot code
Let's presume here that the identified target is "sda1".
Next run terminal command:
```

sudo fsck /dev/sda1

```
for that -simple- file system check/repair.

If it turns out the repair is not simple - please relay what the utility advises.

Restart the system and boot normally.

[INDENT]all good now ?
[/INDENT]

---

### Post by CowDoctor on 2023-07-27
Yes, thank you very much.  Just got it done.  I had to make a boot drive first and there were complications.  It didn't show up exactly as you described, but I was able to muddle through, and will have a better idea what to do if it ever happens again.
Yours most gratefully,
Joe

---

### Post by Bashing-om on 2023-07-27
CowDoctor; Good deal 

Glad things worked out :D

 -together we do -

---

