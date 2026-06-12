---
title: "installing jupyter on ubuntu 16.04, 64 bit, with pip 10.0.01"
date: 2018-06-13
forum: General Help
---

### Post by Lou Reed on 2018-06-13
I amn trying to install jupyter on Ubuntu 16.04, 64 bit, with pip 10.0.01.


When I do it I  get the error message:

james@james-VirtualBox:~$ sudo pip install jupyter
Traceback (most recent call last):
  File "/usr/bin/pip", line 9, in <module>
    from pip import main
ImportError: cannot import name main

I know it can be installed with pip 8.0.0, but I do not want to downgrade my version of pip. So how do I 
get this to install with pip 10.0.01?

Any help  appreciated.


Respectfully,

ernest-t-bass

---

### Post by monkeybrain20122 on 2018-06-13
Looks like your pip is broken. How did you install it? Uninstall all pip packages then  use [get-pip.py]("https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=12&ved=0ahUKEwjoi5zm9dDbAhXH7YMKHZ5bANEQFghnMAs&url=https%3A%2F%2Fbootstrap.pypa.io%2Fget-pip.py&usg=AOvVaw0zKVO_zW0nkF7s0zdjWFNj") to install pip .

If still not work it may have something to do with you being in VB [https://github.com/pypa/pip/issues/5240](https://github.com/pypa/pip/issues/5240) (not in VB, but virtuenv and docker which is kind of a VM)

---

### Post by Lou Reed on 2018-06-14
I think that it has something to do with the pip version. It is clearly installs with pip version 8. At least I have seen videos that show jupyter software installing with pip version 8.

I just need to know how to uninstall this pip, before I put a different version.

Respectfully,

ernest-t-bass

---

### Post by dragonfly41 on 2018-06-14
Have you tried using pip3?

---

### Post by Lou Reed on 2018-06-15
i am quite new to python. I do not know what you mean. How do I install pip3?

I will try pip3 if can install it.

Respectfully,

ernest-t-bass

---

### Post by dragonfly41 on 2018-06-15
There is pip for python2 and pip3 for python3.
What version python are you running?

python --version

---

### Post by Lou Reed on 2018-06-15
I am running python version Python 2.7.15. That is why i do not want to install pip3. I believe it is for python3. I am running an earlier version. 

Respectfully,

ernest-t-bass

---

### Post by monkeybrain20122 on 2018-06-15
> **James_M._Yunker said:**
> I think that it has something to do with the pip version. It is clearly installs with pip version 8. At least I have seen videos that show jupyter software installing with pip version 8.

I just need to know how to uninstall this pip, before I put a different version.

Respectfully,

ernest-t-bass

```
sudo pip uninstall pip
```

This would remove it, then reinstall the deb package

```
sudo apt install --reinstall python-pip
```

Now when you use pip there will be a warning that you are not using the latest pip, just ignore it.

P.S If you are new to python better do python3, py2 is mainly for maintaining legacy codes. All new codes should be written in py3.

---

### Post by Lou Reed on 2018-06-15
That worked. I had to use sudo's -H option because I had initially some directory  ownership warnings. What does the sudo  -H option do?

Also, how do I now install jupyter notebook.

Thanks for all of your help.

Respectfully,

ernest-t-bass

---

### Post by monkeybrain20122 on 2018-06-16
```
sudo pip install -U jupyter
```

---

