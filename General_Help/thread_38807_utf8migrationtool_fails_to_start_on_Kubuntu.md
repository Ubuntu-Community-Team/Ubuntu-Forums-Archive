---
title: "utf8migrationtool fails to start on Kubuntu"
date: 2005-06-02
forum: General Help
---

### Post by ranarion on 2005-06-02
Hello everyone,

the UTF-8 migration tool fails to start on my Kubuntu installation:

```

$ utf8migrationtool
Traceback (most recent call last):
  File "/usr/bin/utf8migrationtool", line 3, in ?
    import sys, locale, os, gtk, gobject
ImportError: No module named gtk

``` 

A quick check with kynaptic tells me all standard python modules (I suspect this is a python app, right?) and everything containing "gtk" in its name is installed. So what is the program looking for?

Many thanks in advance!

---

