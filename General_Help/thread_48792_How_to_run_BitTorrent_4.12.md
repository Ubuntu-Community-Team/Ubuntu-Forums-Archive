---
title: "How to run BitTorrent 4.12?"
date: 2005-07-13
forum: General Help
---

### Post by ubuntp on 2005-07-13
So i downloaded BitTorrent 4.12 from bittorrent.com, installed the deb but now i'm left with some .py files. How do i associate them with my torrents (automatically)?

---

### Post by bored2k on 2005-07-13
Your post is not clear enough. I don't know if you want it to run when double clicking a torrent or you just don't know how to run it. Anyways, here it goes:
-------

A) Run bittorrent ? Open the btdownloadgui.py file (clicking on it should do. you could make it run with a single click instead of double clicking on run). Another method is going to the terminal and running python btdownloadgui.py in the folder your bittorrent got extracted.

-----

B) .Torrent association ?

> Q: How to change default file type "Open with" program?

Right click on file -> Properties

Open With Tab -> Add
Select "Open with" program

Select "Open with" program (Checked)

Would that do the job?
I know you also want this integration with Firefox, but I kinda forgot the site I had previously seen it get done :s

---

### Post by ubuntp on 2005-07-13
Ah yes, i guess i actually figured it out but was irritated by the error which is probably a genuine error:

[I]Traceback (most recent call last):
  File "/usr/bin/btdownloadgui.py", line 17, in ?
    from BitTorrent import locale_root
ImportError: cannot import name locale_root
[/I]

---

