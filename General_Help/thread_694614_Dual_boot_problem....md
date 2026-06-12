---
title: "Dual boot problem..."
date: 2008-02-12
forum: General Help
---

### Post by Moonfrost on 2008-02-12
Well, I was dual booting Ubuntu 7.10 with Windows XP for at least a month with no problems when all of a sudden I needed to use Windows yesterday so I turned on the computer and Windows is not in the grub list anymore...anyone know what could've happened? I didn't modify anything at all lately and I tried restaring the computer several times to see if it got fixed but nothing...I can't access Windows...can anyone help please?

---

### Post by logos34 on 2008-02-12
Here's [one possiblility]("http://users.bigpond.net.au/hermanzone/p15.htm"):

> 1) Paste your Windows entry above the beginning of the debian automagic kernels list
You can cut the entire Windows entry from where it is under the end of the automagic kernels list and paste it above the beginning of the automagic kernels list.
 Above this line: ### BEGIN AUTOMAGIC KERNELS LIST   

**What NOT to do-  don't paste your Windows entry anywhere inside the automagic kernels list because it will be deleted when you have a kernel update in Ubuntu**.

Or put it below the '### END DEBIAN AUTOMAGIC KERNELS LIST' line

---

### Post by apetresc on 2008-02-12
Here's what needs to be added to menu.lst:
```
title Microsoft Windows XP Home Edition
root (hd0,1)
makeactive
chainloader +1
```
(Except replace (hd0,1) with whatever is correct, of course).

Like logos34 said, make sure you don't put it in the middle of Debian's list :)

---

### Post by Moonfrost on 2008-02-12
> **AdrianP said:**
> Here's what needs to be added to menu.lst:
```
title Microsoft Windows XP Home Edition
root (hd0,1)
makeactive
chainloader +1
```
(Except replace (hd0,1) with whatever is correct, of course).

Like logos34 said, make sure you don't put it in the middle of Debian's list :)

Yeah I already knew that, I just moved it to where logos34  suggested...thanks a lot!

---

### Post by Moonfrost on 2008-02-12
> **logos34 said:**
> Here's [one possiblility]("http://users.bigpond.net.au/hermanzone/p15.htm"):



Or put it below the '### END DEBIAN AUTOMAGIC KERNELS LIST' line

Thanks, I put it under ### END DEBIAN AUTOMAGIC KERNELS LIST### and it worked, I hope it doesn't disappear again...thanks for your help.

---

