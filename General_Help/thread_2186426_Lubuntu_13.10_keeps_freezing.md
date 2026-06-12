---
title: "Lubuntu 13.10 keeps freezing"
date: 2013-11-07
forum: General Help
---

### Post by nickkrause on 2013-11-07
I have tried testing the ram and it was fine in addition , I also installed the ati driver but it keeps freezing at random and I just turned my ram to 1600mhz but I doubt that will help.
Every few days it keeps freezing and needing a hard reboot this has been there forever since lubuntu 12.04 and is very annoying.

---

### Post by Erik1984 on 2013-11-07
You could look in the log files for 'suspicious' messages. When I had freezing problems HDD related errors popped up in the file /var/log/kern.log

---

### Post by philinux on 2013-11-07
Also look at x errors.

```
cat ~/.xsession-errors | pastebinit
```

Post back with the link created.

---

### Post by nickkrause on 2013-11-07
Script for cjkv started at run_im.
Script for default started at run_im.
Here is that file.

---

### Post by nickkrause on 2013-11-07
udisks just crashed weird ...

---

### Post by nickkrause on 2013-11-07
1.354337] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20130517/psargs-359)
this turns up in the file you asked me to check

---

### Post by raja.genupula on 2013-11-07
This will tell you more : [http://askubuntu.com/questions/4408/what-should-i-do-when-ubuntu-freezes](http://askubuntu.com/questions/4408/what-should-i-do-when-ubuntu-freezes)

---

### Post by philinux on 2013-11-07
> **nickkrause said:**
> 1.354337] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20130517/psargs-359)
this turns up in the file you asked me to check


Could this be a uefi problem. some bios setting or other. What's the motherboard make and model?

---

### Post by ibjsb4 on 2013-11-07
Bug related?

[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/551654](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/551654)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1093541](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1093541)

[https://lists.launchpad.net/kernel-packages/msg04087.html](https://lists.launchpad.net/kernel-packages/msg04087.html)

---

### Post by nickkrause on 2013-11-07
I have installed linux mint and it is still giving me the error , about freezing and am starting to get very annoyed

---

### Post by nickkrause on 2013-11-07
I have just reseated the graphics and in addition installed linux mint will report if a problem is still there

---

### Post by nickkrause on 2013-11-08
I have just reseated the graphics card will see if it works

---

### Post by nickkrause on 2013-11-11
Still happens and have just reseated and cleaned my graphics card as there is dirt in it so it can't be hardware

---

