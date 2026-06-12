---
title: "Matlab Problems"
date: 2005-06-16
forum: General Help
---

### Post by abhia7 on 2005-06-16
I am trying to run Matlab R14-SP1 on Hoary.
The problem I am facing is that I cannot run Simulink. Matlab installation proceeds without a flaw, but as soon as I start Simulink, Matlab crashes, and I get the following error:

simulink
??? Can't load '/usr/local/matlab7/bin/glnx86/libmwsimulink.so': libXft.so.1: cannot open shared object file: No such file or directory

??? Insufficient memory to execute script %.


------------------------------------------------------------------------
Assertion detected at Thu Jun 16 16:43:56 2005
------------------------------------------------------------------------

Assertion failed: hdr->in_use != 0, at line 706 of file "memmgr/memcache.cpp".
Attempt to free previously freed memory


Did anyone face a similar problem?

Thanks a lot!

---

### Post by GrumpySimon on 2005-06-19
I haven't had this problem, but at a guess, I'd double check that libXft was installed. There are two versions:

libxft2
libxft1

2 is the newer version, and 1 is the older, outdated version.

Try installing them:
```

sudo apt-get install libxft2

```

See if matlab runs, if not, install the first one:
```

sudo apt-get install libxft1

```

As for the memory error - do you have enough RAM? 

--Simon

---

### Post by abhia7 on 2005-06-20
Hello Simon,

Thanks a lot! Your suggestion helped immensely. 
I found that libxft2 was already installed. Installing libxft1 solved the problem and I can run MAtlab and Simulink just fine. 

I do get the following warning:

Inconsistency detected by ld.so: rtld.c: 1259: dl_main: Assertion `_rtld_local._dl_rtld_map.l_prev->l_next == _rtld_local._dl_rtld_map.l_next' failed!

I guess it is because now I have both libXft1 and libXft2 installed. But it hasnt precluded Matlab from working fine, so I am not too concerned. 

Once again, thanks a lot.

Best,

---

### Post by songo on 2006-05-20
[QUOTE=abhia7]
simulink
??? Can't load '/usr/local/matlab7/bin/glnx86/libmwsimulink.so': libXft.so.1: cannot open shared object file: No such file or directory
[/QUOTE]

if you don't want to install libxft2 **sudo apt-get install libxft1** may not solve it but **sudo apt-get --reinstall install libxft1** worked for me. if you (re)install libxft1 with the synaptic it will be fixed also.

but i still getting
**/usr/local/matlab7/bin/util/oscheck.sh: line 134: /lib/libc.so.6: Permission denied**
when i start matlab with or without root. any solutions?

---

