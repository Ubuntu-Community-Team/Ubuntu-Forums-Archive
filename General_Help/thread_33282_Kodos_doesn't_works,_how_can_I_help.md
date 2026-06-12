---
title: "Kodos doesn't works, how can I help ?"
date: 2005-05-10
forum: General Help
---

### Post by pef on 2005-05-10
Hello,

If I try to launch kodos installed with apt-get, I get the following error :

 > pef@iron:~$ kodos
Traceback (most recent call last):
  File "/usr/bin/kodos", line 1255, in ?
    main()
  File "/usr/bin/kodos", line 1246, in main
    kodos = Kodos(filename, debug)
  File "/usr/bin/kodos", line 96, in __init__
    KodosBA.__init__(self)
  File "/usr/share/kodos/modules/kodosBA.py", line 850, in __init__
    self.groupBox1.setSizePolicy(QSizePolicy(7,7,0,0,self.groupBox1.sizePolicy().hasHeightForWidth()))
TypeError: argument 1 of QSizePolicy() has an invalid type 

I find a bug report asking to merge changes from Debian package which has corrected the bug

[https://bugzilla.ubuntu.com/show_bug.cgi?id=10360]("https://bugzilla.ubuntu.com/show_bug.cgi?id=10360")

The patch works, I tested it by downloading the sources (apt-get source) and applying the patch.

Now I have a working kodos package, but how can I send it to the "official" archive ?

Thank you

---

