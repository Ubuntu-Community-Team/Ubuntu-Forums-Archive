---
title: "I can not bring up the grub menu in AMD64 -14.04"
date: 2015-09-23
forum: General Help
---

### Post by Robbyx on 2015-09-23
I have tried various ways of pressing the shift key with no success. Assuming the normal pathways into the grub menu is corrupted how should I access it on startup. I want to run fsck on the main system partitions.

---

### Post by Bashing-om on 2015-09-23
Robbyx; Hi !

Is this an UEFI system ? Then it is the escape key that grub recognizes.

As to:
> 
 I want to run fsck on the main system partitions.


One MUST run file system checks when the file system(s) are NOT mounted.
A quicky can be enabled from terminal :
```

sudo touch /forcefsck
sudo shutdown -r now

```
Which will reset the fsck flag for the file system check to be run at next boot. The 'shutdown' command to reboot and have the check to run.
Comprehensive file system checks are run from a live environment, such as a liveDVD .

[INDENT][INDENT][INDENT]hope this helps
[/INDENT][/INDENT][/INDENT]

---

### Post by Robbyx on 2015-09-23
Thank you. Both of your answers were very helpful.

---

### Post by Bashing-om on 2015-09-23
Robbyx; Hey, hey ...

We try and help. IF enough information has been supplied to answer the question, please mark this thread solved ( thread tools drop down menu ) .

Else, we do continue until such time you are satisfied .

[INDENT][INDENT]we do do this
[/INDENT][/INDENT]

---

