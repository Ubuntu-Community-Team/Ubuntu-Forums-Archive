---
title: "Ubuntu 18.04:  broken python3 stuff? -- &gt; py3compile: not found"
date: 2020-03-20
forum: General Help
---

### Post by sgruenbe on 2020-03-20
Hi guys - I hope you can help me.

I tried already so much things so that I think now that every further attempt will make things worse. 

Everything started with gnome-terminal which didn't start anymore, then an icon appear saying that updates are somehow broken.

Now I'm at the point that I cannot install anything anymore:   

apt-get install python3 --reinstall
...
Setting up python3-minimal (3.6.7-1~18.04) ...
/var/lib/dpkg/info/python3-minimal.postinst: 5: /var/lib/dpkg/info/python3-minimal.postinst: py3compile: not found
dpkg: error processing package python3-minimal (--configure):
...


What can I try to get things working again? I hope someone could guide me...

---

### Post by him610 on 2020-03-20
What happens if you try to reinstall *python3-minimal*

---

### Post by sgruenbe on 2020-03-20
Hi there,

when I try:    apt-get install --reinstall python3-minimal

...I get "0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 no upgraded.
3 not fully installed or removed.
Need to get 0 B/47.2 kB of archives.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for python3-minimal:amd64

---

### Post by him610 on 2020-03-20
I think you have something broken, this is what I get,
```

sudo apt-get install --reinstall python3-minimal
[sudo] password for xxxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  linux-modules-extra-5.3.0-18-generic
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 23.4 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu focal/main amd64 python3-minimal amd64 3.8.2-0ubuntu1 [23.4 kB]
Fetched 23.4 kB in 0s (96.0 kB/s)        
(Reading database ... 245071 files and directories currently installed.)
Preparing to unpack .../python3-minimal_3.8.2-0ubuntu1_amd64.deb ...
Unpacking python3-minimal (3.8.2-0ubuntu1) over (3.8.2-0ubuntu1) ...
Setting up python3-minimal (3.8.2-0ubuntu1) ...
/usr/lib/python3.8/subprocess.py:838: RuntimeWarning: line buffering (buffering=1) isn't supported in binary mode, the default buffer size will be used
  self.stdin = io.open(p2cwrite, 'wb', bufsize)
Processing triggers for man-db (2.9.1-1) ...

```
I don't know what you have that is broken. Please show, between the code tags, results of, 
```

uname -snrp && lsb_release -d && echo $XDG_CURRENT_DESKTOP
```

---

### Post by sgruenbe on 2020-03-21
Hi, here the results:

uname -snrp
Linux zbook 5.3.0-42-generic x86_64

lsb_release -d
bash: /usr/bin/lsb_release: /usr/bin/python3: bad interpreter: No such file or directory

echo $XDG_CURRENT_DESKTOP
ubuntu:GNOME


By the way, in xterm i can start python shells without a problem with:

python
giving the shell for Python 2.7.17

python3
giving the shell for Python 3.5.6

So python seems to work somehow....

---

### Post by rsteinmetz70112 on 2020-03-21
Please use the Code tags.

I think the key is this line

```
3 not fully installed or removed.
```

Try running 

```
sudo apt install -f 
```and ```
sudo dpkg --configure -a
```

If that doesn't fix it at least it will give you and us some clues on what to do next.

---

### Post by sgruenbe on 2020-03-23
Thanks for your response...

```

sudo apt install -f

Reading package lists... Done
Building dependency tree
Reading state information.. Done
...
0 upgraded, 0 newly installed, 0 to remove and 72 not upgraded.
10 not fully installed or removed.
Need to get 0 B/47.2 kB of archives.
After this operation, 0 B of additional disk space will be used.
dpkg: error processing package python3 (--configure):
 package is in a very bad inconsistent state; you should 
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of python3-dev:
 python3-dev depends on python3 (= 3.6.7-1~18.04); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libboost-python1.65-dev:
 libboost-python1.65-dev depends on python3-dev; however:
  Package python3-dev is no configured yet.

dpkg: error processing package libboost-python1.65-dev (--configure):
 dependency problems - leaving unconfigured
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Then as I understood I tried to reinstall python3:
```

sudo apt-get install --reinstall python3
...
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 72 not upgraded.
...

```

Seemed ok. After this I executed again without errors:

```

sudo apt install -f

Reading package lists... Done
Building dependency tree
Reading state information.. Done
...
0 upgraded, 0 newly installed, 0 to remove and 72 not upgraded.

```

---

### Post by sgruenbe on 2020-03-23
After a restart now Gnome does not start anymore!
I end up in a terminal :-(

---

### Post by mörgæs on 2020-03-23
Are you sure that you want to carry on trying to salvage 18.04?
A fresh install of 19.10 takes 20 minutes and contains Python 3.7.5 by default.

---

### Post by sgruenbe on 2020-03-23
Yes I'm already considering this... only thing is to restore all the toolchains and data... this is the biggest concern.
I really would like to know what happened here, but I have no idea anymore what caused the problem...

I think my last attempt will be to make an upgrade to 19.10 from terminal, if that somehow works...

---

### Post by mörgæs on 2020-03-23
Just be sure that everything is backed up before trying the upgrade approach.

---

