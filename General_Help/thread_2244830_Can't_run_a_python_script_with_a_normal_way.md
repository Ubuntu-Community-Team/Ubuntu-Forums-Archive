---
title: "Can't run a python script with a normal way"
date: 2014-09-19
forum: General Help
---

### Post by obocheng on 2014-09-19
I  use the following to run _*proxy.py*_ 
```
sudo python proxy.py
``` 
terminal shows &#65306;
```

Traceback (most recent call last):  File "proxy.py", line 84, in <module>
    import OpenSSL
  File "./packages.egg/linux/OpenSSL/__init__.py", line 35, in <module>
  File "./packages.egg/linux/OpenSSL/__init__.py", line 30, in load_crypto
  File "./packages.egg/linux/OpenSSL/crypto.py", line 10, in <module>
ImportError: No module named OpenSSL.crypto

```

But the *_proxy.py_* works well when use ```
sudo /usr/bin/python proxy.py
```

I don't know why,and how to fix it.
Help me.
Thanks a lot.

---

### Post by claracc on 2014-09-19
I don't think sudoe is a valid command, at least I don't find it in man pages.

What does exist is ```
sudo -e
``` which means that user wants to edit one or more files (as man page states) also, command sudoedit is used when it is desired to see the security policy.

---

### Post by obocheng on 2014-09-19
sorry,I have a typo

---

### Post by steeldriver on 2014-09-19
Your results suggest that the version of python found in sudo's secure path is different from /usr/bin/python - what does

```

sudo which python

```

say?

---

### Post by obocheng on 2014-09-19
> **steeldriver said:**
> Your results suggest that the version of python found in sudo's secure path is different from /usr/bin/python - what does

```

sudo which python

```

say?

I have set python path: export PATH="$PATH:/usr/local/bin/python"
so...
It says: /usr/local/bin/python

---

### Post by steeldriver on 2014-09-19
I`m confused - which version are you trying to use? unless you've messed with the configuration, sudo should ignore your exported PATH (and even ignore root's PATH - it has its own secure_path)

---

### Post by obocheng on 2014-09-20
I am trying to use python 2.7.8.(the latest version).
Because this problem,I guess whether it's my PythonPath's problem,then I try to change it.

---

### Post by steeldriver on 2014-09-20
Based on what you posted previously, you are changing PATH not PYTHONPATH

If you have installed a non-standard version of python in /usr/local, then that is the version that sudo will find because it uses the path, which places /usr/local/bin ahead of /usr/bin

```

Defaults    secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

```

If your script works when you run it with /usr/bin/python but doesn't work when you use 'sudo python', then that suggests your installation of python in /usr/local is incomplete (i.e. based on your error message, it doesn't include the python-openssl wrapper package)

---

