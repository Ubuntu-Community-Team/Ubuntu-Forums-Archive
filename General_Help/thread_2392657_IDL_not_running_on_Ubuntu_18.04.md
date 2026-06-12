---
title: "IDL not running on Ubuntu 18.04"
date: 2018-05-23
forum: General Help
---

### Post by cssj on 2018-05-23
[COLOR=#111111][FONT=Ubuntu]Hi all, 

I have just installed IDL 7.1 on Ubuntu 18.04 x86_64. No error messages were prompted during the installation. However, when I try to run IDL on the shell, an error message is shown:
[/FONT][/COLOR]
```
/idl/idl706/bin/idl: 617: exec: /idl/idl706/bin/bin.linux.x86/idl: not found

```

[COLOR=#111111][FONT=Ubuntu]I have checked that the file /idl/idl706/bin/bin.linux.x86/idl exists. I have also used the file command for this file, and the result is:
[/FONT][/COLOR]
```
idl: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked
     interpreter /lib/ld-linux.so.2, for GNU/Linux 2.6.9, not stripped

```[COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]
Could be a problem with a library?
Does anyone have the same problem? Can you give me a hand with this?

Thanks![/FONT][/COLOR]

---

