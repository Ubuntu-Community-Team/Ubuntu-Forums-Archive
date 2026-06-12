---
title: "Cant Install Anymore"
date: 2007-06-04
forum: General Help
---

### Post by s_h_a_d_o_w_s on 2007-06-04
```
giga@ubuntuzilla:~$ sudo update-manager -c
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

Traceback (most recent call last):
  File "/usr/bin/update-manager", line 71, in ?
    app.main(options)
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 749, in main
    self.fillstore()
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 599, in fillstore
    self.initCache()
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 692, in initCache
    self.cache = MyCache(progress)
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 82, in __init__
    apt.Cache.__init__(self, progress)
  File "/usr/lib/python2.4/site-packages/apt/cache.py", line 36, in __init__
    self.open(progress)
  File "/usr/lib/python2.4/site-packages/apt/cache.py", line 49, in open
    self._cache = apt_pkg.GetCache(progress)
SystemError: E:Dynamic MMap ran out of room, E:Error occurred while processing r-cran-matrix (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.
giga@ubuntuzilla:~$


```What do i do ? :D

---

### Post by christhemonkey on 2007-06-04
You need to add this line to /etc/apt/apt.conf
```
gksudo gedit /etc/apt/apt.conf 
```

Then add this line to the end of the file:
```
APT::Cache-Limit "12582912";
```

Then type:
```
sudo apt-get update 
```

And retry install.

---

### Post by s_h_a_d_o_w_s on 2007-06-04
It still wont work, thanks for the reply though
giga@ubuntuzilla:~$ sudo update-manager -c
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 71, in ?
    app.main(options)
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 7 49, in main
    self.fillstore()
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 5 99, in fillstore
    self.initCache()
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 6 92, in initCache
    self.cache = MyCache(progress)
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 8 2, in __init__
    apt.Cache.__init__(self, progress)
  File "/usr/lib/python2.4/site-packages/apt/cache.py", line 36, in __init__
    self.open(progress)
  File "/usr/lib/python2.4/site-packages/apt/cache.py", line 49, in open
    self._cache = apt_pkg.GetCache(progress)
SystemError: E:Dynamic MMap ran out of room, E:Error occurred while processing r -cran-matrix (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/archive. ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages, E:The package list s or status file could

---

### Post by christhemonkey on 2007-06-04
Did you try the:
```
sudo apt-get update 
```
?

Did it return any errors?

---

### Post by s_h_a_d_o_w_s on 2007-06-04
I got it working i just put " <--  those things (i forgot the name) around the number of cache and added more ache  and it worked :D

Thanks a lot :)

---

### Post by christhemonkey on 2007-06-04
No worries! Thanks for letting us know.


Maybe you should mark this thread as resolved? And maybe file a bug report?

---

### Post by s_h_a_d_o_w_s on 2007-06-04
Ok i checked it as resolved , Im not sure if ill file a bud report because i think it was my fault ; I closed the update manager while it was upgrading to edgy:p

---

### Post by christhemonkey on 2007-06-04
Fair enough!

Thanks for doing that, helps out any one else who has that problem!
A very good day to you sir.

---

### Post by Hasen_A on 2007-06-12
> **s_h_a_d_o_w_s said:**
> I got it working i just put " <--  those things (i forgot the name) around the number of cache and added more ache  and it worked :D

Thanks a lot :)

Next time paste the entire code:
```
APT::Cache-Limit "12582912";
```

I didn't exactly get the idea of where to put the appostraphies.

---

