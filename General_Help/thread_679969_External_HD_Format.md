---
title: "External HD Format"
date: 2008-01-27
forum: General Help
---

### Post by haelen on 2008-01-27
I've been trying to move some data onto an external HD which was formatted on a Mac.

It does have external read write permissions, but my system cannot write to it.

Is there a workaround for this?

TIA,
Tim

---

### Post by wolfen69 on 2008-01-27
boot up live cd.
open terminal.
```
sudo su
```
```
gparted
```
then reformat

---

### Post by FRuMMaGe on 2008-01-27
I have my external HD formatted to reiserfs. it's a great file system for Linux PC's

However, if you want to be able to transfer your data between OS's, your best bet is good ol' FAT32

---

### Post by haelen on 2008-01-27
Hey. Thanks for the prompt r esponse.

I have Gparted on my machine.

Will the Mac be able to read / write data from the HD once done?

---

### Post by FRuMMaGe on 2008-01-27
> **haelen said:**
> Hey. Thanks for the prompt r esponse.

I have Gparted on my machine.

Will the Mac be able to read / write data from the HD once done?

Yes. So long as you format it to a file system that the mac understands :)

---

### Post by haelen on 2008-01-27
> your best bet is good ol' FAT32

Works fine!

Thanks,
Tim

---

### Post by FRuMMaGe on 2008-01-27
> **haelen said:**
> Works fine!

Thanks,
Tim

Sure :)

---

