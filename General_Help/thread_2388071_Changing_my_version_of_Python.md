---
title: "Changing my version of Python?"
date: 2018-03-28
forum: General Help
---

### Post by wakslob on 2018-03-28
Im pretty new with linux, so i hope you guys bare with me.
So when i try to run this python program, i get a syntax error on line 403:
```
def get_data(self, (maxcol,maxrow)):
```
And im guessing that this syntax is illegal in 3.6, (my current version)
So im trying to figure a way where i can use 2.7 or an earlier version where the syntax above would be accepted. 
Is it propper to change the symbolic link for "python" in my /usr/bin/ directory to use an earlier version then python3? 

Thanks.

---

### Post by monkeybrain20122 on 2018-03-28
Don't change the symlinks because many components of the system are linked to default python and python3, resetting symlinks and likewise setting global environmental variables for PYTHONPATH etc in .profile and .bashrc would mess up your system in unpredictable ways. If you want to use different versions of python you can use anaconda (if you use it don't follow the instruction to prepend anaconda/bin to your $PATH, instead append it to the end, for the reasons just explained), 

or install a version of python in some safe directory that doesn't interact with the system, say, $HOME/opt and make a symlink to it like 

```
ln -s /home/usrname/pythonxxx/bin/python /home/username/bin/python3.x
```

you then set up the site-lib and path for it in a script which you can source when you use this version of python 

Edited: if you want to use python2 instead it is easy since 2.7 is default basically you don't have to do anything. python= python2.7, python3 = python3.6
```
$ python --version
Python 2.7.14+
$ python3 --version
Python 3.6.5rc1
```

---

### Post by wakslob on 2018-03-28
Thanks

---

### Post by wakslob on 2018-03-28
After some careful consideration about what you said. I decided to dig deeper and discovered surprisingly, it was as easy as editing the program.py python version at the beginning of the file. Thanks for your insight!

---

### Post by monkeybrain20122 on 2018-03-28
> **wakslob said:**
> After some careful consideration about what you said. I decided to dig deeper and discovered surprisingly, it was as easy as editing the program.py python version at the beginning of the file. Thanks for your insight!

I don't think you need to do that. Just run python script.py or python3 script.py or /opt/pythonxx/bin/python script.py.. You don't have to have the version hard coded in your script (provided it works for whatever python you invoke)

---

