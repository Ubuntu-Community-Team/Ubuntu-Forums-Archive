---
title: "BitTornado error."
date: 2006-08-05
forum: General Help
---

### Post by Roasted on 2006-08-05
BitTorrent T-0.3.13 (BitTornado)
OS: linux2
Python version: 2.4.3 (#2, Apr 27 2006, 14:43:58) 
[GCC 4.0.3 (Ubuntu 4.0.3-1ubuntu5)]
wxWindows version: 2.6.1.2pre

Traceback (most recent call last):
  File "/usr/bin/btdownloadgui", line 2325, in _next
    savedas = dow.saveAs(choosefile, d.newpath)
  File "/usr/lib/python2.4/site-packages/BitTornado/download_bt1.py", line 407, in saveAs
    if path.exists(path.join(file, x['path'][0])):
  File "/usr/lib/python2.4/posixpath.py", line 65, in join
    path += '/' + b
UnicodeDecodeError: 'ascii' codec can't decode byte 0xe2 in position 30: ordinal not in range(128)






:?: :?: :?: :?: 

I followed the instructions on the port forwarding web site to set up 10 ports (as instructed) for BitTornado. I already have one download running, and this was the second one I tried to start when I got the error.

EDIT - I've got 3 torrents now running just fine. Why did it give me the error?

---

### Post by Roasted on 2006-08-06
hai2u

---

### Post by Roasted on 2006-08-06
hai2u x2

---

### Post by Roasted on 2006-08-06
hai2u x3

---

### Post by Roasted on 2006-08-06
Another thing. No matter what I do, the best I can get is a yellow dot. I followed the port forwarding directions PERFECTLY. My screen matches their's and I did all of the changes they said. Still, yellow dot. Why?

---

