---
title: "Can't uninstall python-gst0.10"
date: 2006-12-25
forum: General Help
---

### Post by Ferio on 2006-12-25
When trying to uninstall *python-gst0.10* (Serpentine's dependency, but I don't have Serpentine anymore), I get:
```
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
dpkg: error al procesar python-gst0.10 (--remove):
 el subproceso pre-removal script devolvió el código de salida de error 1
Se encontraron errores al procesar:
 python-gst0.10
Running prelink, please wait...
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
This has happened to me before with *firestarter* and some other packages, but it was as easy as removing the associated *.postrm* file. In this case, I have no idea on how to do it. Anyone?

---

### Post by dbbolton on 2006-12-25
did you try marking the python packages for removal in synaptic ?

---

### Post by Ferio on 2006-12-25
If I remove just *python*, it removes a lot of dependencies, I don't want to imagine what will happen if I remove every *python** package. I'm sure there's a less painful way of doing it. Well, I hope so, at least.

---

### Post by Ferio on 2006-12-28
Solved by removing */var/lib/dpkg/info/python-gst0.10.**, and then uninstalling. Hope everything will be okay after it.

---

