---
title: "How to fix python error &quot;ImportError: No module named&quot;"
date: 2017-06-24
forum: General Help
---

### Post by charkel2 on 2017-06-24
I really need to run Printrun but it gives me this error. I have tried to find the solution but I cannot seem to figure it out.

I really need help.

```
charkel@charkel /usr/bin $ ./pronsole.py 
Traceback (most recent call last):
  File "./pronsole.py", line 21, in <module>
    from printrun.pronsole import pronsole
ImportError: No module named printrun.pronsole



```

---

### Post by bks on 2017-06-25
Could you perhaps post the source code to pronsole.py? You can also make sure the module is present in your Python directory, so the script can find it when it tries to load it. For example, I have all my additional packages installed in the *usr/lib/python2.7/dist-pakages* folder. 
Also install pip: ```
sudo apt-get install pip
```
Then try installing your packages: ```
sudo pip install [package name]
```

---

