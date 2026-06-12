---
title: "gmailfs Problems"
date: 2005-09-24
forum: General Help
---

### Post by conor on 2005-09-24
Okay guys, when I try to mount my new gmail file system, I get the following error message: 

```
conor@xxxxxx:~$ sudo mount gmailfs
conor@xxxxxx:~$ gmailfs.py:Gmailfs:mountpoint: '/home/conor/gmailfs'
gmailfs.py:Gmailfs:unnamed mount options: ['rw', 'noauto']
gmailfs.py:Gmailfs:named mount options: {'username': 'xxxxxxxxxxxxxx@gmail.com', 'password': 'xxxxxxxxxx', 'fsname': 'xxxxxxxxxxx'}
Traceback (most recent call last):
  File "/usr/share/gmailfs/gmailfs.py", line 1117, in ?
    server = Gmailfs()
  File "/usr/share/gmailfs/gmailfs.py", line 603, in __init__
    self.ga.login()
  File "/usr/lib/python2.4/site-packages/libgmail/__init__.py", line 281, in login
    raise GmailLoginFailure
libgmail.GmailLoginFailure

``` 

Does anyone know what I'm doing wrong?

---

### Post by karczi on 2005-09-29
first of all: u shoud use python 2.3 not the newest version 2.4...dunno why exacly but all ppl are saying me the same...

---

### Post by makhand on 2005-11-08
[QUOTE=karczi]first of all: u shoud use python 2.3 not the newest version 2.4...dunno why exacly but all ppl are saying me the same...[/QUOTE]

I'm having the same problem. What do i need to change to get it to use python 2.3? I didnt set it up with 2.4, it did it by itself through synaptic. I'm using breezy, by the way

---

