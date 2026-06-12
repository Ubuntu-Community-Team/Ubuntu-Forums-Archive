---
title: "Installing and running &quot;destar&quot;"
date: 2007-10-30
forum: General Help
---

### Post by nickcoons on 2007-10-30
I'm setting up an Asterisk system and have decided to try out destar for a web-based front-end.  However, I'm running into a problem after installation when trying to run destar.  I have two asterisk systems, one is Feisty and the other Gutsy.  They both produce this output when run:

```
DeStar 0.2.2, Copyright (C) 2005 by Holger Schurig and contributors.

DeStar comes with ABSOLUTELY NO WARRANTY. This is free software,
you are welcome to redistribute it under certain conditions;
see the included files GPL-2.txt and COPYRIGHT.txt

Serving application 'page_main' on port 8080
warning: Computing default hostname
info: Medusa (V1.11) started at Tue Oct 30 14:38:56 2007
        Hostname: [myhostname[
        Port:8080

Traceback (most recent call last):
  File "/usr/share/destar/python/destar.py", line 139, in <module>
    pub.run()
  File "/usr/share/destar/python/Server.py", line 168, in run
    publisher = self.publishclass(self.approot)
  File "/var/lib/python-support/python2.5/quixote/publish.py", line 107, in __init__
    self.root_namespace = _get_module(root_namespace)
  File "/var/lib/python-support/python2.5/quixote/publish.py", line 32, in _get_module
    __import__(name)
  File "/var/lib/python-support/python2.5/quixote/ptl_import.py", line 127, in find_import_module
    return self.loader.load_module(fullname, stuff)
  File "/var/lib/python-support/python2.5/quixote/ptl_import.py", line 107, in load_module
    return _load_ptl(name, filename, file)
  File "/var/lib/python-support/python2.5/quixote/ptl_import.py", line 72, in _load_ptl
    code = compile_template(file, filename, output)
  File "/var/lib/python-support/python2.5/quixote/ptl_compile.py", line 297, in compile_template
    template.compile()
  File "compiler/pycodegen.py", line 111, in compile
  File "/var/lib/python-support/python2.5/quixote/ptl_compile.py", line 268, in _get_tree
    tree = parse(self.source, self.filename)
  File "/var/lib/python-support/python2.5/quixote/ptl_compile.py", line 223, in parse
    return TemplateTransformer().parsesuite(buf)
  File "compiler/transformer.py", line 129, in parsesuite
  File "compiler/transformer.py", line 125, in transform
  File "compiler/transformer.py", line 158, in compile_node
  File "/var/lib/python-support/python2.5/quixote/ptl_compile.py", line 58, in file_input
    io_imp = ast.From(IO_MODULE, [(IO_CLASS, None)])
TypeError: __init__() takes at least 4 arguments (3 given)

```

According to the destar site, installation is pretty straight-forward.  Install the software, then run it.

Any ideas?

---

### Post by nickcoons on 2007-10-30
I should also add that I've never used any Asterisk front-end before; have always configured using the configuration files.  So I'm not stuck on destar.

If someone knows any other web-based front-ends that are very good and encompass many or all of the functionality one would get from manual configuration file editing, I would be open to trying those out as well.

---

### Post by verdaobr on 2007-12-26
I was having the same problem (with ubuntu server 7.10). I've found a similar bug in ubuntu 7.04 and it worked for me (after installing the package python2.4).
look to the bug report #82286: [https://bugs.launchpad.net/ubuntu/+source/destar/+bug/82286](https://bugs.launchpad.net/ubuntu/+source/destar/+bug/82286)

regards

---

