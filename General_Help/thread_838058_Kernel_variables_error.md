---
title: "Kernel variables error"
date: 2008-06-23
forum: General Help
---

### Post by leep on 2008-06-23
After the upgrade to the last version, everytime I switch on my pc, during the boot process, I obtain this error:

```
Loading Kernel variables:
error: 'vm.mmap_mn_addr' is an unkonwn key [FAIL]
```

Once loaded, the pc works perfectly, just a little bit slower than before. Any idea about what the error means, and how to fix it?
Thank you in advance,
Simone

---

### Post by sdennie on 2008-06-23
That error shouldn't make the PC run any slower at all.  I'm not sure why you'd suddenly start getting it but, you can edit /etc/sysctl.conf and remove the option if the error is bothering you:

```

gksudo gedit /etc/sysctl.conf

```

Then find the line that has "vm.mmap_mn_addr" and put a "#" in front of it.

---

### Post by leep on 2008-06-23
Did what you wrote, but I'm unable to find a line containing that key. It's really a mistery to me. Thank you for your reply.

---

### Post by sdennie on 2008-06-23
Wait, I think I see the problem.  It should be mmap_min_addr and not mmap_mn_addr.  What is the output of:

```

grep mmap /etc/sysctl.log

```

---

### Post by leep on 2008-06-23
```
simone@hs01:~$ grep mmap /etc/sysctl.log
grep: /etc/sysctl.log: Nessun file o directory
```

"No file or directory".

---

### Post by sdennie on 2008-06-23
I mistyped there.  It should have been:

```

grep mmap /etc/sysctl.conf

```

---

### Post by leep on 2008-06-23
Here I am:

```
# protect bottom 64k of memory from mmap to prevent NULL-dereference
vm.mmap_min_addr = 65536

```

Sorry, but I'm a totally noob.

---

