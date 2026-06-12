---
title: "openoffice does not work anymore"
date: 2007-10-18
forum: General Help
---

### Post by PsychedelicReaction on 2007-10-18
```
ziggy@stardust:~$ openoffice 
ziggy@stardust:~$ X-Error: BadAlloc (insufficient resources for operation)
        Major opcode: 53 (X_CreatePixmap)
        Resource ID:  0x4c00117
        Serial No:    2159 (2159)
These errors are reported asynchronously,
set environment variable SAL_SYNCHRONIZE to 1 to help debugging
```

that's what happens when i start openoffice writer. all the others components work fine.
any suggestion? i tried to install it again...

---

### Post by r-mo on 2007-10-18
try deleting the .openoffice.org2 directory in your home.  ctrl+h to see it in nautilus.

---

### Post by jsidew on 2007-10-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/153659](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/153659) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm on Gutsy too and having the same problem.
i deleted .openoffice.org2 folder in home dir, but the problem remains

can anyone suggests something else?

thank you.

---

