---
title: "Help with tar.gz (binary) installation"
date: 2007-01-26
forum: General Help
---

### Post by ChrisR on 2007-01-26
I'm running Ubuntu Edgy.

I'm trying to upgrade my Mozilla Thunderbird from 1.5 to 2.0.

I downloaded the Thunderbird 2.0 tar.gz file into my /tmp folder.

I extracted with the tar command.

So now I have a directory called "thunderbird" in my /tmp directory.

This is where I ran into some trouble. I know that I don't have to compile from source to install this program. There is a file in the thunderbird directory called "run-mozilla.sh"

I believe this is the binary. 

My question is, how do I execute it?

I've tried the following:

./run-mozilla.sh
./install run-mozilla.sh

Doesn't seem to work. Thank you.

---

### Post by taurus on 2007-01-26
Can you list the whole directory of it, /tmp/thunderbird?

```
ls -la /tmp/thunderbird
```

---

### Post by kosmic on 2007-01-26
try to do :

***sudo chmod a+x run-mozilla.sh***
and then
***./run-mozilla.sh***

---

### Post by ChrisR on 2007-01-26
> **taurus said:**
> Can you list the whole directory of it, /tmp/thunderbird?

```
ls -la /tmp/thunderbird
```

Here it is:

rossini@rossini-desktop:/tmp/thunderbird$ ls -la /tmp/thunderbird
total 16976
drwxr-xr-x 12 rossini rossini     4096 2006-12-06 18:50 .
drwxrwxrwt 13 root    root        4096 2007-01-26 17:21 ..
drwxr-xr-x  3 rossini rossini     4096 2006-12-06 18:50 chrome
drwxr-xr-x  2 rossini rossini     8192 2006-12-06 18:50 components
drwxr-xr-x  8 rossini rossini     4096 2006-12-06 18:45 defaults
-rw-r--r--  1 rossini rossini       52 2006-12-06 18:22 dependentlibs.list
drwxr-xr-x  2 rossini rossini     4096 2006-12-06 18:39 dictionaries
drwxr-xr-x  4 rossini rossini     4096 2006-12-06 18:46 extensions
drwxr-xr-x  2 rossini rossini     4096 2006-12-06 18:34 greprefs
drwxr-xr-x  2 rossini rossini     4096 2006-12-06 18:45 icons
drwxr-xr-x  2 rossini rossini     4096 2006-12-06 18:45 init.d
-rw-r--r--  1 rossini rossini      476 2006-12-06 18:50 libfreebl3.chk
-rwxr-xr-x  1 rossini rossini   250416 2006-12-06 18:50 libfreebl3.so
-rwxr-xr-x  1 rossini rossini   174036 2006-12-06 18:50 libldap50.so
-rwxr-xr-x  1 rossini rossini   749380 2006-12-06 18:50 libmozjs.so
-rwxr-xr-x  1 rossini rossini   208096 2006-12-06 18:50 libnspr4.so
-rwxr-xr-x  1 rossini rossini   472328 2006-12-06 18:50 libnss3.so
-rwxr-xr-x  1 rossini rossini   267976 2006-12-06 18:50 libnssckbi.so
-rwxr-xr-x  1 rossini rossini    16464 2006-12-06 18:50 libplc4.so
-rwxr-xr-x  1 rossini rossini    10080 2006-12-06 18:50 libplds4.so
-rwxr-xr-x  1 rossini rossini    15204 2006-12-06 18:50 libprldap50.so
-rwxr-xr-x  1 rossini rossini   149480 2006-12-06 18:50 libsmime3.so
-rw-r--r--  1 rossini rossini      476 2006-12-06 18:50 libsoftokn3.chk
-rwxr-xr-x  1 rossini rossini   351800 2006-12-06 18:50 libsoftokn3.so
-rwxr-xr-x  1 rossini rossini   166876 2006-12-06 18:50 libssl3.so
-rwxr-xr-x  1 rossini rossini   110980 2006-12-06 18:50 libxpcom_compat.so
-rwxr-xr-x  1 rossini rossini   786168 2006-12-06 18:50 libxpcom_core.so
-rwxr-xr-x  1 rossini rossini    10548 2006-12-06 18:50 libxpcom.so
-rwxr-xr-x  1 rossini rossini     9028 2006-12-06 18:50 libxpistub.so
-rwxr-xr-x  1 rossini rossini     6434 2006-06-26 20:25 LICENSE.txt
-rwxr-xr-x  1 rossini rossini   152244 2006-12-06 18:50 mozilla-installer-bin
-rwxr-xr-x  1 rossini rossini    11200 2006-12-06 18:50 mozilla-xremote-client
-rw-r--r--  1 rossini rossini      184 2005-05-13 15:53 README.txt
-rwxr-xr-x  1 rossini rossini     2319 2006-12-06 18:49 removed-files
drwxr-xr-x  5 rossini rossini     4096 2006-12-06 18:50 res
-rwxr-xr-x  1 rossini rossini    10492 2005-10-01 01:36 run-mozilla.sh
-rwxr-xr-x  1 rossini rossini     5201 2006-12-06 18:40 thunderbird
-rwxr-xr-x  1 rossini rossini 13148852 2006-12-06 18:50 thunderbird-bin
-rwxr-xr-x  1 rossini rossini    71112 2006-12-06 18:50 updater
-rw-r--r--  1 rossini rossini      148 2006-09-25 14:36 updater.ini
drwxr-xr-x  3 rossini rossini     4096 2006-12-06 18:45 updates
-rwxr-xr-x  1 rossini rossini    26520 2006-12-06 18:50 xpicleanup

---

### Post by taurus on 2007-01-26
You run it with

```
./thunderbird-bin
```
However, I would strongly recommend you move directory thunderbird to your $HOME or somewhere else because /tmp will get emptied when you reboot your machine.  Then, /tmp/thunderbird will be gone.

---

### Post by ChrisR on 2007-01-26
> **kosmic said:**
> try to do :

***sudo chmod a+x run-mozilla.sh***
and then
***./run-mozilla.sh***

Unfortunately, this was the result:

rossini@rossini-desktop:/tmp/thunderbird$ sudo chmod a+x run-mozilla.sh
Password:
rossini@rossini-desktop:/tmp/thunderbird$ ./run-mozilla.sh

run-mozilla.sh: Cannot execute .

---

### Post by ChrisR on 2007-01-26
> **taurus said:**
> You run it with

```
./thunderbird-bin
```
However, I would strongly recommend you move directory thunderbird to your $HOME or somewhere else because /tmp will get emptied when you reboot your machine.  Then, /tmp/thunderbird will be gone.

ahhh....

Should I move it before or after I run ./thunderbird-bin? Does it matter?

---

### Post by taurus on 2007-01-26
You can run it now to see if it works.  Then, shut it down and move the whole thunderbird directory to somewhere else before you reboot or turn off your computer.

---

### Post by ChrisR on 2007-01-26
> **taurus said:**
> You can run it now to see if it works.  Then, shut it down and move the whole thunderbird directory to somewhere else before you reboot or turn off your computer.

Thank you so much for your help! :D

---

### Post by taurus on 2007-01-26
Does the new version of thunderbird start?

---

