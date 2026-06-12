---
title: "Make python3 the default"
date: 2019-08-26
forum: General Help
---

### Post by hojjat on 2019-08-26
I upgrade my Ubuntu all the way from 16.04 to 18.04 when it came out. Through this process, python 2.x remained the default version of python, and when I installed pip, it was also installed based on python 2.x

How can I make python 3.x the default version? Also, how can I get pip to work based on python 3, not python 2?

I tried ```
sudo apt install python3-pip
``` but when I ran ```
pip3
``` on the command it said "command not found: pip3"

---

### Post by #&amp;thj^% on 2019-08-26
There isn't such a thing as a 'default' python interpreter because it just depends on which actual file /usr/bin/python points to.

Can't you alias pip='pip3' in your ~/.bash_profile?

In Terminal, run nano ~/.bash_profile, then add a line to the end that reads "alias pip='pip3'". This is safe; it won't affect system processes, only your user and terminal.
```

me on Mon Aug 26 at 11:49 AM in ~ branch: (HEAD) 
>> pip -V
pip 19.0.3 from /usr/lib/python3.7/site-packages/pip (python 3.7)
```

I always just run it via Python itself, this way:
```

python3 -m pip install some_module
```

or
```

python2 -m pip install some_module
```

The -m calls the __main__.py module of a specified package. Pip supports this.

---

### Post by oldfred on 2019-08-26
Python will always be the python2 version.
You start python3 by specifying that.
With 18.04 python3 is default, but many apps still install python2. 
You do not want to change python defaults or you may have to totally reinstall Ubuntu.

fred@bionic-z97:~/Downloads$ pip3 --version
pip 9.0.1 from /usr/lib/python3/dist-packages (python 3.6)
fred@bionic-z97:~/Downloads$ python --version
Python 2.7.15+
fred@bionic-z97:~/Downloads$ python3 --version
Python 3.6.8

---

### Post by hojjat on 2019-08-26
Thank you both. The issue is when I run *pip3 --version* I get "command not found: pip3" but when I run *sudo apt-get install python3-pip* it says the package is already installed.

---

### Post by hojjat on 2019-08-26
Actually, never mind. Uninstalling and reinstalling python3-pip fixed it. Thanks for the explanation of the rest of the points!

---

### Post by Skaperen on 2019-08-26
try "pip install pip3" and see if that does it?  i can't recall how i did it, but i have the opposite problem of "command not found: pip" on Xubuntu 18.04.

---

### Post by dragonfly41 on 2019-08-26
I used this command to refresh my memory on how I installed pip3

```
history | grep pip3 | grep install
```

Also I use update-alternatives to toggle between different python versions.

e.g. sudo update-alternatives --config python3

---

