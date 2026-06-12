---
title: "segmentation fault"
date: 2007-05-29
forum: General Help
---

### Post by dracule on 2007-05-29
I just installed wubi, and now get a segmentation fault error when booting, never gets past the text part...

here is my windows setup:
300gb C:/
20Gb D:/(with windows on it)

so i was wondering since windows is installed on the D:/ instead of C if that would cause this problem.

---

### Post by ago on 2007-05-29
can you please provide detailed error information?

---

### Post by dracule on 2007-05-29
well, its basically during the boot sequence (when its all text)and it stops with this line

"[    25.894958]   Segmentation fault"

---

### Post by ago on 2007-05-29
Looks like a kernel crash. Is that after "Loading please wait..." line? Is this on first reboot or after installation? Did you try with the live CD? Can you provide a couple more lines?

---

### Post by dracule on 2007-05-29
this is right after installation. the line before it is EIP: [<e086e625>] sis_init_one+0x75/0x3c0 [pata_sis] SS:ESP 0068: df947e0c

---

### Post by ago on 2007-05-29
> **dracule said:**
> this is right after installation.

That is a bit vague. Do you mean after installation is completed (you see a lot of blue screens with red progressbars) or soon after the windows is rebooted? Please try the live CD and see if you have the same issue. If that also fails your hardware might not be compatible with current kernel.

---

### Post by andy graham on 2007-06-02
Please Help!!!

i have the same problem. its ater ive installed it and wen i reboot and my choice comes up whether i wnt to load windows or ubuntu, i click ubuntu and then this error comes up. 
PLEASE HELLp! i really dnt kno nething about ubuntu and am not even that experience to know what the error mean. Pleas help itd b much appreciated.

i have a live cd butt i dnt kno hw 2 dual boot either.lol

---

