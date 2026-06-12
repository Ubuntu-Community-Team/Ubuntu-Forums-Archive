---
title: "Problems with flyback"
date: 2008-01-15
forum: General Help
---

### Post by ByKeLaO on 2008-01-15
I have downloaded flyback using svn. All the dependencies are satisfied. When I run "python flyback.py" I get the following error:

Traceback (most recent call last):
  File "flyback.py", line 1040, in <module>
    main()
  File "flyback.py", line 1035, in main
    MainGUI()
  File "flyback.py", line 418, in __init__
    self.refresh_file_list()
  File "flyback.py", line 271, in refresh_file_list
    file_stats = os.stat(full_file_name)
**OSError: [Errno 2] No such file or directory: '/tools'**

Anyone know how to fix this?

---

### Post by WearZeeP on 2008-01-15
If you are sure that nothing is wrong with the script and that it has all the right permissions, try running it with 
```
./flyback.py
```
I think it has something to do with python or other programs versions or something, but when you try the other method, it will sometimes get the correct version and get it right.
I believe it has something to to with the magic first bytes or what its called.

---

### Post by ByKeLaO on 2008-01-15
No luck. It gives me the same error message as before.
Actually, come to think of it I don't think all the dependencies are actually installed. There is one that doesn't seem to be in the apt-get repositories:
python-sqlite3

Anyone know where I can get it?

---

### Post by LJanardhan on 2008-01-18
Hi,

  Ya even i found the same problem during the installation of flyback. It seems to be apt-cache doesn't have that package in repository. 

  Is there any other solution to workaround.

Regards
Janardhan.
[http://linuxgalore.com/](http://linuxgalore.com/)

---

### Post by MeneK on 2008-01-20
Same problem here. I've installed python-sqlite (not python-sqlite3),  following these instructions: [http://bernaz.wordpress.com/2008/01/19/flyback-a-time-machine-backup-utility-for-linux/](http://bernaz.wordpress.com/2008/01/19/flyback-a-time-machine-backup-utility-for-linux/)

This is the error msg. I get:

```
Traceback (most recent call last):
  File "flyback.py", line 721, in <module>
    main()
  File "flyback.py", line 716, in main
    main_gui()
  File "flyback.py", line 363, in __init__
    self.refresh_file_list()
  File "flyback.py", line 246, in refresh_file_list
    file_stats = os.stat(full_file_name)
OSError: [Errno 2] No such file or directory: '/liblibvixAllProducts.so
```

---

### Post by fcarmona on 2008-01-22
the link is pointing to some unknow file.

grettings

[fcarmona]("http://weblog.fcarmona.com.mx")

---

### Post by skillllllz on 2008-01-23
> **robinjam said:**
> No luck. It gives me the same error message as before.
Actually, come to think of it I don't think all the dependencies are actually installed. There is one that doesn't seem to be in the apt-get repositories:
python-sqlite3

Anyone know where I can get it?


python-sqlite3 is not the correct package name. Install python-sqlite2 instead:
```
sudo apt-get install python-sqlite2
```

Enjoy! ;)

---

