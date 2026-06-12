---
title: "digikam crashes w/ GDBM error"
date: 2005-03-29
forum: General Help
---

### Post by Rooftop on 2005-03-29
Hi,

running digikam from command line throws following error every time when I try to access image directories (albums)
~> digikam
digikam: WARNING: GDBM fatal error occured: lseek error
~>

.. and thereafter it just closes. 
Digikam version is:
~>dpkg -l digikam
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  digikam        0.7-3          digital photo management application for KDE

Any ideas?
Rx.

---

### Post by s_p_a_r_k_y on 2005-04-24
I get basically the same error
```
god@bart:~$ digikam
kbuildsycoca running...
digikam: WARNING: GDBM fatal error occured: lseek error
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
```

However I moved from another Linux distro to ubuntu keeping my /home directory. I'll try to remove any digikam configuration I had and then try it again.

---

### Post by s_p_a_r_k_y on 2005-04-24
Removing
/home/USERNAME/.thumbnails/digikam-thumbnails.db
worked for me.

---

