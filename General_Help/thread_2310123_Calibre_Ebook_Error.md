---
title: "Calibre Ebook Error"
date: 2016-01-16
forum: General Help
---

### Post by sasafrass452 on 2016-01-16
One of my ebooks no longer opens. Calibre gives me this error:

 Traceback (most recent call last):
   File "/usr/lib/calibre/calibre/gui2/viewer/main.py", line 37, in run
     Thread.run(self)
   File "/usr/lib/python2.7/threading.py", line 763, in run
     self.__target(*self.__args, **self.__kwargs)
   File "/usr/lib/calibre/calibre/ebooks/oeb/iterator/book.py", line 100, in __enter__
     {}, self.base)
   File "/usr/lib/calibre/calibre/customize/conversion.py", line 241, in __call__
     log, accelerators)
   File "/usr/lib/calibre/calibre/ebooks/conversion/plugins/epub_input.py", line 197, in convert
     extractall(stream)
   File "/usr/lib/calibre/calibre/utils/localunzip.py", line 223, in extractall
     _extractall(f, path)
   File "/usr/lib/calibre/calibre/utils/localunzip.py", line 210, in _extractall
     raise ValueError('Not a ZIP file')
 ValueError: Not a ZIP file

What can I do to fix this? I tried downloading it again, but got the same result. It won't open on my android tablet, either. Help!

---

### Post by sasafrass452 on 2016-01-19
Can anyone help?

---

