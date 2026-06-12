---
title: "What the heck is goin on? Python environmental variable issue"
date: 2013-08-03
forum: General Help
---

### Post by elesbb on 2013-08-03
Hello guys, some reason i had to make a new account. Anyhow, trying to compile Mozilla for android using the prebuilt virtual disk. Having issues with python.

Here is what i tried and what i got. Pretty self explanatory..

```
mozilla@ubuntu:~/src/mozilla-central$ export PYTHON=python2.7
mozilla@ubuntu:~/src/mozilla-central$ python
Python 2.6.5 (r265:79063, Apr 16 2010, 13:09:56) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 



```

Whats happening if you dont see it right away is that even though i am setting the environment variable of PYTHON to python2.7, when executing "python" it says its 2.6.5. What the heck?? This prevents me from using ./mach to build the android app

---

### Post by drmrgd on 2013-08-03
I don't believe that you're doing what you think you're doing.  There is no environment variable $PYTHON.  So, while you've set '$PYTHON' to that path, it's not going to get called when you run 'python'.  Beyond that, it's not really a good idea to change the default version of python like that, as there are a lot of critical Ubuntu components that rely on python to work.  You can just specify the version you want by adding the version string to the call: 'python2.7 mach' (which I'm assuming is a python script).

```
$ pythonPython 2.7.3 (default, Apr 10 2013, 06:20:15) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 
dave@CygnusX1:/usr/bin $ python3
Python 3.2.3 (default, Apr 10 2013, 06:11:55) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 

```

---

### Post by elesbb on 2013-08-04
> **drmrgd said:**
> I don't believe that you're doing what you think you're doing.  There is no environment variable $PYTHON.  So, while you've set '$PYTHON' to that path, it's not going to get called when you run 'python'.  Beyond that, it's not really a good idea to change the default version of python like that, as there are a lot of critical Ubuntu components that rely on python to work.  You can just specify the version you want by adding the version string to the call: 'python2.7 mach' (which I'm assuming is a python script).

```
$ pythonPython 2.7.3 (default, Apr 10 2013, 06:20:15) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 
dave@CygnusX1:/usr/bin $ python3
Python 3.2.3 (default, Apr 10 2013, 06:11:55) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 

```

Hmm, okay then.. I was just following instructions xD 
# build
rm -rf objdir-droid
export PYTHON=python2.7
./mach build
./mach package



So i was very confused when i got those errors. i will try python2.7 mach and see what happens.

Thanks for the reply!

---

### Post by elesbb on 2013-08-04
Yayy

Now im getting this. Damn i thought the whole point in downloading this 4 gig VB disk was to make things simple? This is freaking ridiculous.

```

mozilla@ubuntu:~/src/mozilla-central$ python2.7 mach build
Traceback (most recent call last):
  File "mach", line 47, in <module>
    mach = load_mach(dir_path)
  File "mach", line 21, in load_mach
    return mach_bootstrap.bootstrap(topsrcdir)
  File "/home/mozilla/src/mozilla-central/build/mach_bootstrap.py", line 163, in bootstrap
    import mach.main
ImportError: No module named mach.main

```

---

