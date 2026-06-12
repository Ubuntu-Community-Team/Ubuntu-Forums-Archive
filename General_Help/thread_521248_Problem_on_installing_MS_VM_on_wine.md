---
title: "Problem on installing MS VM on wine"
date: 2007-08-09
forum: General Help
---

### Post by satimis on 2007-08-09
Hi folks,

Ubuntu 7.04 desktop
IEs4Linux
IE6

Download following packages on Internet;
msjavx86b3805.exe
MSJavWU_8073687b82d41db93f4c2a04af2b34d.exe 

I suppose "wine MSJavWU_8073687b82d41db93f4c2a04af2b34d.exe" is upgrade.


On terminal:
$ WINEPREFIX="/home/satimis/.ies4linux/ie6" wine msjavx86b3805.exe```

.....
Backtrace:
=>1 0x00be006e (0x0034fe18)
  2 0x7bc3ac3d in ntdll (+0x2ac3d) (0x0034fea8)
  3 0x7bc3b07f in ntdll (+0x2b07f) (0x0034fec8)
  4 0x7b86f87f ExitProcess+0x1f() in kernel32 (0x0034fee8)
  5 0x7ee8272a in regsvr32 (+0x272a) (0x0034ff08)
  6 0x7b87221e in kernel32 (+0x5221e) (0x0034ffe8)
  7 0xb7e0e897 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x00be006e: movl        0x10(%eax),%eax
Wine-dbg>

```
It hung here.

Typing  quit/finish etc. w/o action only popup "Wine-dbg>" again.

(Remark:)
Can't add "sudo" on the command line.  It can't find /home/satimis/....." path.


Continued to run;
$ WINEPREFIX="/home/satimis/.ies4linux/ie6" wine MSJavWU_8073687b82d41db93f4c2a04af2b34d.exe 

still the same ending finally at "Wine-dbg>"


Wine-dbg>what is```

err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file ole32.dbg ("")
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file oleaut32.dbg ("")
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file msjava.dbg ("")
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file vmhelper.dbg ("")
No symbols found for is

Undefined symbol
```

I have to force exit with :-
Wine-dbg>Ctrl-C: stopping debuggee


On both cases installation went through w/o complaint.


Started IE6

Tools -> Internet Options -> Advanced
Can't find "MS VM" there.


Pls help.  TIA


B.R.
satimis

---

