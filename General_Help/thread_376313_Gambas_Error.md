---
title: "Gambas Error"
date: 2007-03-04
forum: General Help
---

### Post by onomus on 2007-03-04
I'm running Ubuntu Edgy 6.10. 

When I try to test run a program in gambas I get the following error:

```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

When I googled the error I found that this error is common for more than one application. 

Thanks,

-Onomus

---

### Post by caldevil on 2007-03-04
Well that error is due to extra devices added in xorg.conf for tablet PC and it is completely innocuous.

---

### Post by onomus on 2007-03-05
That's odd. So I should just remove the line?

---

