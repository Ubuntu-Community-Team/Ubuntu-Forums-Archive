---
title: "problem with &quot;unicode&quot; package"
date: 2006-12-15
forum: General Help
---

### Post by street spirit on 2006-12-15
Hi.

*I know I should be posting this in the bug tracker, but I'm having email troubles and can't receive the registration emails. Maybe someone wants to file the bug for me?*

I just installed the "unicode" package on dapper, but it looks broken:

```
spaceman@babylon:~ $ unicode
Traceback (most recent call last):
  File "/usr/bin/unicode", line 159, in ?
    out( "Making directory %s\n" % (HomeDir) )
  File "/usr/bin/unicode", line 33, in out
    sys.stdout.write(i.encode(options.iocharset, 'replace'))
NameError: global name 'options' is not defined
```

/usr/bin/unicode is a Python script, and while I don't really know a thing about Python, the problem appears to be fixed by this simple patch:

```
--- /usr/bin/unicode.orig       2006-12-15 20:45:26.000000000 +0100
+++ /usr/bin/unicode    2006-12-15 20:45:54.000000000 +0100
@@ -30,7 +30,7 @@
 def out(*args):
     "pring args, converting them to output charset"
     for i in args:
-        sys.stdout.write(i.encode(options.iocharset, 'replace'))
+        sys.stdout.write(i.encode(iocharsetguess, 'replace'))

 colours = {
             'none'       :    "",
```

Could somebody who knows Python please confirm this, and (if the patch is alright) enter it into the bug tracker?

TIA

---

