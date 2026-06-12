---
title: "sudo kate freezing"
date: 2006-11-21
forum: General Help
---

### Post by Ariliand on 2006-11-21
Hello, forums.

I get the following error whenever I try to run kate using sudo:

> 
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0
DCOP aborting call from 'anonymous-5921' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
Loading kconfig Config module ...
Creating backend ...
ERROR: could not open init.scm (errobj No such file or directory)

*backtrace*
>>(require "init.scm")
>>(*catch (quote errobj) (require "init.scm"))
>>(eq? (quote *init.scm-loaded*) (*catch (quote errobj) (require "init.scm")))

ERROR: unbound variable (errobj create-context)

*backtrace*
>>(create-context 0 (quote ()) (quote ()))

Loading socket FrontEnd module ...
Starting SCIM as daemon ...
  


...and then it freezes.

I tried to install SKIM recently, following this guide:

[https://help.ubuntu.com/community/SCIM/Kubuntu?action=show](https://help.ubuntu.com/community/SCIM/Kubuntu?action=show)

I think the error might be related, any help would be greatly appreciated.

Thanks.

---

### Post by aysiu on 2006-11-21
Have you tried this instead? ```
kdesu kate
```

---

### Post by Ariliand on 2006-11-21
Well, of course. Skim has been giving me so much trouble lately that I assumed it was at fault.

Thanks a lot.

---

### Post by aysiu on 2006-11-21
> **Ariliand said:**
> Well, of course. Skim has been giving me so much trouble lately that I assumed it was at fault.

Thanks a lot.
Read more here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

