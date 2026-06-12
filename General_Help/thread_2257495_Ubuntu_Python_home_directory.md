---
title: "Ubuntu Python home directory"
date: 2014-12-20
forum: General Help
---

### Post by Semn on 2014-12-20
Hello, I am trying to install a program that requires the python path in Ubuntu. However, this path is manifold:

/usr/include/python2.7/
/usr/include/wx-2.8/wx/wxPython/
/usr/local/lib


and others

Which path is the one that points to all necessary files of the final installed python package?

---

### Post by steeldriver on 2014-12-20
Hello and welcome to the forums. What are you trying to install, exactly?

Those look like paths to python development headers and libs - they shouldn't be relevant unless you are trying to build a program from source that uses python bindings

If you are just installing a pre-built python module library, then usually you don't need to mess with the default pythonpath unless you have installed things in non-standard locations

---

