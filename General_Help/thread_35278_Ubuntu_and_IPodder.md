---
title: "Ubuntu and IPodder"
date: 2005-05-18
forum: General Help
---

### Post by loom001 on 2005-05-18
I searched through the forums and came up with 2 ipodder hits that really didn't provide any real help.  

So I am wondering if anyone has a step by step to get IPodder working on Ubuntu Hoary.  I am pulling my hair out over this one any help would be great.

Thanks in advance!

[Ipodder website](http://ipodder.sourceforge.net/index.php) 

 ](*,)

---

### Post by loom001 on 2005-05-18
I did just find this, and I am going to try it out.  Will update with if it works or not.

[http://www.ubuntulinux.org/wiki/IPodder](http://www.ubuntulinux.org/wiki/IPodder)

---

### Post by 23meg on 2005-05-18
well, [one of those threads](http://www.ubuntuforums.org/showthread.php?t=14536&highlight=iPodder)  is about the exact same matter, so you could have just posted there instead of starting a new one, preferably with the error messages you're getting.

---

### Post by loom001 on 2005-05-18
The Link that I posted preety much solved that issue, but after that I was missing a wx that I also hade to install.

It is working for me know.

---

### Post by loom001 on 2005-05-18
Ok for the benifit of everyone here is what I did to get ipodder to work.

1. tar -xjf iPodder-linux-2.0-rc3.tar.bz2 

2. sudo ./iPodder-linux/install.sh 

3. sudo apt-get install python2.4-xmms 

4. sudo apt-get install wxpython2.5.3

Thats it then it worked for me.

Hope that helps out anyone having issues.

---

### Post by loom001 on 2005-05-19
I am having issues getting it to download, but the above directions are good to aleast get it to install.

---

### Post by joeh on 2005-05-19
How do I get iPodder to use xmms as the player?

---

### Post by rathel on 2005-06-26
Okay I did what you guys suggest but I get this error:
```

rathel@ubuntu:~$ iPodder
Traceback (most recent call last):
  File "iPodderGui.py", line 38, in ?
    import iPodderWindows
  File "/opt/iPodder/iPodderWindows.py", line 6, in ?
    import gui.tree
  File "/opt/iPodder/gui/tree.py", line 16, in ?
    from ipodder import grabbers
  File "/opt/iPodder/ipodder/grabbers.py", line 56, in ?
    from configuration import __version__
  File "/opt/iPodder/ipodder/configuration.py", line 15, in ?
    import players
ImportError: Bad magic number in /opt/iPodder/ipodder/players.pyc

```

---

### Post by nikopol on 2005-06-27
[QUOTE=rathel]Okay I did what you guys suggest but I get this error:
```
[...]
ImportError: Bad magic number in /opt/iPodder/ipodder/players.pyc

```[/QUOTE]

```
sudo chmod 644 /opt/iPodder/ipodder/players.py
``` will solve your problem. Just check the link in post numero 2.

---

### Post by rathel on 2005-06-27
Thank you, I will check it out.

---

### Post by nybble on 2005-07-07
[QUOTE=nikopol]```
sudo chmod 644 /opt/iPodder/ipodder/players.py
``` will solve your problem. Just check the link in post numero 2.[/QUOTE]


Thanks man, that fixed my issue aswell :)

**nybble**

---

### Post by nikopol on 2005-07-21
Glad it's working now :)

---

### Post by nybble on 2005-08-29
Well, I've reinstalled Hoary, and now I'm having new issues:
```

nybble@essence:~$ iPodder
  File "iPodderGui.py", line 73
    CHECK_VERSION = 2.1.1
                        ^
SyntaxError: invalid syntax

```
Thanks in advance. I've done all the recommended steps here, and i've gotten no-where... ](*,)

---

### Post by knathraak on 2005-08-30
[QUOTE=nybble]Well, I've reinstalled Hoary, and now I'm having new issues:
```

nybble@essence:~$ iPodder
  File "iPodderGui.py", line 73
    CHECK_VERSION = 2.1.1
                        ^
SyntaxError: invalid syntax

```
Thanks in advance. I've done all the recommended steps here, and i've gotten no-where... ](*,)[/QUOTE]

This actually is an error in the python script, iPodderGuid.py, in the latest version.
Go to where you installed iPodder--assuming /opt/iPodder/.
you may need to be root to do the following steps.
make a backup copy of iPodderGui.py like this:
cp iPodderGui.py iPodderGui.py.orig
open iPodderGui.py in your favorite text editor like gedit or vi.
go to line 73
where 2.1.1 is assigned to CHECK_VERSION, it should be in quotes but it's not.  change it so it reads:
CHECK_VERSION = "2.1.1"

save and exit.

All should be good.

if you break things you can always copy the iPodderGuid.py.orig back to iPodderGui.py to get back to a known state.

---

### Post by Davidios on 2005-09-03
When I start iPodder...

> Another copy of iPodder is running. Please raise it, wait for it to complete, or kill it.

There is no another iPodder running, I can't kill anything. What can I do?

---

