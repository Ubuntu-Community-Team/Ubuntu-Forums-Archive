---
title: "Wine doors installation"
date: 2007-01-15
forum: General Help
---

### Post by glendavee on 2007-01-15
I'm trying to install wine-doors using these instructions from [http://doc.gwos.org/index.php/HowToWine#Wine_Desktop](http://doc.gwos.org/index.php/HowToWine#Wine_Desktop)

sudo aptitude install subversion python
cd 
mkdir src 
cd src 
svn co [http://www.wine-doors.org/svn](http://www.wine-doors.org/svn) wine-doors 
cd wine-doors 
sudo python setup.py install

All seems to go ok until the install line when I get error message "no such file or directory"

Using file browser, I can see the file at   /wine-doors/wine-doors/trunk/setup.py

What am I doing wrong??

---

### Post by bodhi.zazen on 2007-01-15
Try:

sudo python setup.py

Or

sudo python ./setup.py

---

### Post by glendavee on 2007-01-15
Tried both these, same result - no such file or directory..

---

### Post by bodhi.zazen on 2007-01-15
:(

Wine-doors can be a .... hassle

Can you post the contents of the directory ...

ls -la

---

### Post by glendavee on 2007-01-15
Thanks for the reply
ls -la contents are :

total 28
drwxr-xr-x  7 david david 4096 2007-01-15 14:29 .
drwxr-xr-x 55 david david 4096 2007-01-15 19:35 ..
drwxr-xr-x  6 david david 4096 2007-01-15 14:30 sandbox
drwxr-xr-x  7 david david 4096 2007-01-15 14:30 .svn
drwxr-xr-x  4 david david 4096 2007-01-15 14:29 wine-doors
drwxr-xr-x  3 david david 4096 2007-01-15 14:29 wine-doors-server
drwxr-xr-x  4 david david 4096 2007-01-15 14:29 wine-doors-website

---

### Post by bodhi.zazen on 2007-01-15
descend into winedoors again:

 cd wine-doors

and take a peak ...

---

### Post by glendavee on 2007-01-15
Sorry, not sure I understand you. I ran ls -la from the wine-doors directory.
What do I do next?

---

### Post by bodhi.zazen on 2007-01-15
> **glendavee said:**
> Sorry, not sure I understand you. I ran ls -la from the wine-doors directory.
What do I do next?

Sorry, but within your wine-doors directory it appears there is another wine-doors sub directory ....

cd winedoors
ls -la

will change to that sub directory and ls will again list the contents of the directory ...

---

### Post by glendavee on 2007-01-15
Got you - I was being a bit thick.
result is 

total 16
drwxr-xr-x 4 david david 4096 2007-01-15 14:29 .
drwxr-xr-x 7 david david 4096 2007-01-15 14:29 ..
drwxr-xr-x 7 david david 4096 2007-01-15 14:30 .svn
drwxr-xr-x 8 david david 4096 2007-01-15 14:29 trunk

---

### Post by bodhi.zazen on 2007-01-15
Ackk ... :(

I don't see the install script anywhere. 

Go ahead and search some, but you may want to delete the whole thing and try downloading (svn) again ...

svn co [http://www.wine-doors.org/svn](http://www.wine-doors.org/svn) wine-doors

---

### Post by glendavee on 2007-01-15
I'll delete everything and have another go. I'll report back tomorow - enough Ubuntu for one day.

---

### Post by glendavee on 2007-01-19
I've had another go at downloading and installing. This time, when at the command line
python <file> install, I get following error :

[COLOR="Red"]david@david-desktop:~$ sudo python ~/src/wine-doors/wine-doors/trunk/setup.py install
Traceback (most recent call last):
  File "/home/david/src/wine-doors/wine-doors/trunk/setup.py", line 3, in ?
    from preferences import preferences
ImportError: No module named preferences[/COLOR]

First 3 lines in the setup.py file are :

import os, sys, shutil, gzip
sys.path.append( "./src" )
from preferences import preferences

Any ideas?

---

### Post by bodhi.zazen on 2007-01-19
Ack ...

---

