---
title: "&quot;file&quot; not specifying mime types for Word/Excel?"
date: 2007-03-29
forum: General Help
---

### Post by nathanziarek on 2007-03-29
I'm trying to build a little app to import and act on certain file types based on their kind (word, jpg, etc). I figured using the mime-type was probably the safest method.

I would like to use the actual mime types, not the human readable stuff.

```
**$ file test.***
test.doc:        Microsoft Office Document
test.xls:        Microsoft Office Document
```

If I run file to get the mime type, though, it returns a blank:
```
**$ file -i -m /usr/share/file/magic test.***
test.doc:
test.xls:

```

From reading around, it seems like this magic file is pretty important, and I would just soon not mess with it without at least some suggestions. Obviously the magic file knows how to figure out an office doc (although it seems to not differentiate between excel and word), but it won't return the mime type.

Am I doing something wrong? Is there something I can change (safely) to help it along?

Thanks!

Nate

---

### Post by nathanziarek on 2007-03-29
Furthering my question:
```
**$ file -i -k -r -m /usr/share/file/magic test.***
test.xls:        
- application/msword
- application/msword
test.doc: 
- application/msword
- application/msword
```

As you can see, it doesn't seem to know the difference between an Excel and Word doc (although it does know the difference between OOo Writer / Calc docs).

---

