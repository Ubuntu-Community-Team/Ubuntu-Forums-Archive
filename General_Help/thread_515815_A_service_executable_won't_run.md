---
title: "A service executable won't run"
date: 2007-08-02
forum: General Help
---

### Post by tjkolev on 2007-08-02
Hello!

This is a general problem, but it is in the context of trying to run the TwonkyMusic service on my Feisty amd64 box. The installation of the package went fine. However the service executable won't run, and I can't figure why.

Here's what my setup looks like.

```

ls -l /etc/init.d/twonkyserver
-rwxr-xr-x 1 root root 4120 2007-07-23 22:41 /etc/init.d/twonkyserver

ls -ld /usr/local/TwonkyVision
drwxr-xr-x 4 root root 4096 2007-07-22 12:59 /usr/local/TwonkyVision

ls -l /usr/local/TwonkyVision
total 428
-rw-r--r-- 1 root root    311 2007-07-22 12:59 install.log
-rw-r--r-- 1 root root  16104 2007-04-04 06:21 licence-en.rtf
-r--r--r-- 1 root root   2763 2006-08-11 10:06 Linux-HowTo.txt
drwxr-xr-x 2 root root    106 2007-04-11 10:39 plugins
-rw-r--r-- 1 root root    421 2004-10-31 11:57 radio.m3u
drwxr-xr-x 2 root root   4096 2007-04-11 10:39 resources
-rw-r--r-- 1 root root  28238 2007-04-11 05:01 RevisionHistory
-rw-r--r-- 1 root root    422 2007-04-11 10:39 twonkymedia-default.ini
-rwxr-xr-x 1 root root   3946 2007-07-22 12:59 twonkymedia.sh
-rwxr-xr-x 1 root root   4300 2007-04-11 10:32 twonkymusic
-rwxr-xr-x 1 root root 352276 2007-04-11 10:32 twonkymusicserver
-rw-r--r-- 1 root root     29 2007-07-22 12:59 twonkyvision-musicserver.ini

```

The script in init.d tries to run twonkymusic from the above directory. But it fails. I try to start it manually and it fails with the same error

```

/usr/local/TwonkyVision/twonkymusic
-bash: /usr/local/TwonkyVision/twonkymusic: No such file or directory

```

Same thing with sudo:

```

sudo /usr/local/TwonkyVision/twonkymusic
sudo: unable to execute /usr/local/TwonkyVision/twonkymusic: No such file or directory

```

What is going on here? The file is there. Is bash giving me the wrong error back? Perhaps the file is corrupted or not an executable? I should get a different error in this case, right? Is it because I am trying to run it in 64 bit environment? What can I do to make this work?

Thank you!
tjk

---

### Post by greybit on 2007-08-02
What if you try:

```

sh /usr/local/TwonkyVision/twonkymusic

```

or:

```

cd /usr/local/TwonkyVision/
./twonkymusic

```

---

### Post by tjkolev on 2007-08-03
The second one gives me exactly the same error. The first one gives me a syntax error. The file is not a shell script.

tjk :)

---

### Post by tjkolev on 2007-08-05
As expected the problem was because the executable is 32bit and I am trying to run it in 64bit environment. Installing the package ia32-libs fixes it.

tjk

---

