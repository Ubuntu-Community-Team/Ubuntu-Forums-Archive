---
title: "Multiple Python locations? I do not know why they are there?"
date: 2020-05-18
forum: General Help
---

### Post by victor47 on 2020-05-18
Hello everyone! Sorry for taking up your time. 

I'm new to Linux in general. I've only been using it full time within the last month or so.

I've been digging into the my file system and at the same time reading the FHS documentation.

I've come across something that confuses me. I seem to have multiple Python installations. I remember I installed 3.8.2 sometime ago.

I thought that it was the only installation of Python.

Then after snooping around my file system (Ubuntu Budgie) and what I found was the following.

I saw that within the **/usr/lib **directory I found:
[B]python2.7
python3
python3.8[/B]

I did not understand why there were so many. The 2.7 isn't as important to me as much as the python3 and python3.8

when you go inside **python3 ** you find a directory called "**dist-packages**" with a bunch of modules. I could not find documentation on this directory.

inside of **python3.8** it seems to have the standard library modules.

Now if you go into **/usr/local/lib **you will find the same directory with same files plus a few more that aren't in the previous directory.

I thought that perhaps the python3.8 in the* /usr/lib is a symbolic link to /usr/local/lib* but when you run a ```
ls -al
``` on the /usr/lib directory

You see that it is its own directory and not a symbolic link.

This in general has me confused because when I run either python3 OR python3.8 I'll get the same python interpreter version. 

I don't know which directory the system is really using whenever I run python3 or python3.8



Is there a way for me to see which directory the system uses when I run the python interpreter.?

Also would there be a way for me to remove one of the installations?

---

### Post by wildmanne39 on 2020-05-18
*Thread moved to **General Help for a more appropriate fit**.*

---

### Post by CatKiller on 2020-05-18
> **victor47 said:**
> I've been digging into the my file system and at the same time reading the FHS documentation.

That's not going to help you as much as you imagine it will.

> I seem to have multiple Python installations.

You'll have multiple lots of things. The **alternatives** system is how they're managed.

For the specific case of python, Python 3 is not backwards compatible with Python 2, people called "python" when they meant Python 2, and Python 2 is dead. It was quite a mess. Python 2 is no longer (as of 20.04) included in a default Ubuntu install, which was a lot of work since Python is used by *a lot* of architectural things, like package management. You can still install Python 2 if you need it, but it's been bumped to the Universe repository.

> Is there a way for me to see which directory the system uses when I run the python interpreter.?

```
which python
which python3
ls -l /usr/bin/python
ls -l /usr/bin/python3

```

---

### Post by noob-at-linux on 2020-05-18
There can be multiple python packages because it may be required by other packages to run. It doesn't mean that it is important. But python2 is obsolete by now so I don't know why is it still there.
Yes you can see which interpreter you are using when using python. Just type python3.* or any version you have and press enter. It will start python interpreter and it will also show you the version you are using.
If you want to use different python versions you can type python3.* or python3 file.py to use specific interpreter. The program will be interepreted according to interpreter used by you. If you are using ubuntu 20.04 don't delete python3.8.
Sorry for my bad english.

---

### Post by TheFu on 2020-05-18
I’d bet that python3 and python3.8  are either hardlinks or one is a symbolic link to the other.  There are wikipedia articles for both topics.

For developers using python, the best practice is NOT to use the system versions, but to install the specific versions using something like pyenv so you can switch between the versions as needed.  Ruby and Perl have similar tools and best practices too.
 
Python2 is not obsolete and won't be for 15 yrs.  The code being used in the world determine that, not some group of devs chasing the new-shiny thing every year.  There are cobol programs written in the 1970s still running billing programs for many companies today.  Python2 will last that long too, probably.

---

### Post by CatKiller on 2020-05-18
> **TheFu said:**
> 
Python2 is not obsolete and won't be for 15 yrs.

https://www.python.org/doc/sunset-python-2/
> We have decided that January 1, 2020, was the day that we sunset Python 2. That means that we will not improve it anymore after that day, even if someone finds a security problem in it. You should upgrade to Python 3 as soon as you can.
... 
We released Python 2.0 in 2000. We realized a few years later that we needed to make big changes to improve Python. So in 2006, we started Python 3.0. Many people did not upgrade, and we did not want to hurt them. So, for many years, we have kept improving and publishing both Python 2 and Python 3.
... 
We did not want to hurt the people using Python 2. So, in 2008, we announced that we would sunset Python 2 in 2015, and asked people to upgrade before then. Some did, but many did not. So, in 2014, we extended that sunset till 2020.
... 
If people find catastrophic security problems in Python 2, or in software written in Python 2, then most volunteers will not help fix them. If you need help with Python 2 software, then many volunteers will not help you, and over time fewer and fewer volunteers will be able to help you. 

It is definitely obsolete, and it's already had 12 years on life support.

---

### Post by mIk3_08 on 2020-05-19
> Also would there be a way for me to remove one of the installations?
Since Python3 is not backwards-compatible and a lot of complex libraries are not yet ported to python3, I think this might not be a good idea for now. 
even though Python2 officially Hits End of Life, but not fully ended its life. If you try to remove it, that would be a risk.
Remember, Python3 is not backwards-compatible.

---

### Post by sisco311 on 2020-05-19
> **victor47 said:**
> 
when you go inside **python3 ** you find a directory called "**dist-packages**" with a bunch of modules. I could not find documentation on this directory.


There is a README.txt file in the directory
```
cat /usr/lib/python3/dist-packages/README.txt 
This directory exists so that 3rd party packages can be installed
here.  Read the source for site.py for more details.
```


You can use `dpkg-query --search *filename*' to search for packages that own a file. 

```
dpkg-query --search /usr/lib/python3/dist-packages/README.txt
dpkg-query --search /usr/lib/python3/dist-packages/

```

The first command will give you a hint where you can find the site.py file ;)
and the second one will list all the packages on your system which use the dist-packages directory.

EDIT:
I'm not familiar with python, but I hope this points you in the right direction.

---

### Post by Impavidus on 2020-05-19
> **victor47 said:**
> 
I've come across something that confuses me. I seem to have multiple Python installations. I remember I installed 3.8.2 sometime ago.

I thought that it was the only installation of Python.

Then after snooping around my file system (Ubuntu Budgie) and what I found was the following.

I saw that within the **/usr/lib **directory I found:
[B]python2.7
python3
python3.8[/B]

I did not understand why there were so many. The 2.7 isn't as important to me as much as the python3 and python3.8

when you go inside **python3 ** you find a directory called "**dist-packages**" with a bunch of modules. I could not find documentation on this directory.

inside of **python3.8** it seems to have the standard library modules.

Now if you go into **/usr/local/lib **you will find the same directory with same files plus a few more that aren't in the previous directory.

On Ubuntu 20.04, Python 3.8 is vital. You can't have a working Ubuntu  20.04 without Python 3.8, so it must have been installed already. Python  2.7 is no longer installed by default, but may be installed from the  package manager and may be there if you upgraded from a previous release  of Ubuntu. Python 3.8 is a form of Python 3, so not a different version.

/usr/local/lib only contains a few empty directories  and stuff you installed yourself without using the Ubuntu package  manager. It never contains vital stuff, but you can use it to install  extensions.
> **mIk3_08 said:**
> Since Python3 is not backwards-compatible and a lot of complex libraries are not yet ported to python3, I think this might not be a good idea for now. 
even though Python2 officially Hits End of Life, but not fully ended its life. If you try to remove it, that would be a risk.
Remember, Python3 is not backwards-compatible.On Ubuntu 20.04, nothing vital depends on Python 2.7. All vital software on Ubuntu 20.04 that uses Python has been ported to Python 3.

---

### Post by victor47 on 2020-05-19
Thank you guys for all your answers, it really helped.

---

### Post by TheFu on 2020-05-19
> **Impavidus said:**
> On Ubuntu 20.04, Python 3.8 is vital. You can't have a working Ubuntu  20.04 without Python 3.8, so it must have been installed already. Python  2.7 is no longer installed by default, but may be installed from the  package manager and may be there if you upgraded from a previous release  of Ubuntu. Python 3.8 is a form of Python 3, so not a different version.

/usr/local/lib only contains a few empty directories  and stuff you installed yourself without using the Ubuntu package  manager. It never contains vital stuff, but you can use it to install  extensions.
On Ubuntu 20.04, nothing vital depends on Python 2.7. All vital software on Ubuntu 20.04 that uses Python has been ported to Python 3.

Today I solved an issue getting rdiff-backup on 20.04 to be compatible with my backup server running 16.04.

rdiff-backup v1.2.8 on 16.04 is python2.
rdiff-backup v2.0.0 on 20.04 is python3 and incompatible. Something about string handling changes.
I use the client/server mode for rdiff-backup to limit the malware and crypto-ware risks.

It entailed pulling the 18.04 version of rdiff-backup (also v1.2.8) onto the 20.04 box. Pulled librsync1 code from 18.04.  The newer version isn't compatible with rdiff-backup.  Compiled librsync1, ran the "checks" [8 passed] and installed it into /usr/local/ (had to go back and add a -fPIC option, clean and redo it).  

Ran the rdiff-backup setup.py install ... got some error about missing Python.h ... sudo apt install python-dev ... back top python setup.py install --prefix=/usr/local  ... all seemed good.

Kicked off a backup of the 20.04 machine from my backup server ... 8 minutes later, it was done. Solved.  I'd been afraid to commit to 20.04 without a workable backup that fit into the infrastructure.
This is happiness:
```
$ sudo rdiff-backup --list-increment-sizes regulus
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Tue May 19 14:59:54 2020         5.51 GB           5.51 GB   (current mirror)
```

Having multiple pythons is important.  A few of my LUG members are having similar issues, which is to be expected.  As long as 16.04 and 18.04 are supported, we'll stay using rdiff-backup v1.2.8.  New and shinny isn't always better in the real world.

22.04 will need python2, but 24.04 probably won't.  Businesses have multiple distributions running. Hopefully, they will all be supported releases.

Anyway,  victor47 please mark this thread **SOLVED** - thread tools button just above the first post.

---

