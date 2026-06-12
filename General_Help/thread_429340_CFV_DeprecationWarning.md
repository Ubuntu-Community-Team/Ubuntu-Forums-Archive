---
title: "CFV DeprecationWarning"
date: 2007-05-01
forum: General Help
---

### Post by mucha on 2007-05-01
I think my cfv or python package aren't working that well. Because when I tries to check sfv with cfv I always get this error:
```
yadayada.r01 : ##################/usr/lib/python2.5/site-packages/cfv.py:705: DeprecationWarning: struct integer overflow masking is deprecated
  return struct.pack('>I',self.value)
```
Always on the first checksum-file, then the other files checks ok. Any idea what could be wrong?

---

### Post by zwanzig on 2007-12-15
I get the exact same error after some updates, used to work like a charm.

---

### Post by qpieus on 2008-02-09
yeah, me too. Nobody has any ideas about this error?

edit:
there's a bug report filed on this warning:

[https://bugs.launchpad.net/ubuntu/+source/cfv/+bug/158747](https://bugs.launchpad.net/ubuntu/+source/cfv/+bug/158747)

---

### Post by qpieus on 2008-02-09
Well, even with this warning, cfv seems to still check the files OK. I just did a test where I made a sfv file from a group of 8 picture files. Then I changed one of the picture files and ran an sfv check on the 8 files again. cfv correctly reported a bad crc on the file I changed.

---

### Post by neptune on 2008-02-11
I get this error too.
However, the last development on cfv was in 2005 so it probably isn't going to be resolved or updated.

---

### Post by qpieus on 2008-02-11
ah, I didn't know it hasn't been touched in a while. BTW, I get no errors when I make or check md5 check files, so I use those instead of sfv.

---

### Post by da chicken on 2008-05-17
First, this is a Warning, not an Error.  A Warning is the term when something was done wrong or needs to be fixed, but it's not an error-causing condition.

Second, is a deprecation warning.  The code line 763 uses a function or statement that the Python team has depreciated in Python 2.5.  It's deprecated, so the functionality is discouraged, probably because the Python team plans on removing it at some point in the future.

It's a bug that the cfv people need to fix, because cfv as written isn't going to work with future version of Python.

---

