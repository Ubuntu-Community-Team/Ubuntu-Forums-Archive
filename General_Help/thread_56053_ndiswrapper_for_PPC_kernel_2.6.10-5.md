---
title: "ndiswrapper for PPC kernel 2.6.10-5"
date: 2005-08-11
forum: General Help
---

### Post by ru55 on 2005-08-11
hi all ! 

i'm trying to find a working ndiswrapper for PPC chipset but until now 
i couldn't find any 
i've an ibook G4 running ubuntu everything works fantastic (except for the ole broadcom wlan shit ) anyway 
i tried to install the latest ndiswrapper source and it brings an error 
 
here's a copy, i don't post everything because the list is too long and the errors are all the same upward .

> 
.......
/opt/ndiswrapper-1.2/driver/misc_funcs.c:1037: warning: `regparm' attribute directive ignored
/opt/ndiswrapper-1.2/driver/misc_funcs.c:1045: warning: `__stdcall__' attribute directive ignored
/opt/ndiswrapper-1.2/driver/misc_funcs.c:1045: warning: `regparm' attribute directive ignored
{standard input}: Assembler messages:
{standard input}:3085: Error: Unrecognized opcode: `movl'
make[3]: *** [/opt/ndiswrapper-1.2/driver/misc_funcs.o] Error 1
make[2]: *** [_module_/opt/ndiswrapper-1.2/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-powerpc'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/opt/ndiswrapper-1.2/driver'
make: *** [install] Error 2 

what could be the problem ?

---

### Post by Kimm on 2005-08-11
dont get me wrong,  dont use ppc and I never have, but I find this line disturbing.

> 
....
{standard input}: Assembler messages
....


if the code contains assembler you wount be able to compile the program for any other architecture then the one it was written for, not without rewriting the assembler parts.

I'm not saying it does... but that line cinda suggests it does

---

### Post by ru55 on 2005-08-11
right  ](*,) 

i doubt that's ppc assembler like you said - duhh i didn't realize it :D 

so there's no hope to get a ppc ndiswrapper except doing it by myself ....

thanx anyway kimm

---

