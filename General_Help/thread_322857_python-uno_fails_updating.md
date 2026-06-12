---
title: "python-uno fails updating"
date: 2006-12-21
forum: General Help
---

### Post by Ferio on 2006-12-21
I've got some new updates today (or so my Update Manager says): some security ones (related to Mono), and some others related to OpenOffice. But when trying to apply the OO updates, everyone of them works but the *python-uno* one. Now the package seems to be broken, and I get this every time I try to update it (some lines are in Spanish, if you need the translation, just tell me):
```
Preparando para reemplazar python-uno 2.0.4-0ubuntu3 (usando .../python-uno_2.0.4-0ubuntu4_i386.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 935, in run
    pkg.remove(runtimes, remove_script_files=True)
  File "/usr/bin/pycentral", line 693, in remove
    default_runtime.remove_byte_code(self.private_files)
AttributeError: 'NoneType' object has no attribute 'remove_byte_code'
dpkg: aviso - script de `pre-removal' antiguo devolvió código de error 1
dpkg - probando el script del nuevo paquete en su lugar...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 935, in run
    pkg.remove(runtimes, remove_script_files=True)
  File "/usr/bin/pycentral", line 693, in remove
    default_runtime.remove_byte_code(self.private_files)
AttributeError: 'NoneType' object has no attribute 'remove_byte_code'
dpkg: error al procesar /var/cache/apt/archives/python-uno_2.0.4-0ubuntu4_i386.deb (--unpack):
 el subproceso script pre-removal nuevo devolvió el código de salida de error 1
Se encontraron errores al procesar:
 /var/cache/apt/archives/python-uno_2.0.4-0ubuntu4_i386.deb
Running prelink, please wait...
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Any idea anyone? Thanks in advance.

---

### Post by kperkins on 2006-12-21
[LEFT]Same here--any help?
I've tried fixing the broken package through synaptic, forcing removal through apt-get, and dpkg, to no avail.
It seems to be a pycentral problem as far as I can tell, but I 'm not sure.```

Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 935, in run
    pkg.remove(runtimes, remove_script_files=True)
  File "/usr/bin/pycentral", line 693, in remove
    default_runtime.remove_byte_code(self.private_files)
AttributeError: 'NoneType' object has no attribute 'remove_byte_code'
dpkg: error processing python-uno (--purge):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 python-uno

Not all changes and updates succeeded. For further details of the the failure, please expand the 'terminal' panel below.


```[/LEFT]

---

### Post by OffHand on 2006-12-21
```
sudo apt-get remove python-uno && sudo apt-get install python-uno
```

---

### Post by kperkins on 2006-12-21
Get the same errors

---

### Post by lamego on 2006-12-21
```
sudo rm /var/lib/dpkg/info/python-uno.prerm
sudo apt-get remove python-uno
sudo apt-get install python-uno
```

---

### Post by kperkins on 2006-12-21
Thanks lamego. :D

---

### Post by Ferio on 2006-12-22
Yes! Thank you, lamego. It's the same error that happens when trying to uninstall Firestarter, but I didn't notice.

---

### Post by durand on 2007-02-26
thank u soo much. took me ages to fix my problems but a combination of apt-get and synaptic along with ur template code did the trick. :D

---

