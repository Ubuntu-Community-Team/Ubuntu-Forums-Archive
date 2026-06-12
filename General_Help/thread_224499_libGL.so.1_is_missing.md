---
title: "libGL.so.1 is missing"
date: 2006-07-28
forum: General Help
---

### Post by calx on 2006-07-28
When trying to run Amarok I get the following error..

/usr/lib/amarok/amarokapp: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

How can I restore libGL.so.1?

---

### Post by philippe_carlo on 2006-07-28
If /usr/lib/libGL.so.1.2 still exists, then it's just a matter of creating a link:
```
 sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1
```

In the other case, try doing
```
sudo aptitude reinstall libgl1-mesa
```

---

### Post by calx on 2006-07-28
Thanks for the reply, seems libGL.so.1 is missing too. Any idea how I can fix the package manually as it suggests? And why does it want to uninstall gdm?! 

```
calx@rasta:/usr/lib$ sudo aptitude reinstall libgl1-mesa
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  gdm ubuntu-sounds
The following packages will be REINSTALLED:
  libgl1-mesa
0 packages upgraded, 0 newly installed, 1 reinstalled, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 16.3MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Error!
E: I wasn't able to locate file for the libgl1-mesa package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
```

Cheers philippe I didnt even know where to start, at least you gave me something to work on.

---

### Post by philippe_carlo on 2006-07-28
First: it is not trying to install gdm, but it is trying to remove it (read again). 

Weird error you're getting there. Try:
```

sudo apt-get update
sudo aptitude reinstall libgl1-mesa

```

---

### Post by calx on 2006-07-29
> And why does it want to **uninstall** gdm?!

Still get the same error :( This started when I tried to install compiz.. grr second time I've wrecked an installation trying to do the same thing guess I should stop trying! :confused: 


> **philippe_carlo said:**
> First: it is not trying to install gdm, but it is trying to remove it (read again). 

Weird error you're getting there. Try:
```

sudo apt-get update
sudo aptitude reinstall libgl1-mesa

```

---

### Post by calx on 2006-07-29
Ok well I figured out why it wasnt able to find the libgl1-mesa package, I had removed the following from my sources.list; 

```
deb http://xgl.compiz.info/ dapper aiglx
deb http://xgl.compiz.info/ dapper main
```
Adding them back has allowed libgl1-mesa to be reinstalled, yet all I get now is..
```
calx@rasta:/usr/lib$ ls libGL*
libGLEW.so.1.3  libGLEW.so.1.3.1  libGL.so  libGLU.so.1  libGLU.so.1.3.060500

```
No libGL.so.1 :confused: Still getting the same errors when I try to run Amarok and other apps that seem to be relying on libGL.so.1 to run.

---

### Post by mlind on 2006-07-29
```

$ dpkg -S /usr/lib/libGL.so.1
libgl1-mesa: /usr/lib/libGL.so.1

```

aptitude reinstall should do it. If it doesn't work, try
```

sudo dpkg -P --force-depends libgl1-mesa

```
Then install package back using aptitude.

---

### Post by calx on 2006-07-29
Thanks for all the replies.. this thread pointed me in the right direction [http://ubuntuforums.org/showthread.php?t=197471]("http://ubuntuforums.org/showthread.php?t=197471") 

Simply copying the file out of ATI driver package to /usr/lib did the trick. :D

---

