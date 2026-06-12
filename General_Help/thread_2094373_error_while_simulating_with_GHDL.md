---
title: "error while simulating with GHDL"
date: 2012-12-13
forum: General Help
---

### Post by dxtr12 on 2012-12-13
hey everybody
i want to simulate a basic vhdl program , but i think something is wrong with GHDL , the code is 100% correct because i've just simulate it in Modelsim on Windows
here is the Error
```

dxtr@dxtr:~/Desktop/Vhdl/diviseur$ ghdl -a diviseur.vhd
dxtr@dxtr:~/Desktop/Vhdl/diviseur$ ghdl -e diviseur
/usr/bin/ld: cannot find -lz
collect2: error: ld returned 1 exit status
ghdl: compilation error

```
can you please help me

---

### Post by dxtr12 on 2012-12-13
anybody ??

---

### Post by dxtr12 on 2012-12-13
what does this means "/usr/bin/ld: cannot find -lz"

---

### Post by Dio Gratia on 2012-12-14
The GHDL run time uses a runtime library (grt) that requires several libraries to operate.  These are found in a file named grt.lst collocated withe the GHDL runtime library libgrt.a.  The installation location can be at the whim of distribution and version.

grt.lst contents:

[INDENT]@/libgrt.a
-ldl
-lm
-Wl,--version-script=@/grt.ver
-Wl,--export-dynamic
-L./
-lz
[/INDENT]

-lz means include the library archive z (libz.a) in the linking process (a flag to the ld command).  

You don't have libz recognizably installed.

If I had to hazard a guess it's used for waveform dump files.

---

### Post by dxtr12 on 2012-12-14
> **Dio Gratia said:**
> The GHDL run time uses a runtime library (grt) that requires several libraries to operate.  These are found in a file named grt.lst collocated withe the GHDL runtime library libgrt.a.  The installation location can be at the whim of distribution and version.

grt.lst contents:

[INDENT]@/libgrt.a
-ldl
-lm
-Wl,--version-script=@/grt.ver
-Wl,--export-dynamic
-L./
-lz
[/INDENT]

-lz means include the library archive z (libz.a) in the linking process (a flag to the ld command).  

You don't have libz recognizably installed.

If I had to hazard a guess it's used for waveform dump files.
Problem solved :) 
i just uninstall it and re install it again

---

