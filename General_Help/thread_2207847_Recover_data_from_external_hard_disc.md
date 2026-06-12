---
title: "Recover data from external hard disc"
date: 2014-02-25
forum: General Help
---

### Post by yafuslae on 2014-02-25
Hello. By error i launch the command **dd if=/dev/zero of=/dev/sd****[SIZE=3]c[/SIZE]**[COLOR=#666666][FONT=Raleway] and the hard disc was _**partially**_ erased. I can't mount this external HDD. 
The data erased is about 5%.
Is there any way to recover the data no erased or [/FONT][/COLOR]provide a file system without erasing the HDD[COLOR=#666666][FONT=Raleway]?
It's important.

[/FONT][/COLOR]

---

### Post by alex2e1gzy on 2014-02-25
You probably need to use parted to recover your partition information. This article has saved my skin a few times: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by westie457 on 2014-02-25
Welcome to the Forum.

Also there is 'Testdisk' available in the repositories
```
sudo apt-get install testdisk
```

See here for info and how-to's.  [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

