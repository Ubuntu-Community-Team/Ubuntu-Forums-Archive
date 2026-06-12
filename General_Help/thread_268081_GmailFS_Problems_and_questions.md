---
title: "GmailFS: Problems and questions"
date: 2006-09-29
forum: General Help
---

### Post by jimtb on 2006-09-29
I'm using Kubuntu Dapper Drake 6.06 and I wanted to try something new today, so I decided to play with GmailFS...
I followed some instructions I found on the net and I finally managed to mount my gmailfs but:
First of all, I cant cd to /mnt/gmailfs without having root privilleges. I tried
```
$chown jimakos.jimakos /mnt/gmailfs
$chown jimakos /mnt/gmailfs
$chmod 777 /mnt/gmailfs
```
but none of them made a difference.

Also, when I try to mount the gmailfs drive, I get the following errors:
```
jimakos@jimakos-desktop:~$ sudo mount /mnt/gmailfs
Password:
Ignored option :rw
Ignored option :noauto
Traceback (most recent call last):
  File "/sbin/mount.gmailfs", line 164, in ?
    main(mountpoint, namedOptions, useEncfs)
  File "/sbin/mount.gmailfs", line 90, in main
    gmailfs.main(mountpoint, namedOptions)
  File "/usr/bin/gmailfs.py", line 1130, in main
    jimakos@jimakos-desktop:~$ server = Gmailfs(mountpoint, **namedOptions)
  File "/usr/bin/gmailfs.py", line 542, in __init__
    Fuse.__init__(self, mountpoint, **kw)
  File "/usr/lib/python2.4/site-packages/fuse.py", line 560, in __init__
    self.parser = parserclass(*args, **kw)
  File "/usr/lib/python2.4/site-packages/fuse.py", line 224, in __init__
    SubbedOptParse.__init__(self, *args, **kw)
  File "/usr/lib/python2.4/site-packages/fuseparts/subbedopts.py", line 240, in __init__
    OptionParser.__init__(self, *args, **kw)
TypeError: __init__() got an unexpected keyword argument 'username'

```

This can be [temporarily] fixed if I type
```
export FUSE_PYTHON_COMPAT=0.1
```
but if I open a new console session, the problem reappears.

I also have one question, whats the purpose of gmailfs.conf, if I still have to write my password in fstab or the shell command? Shouldnt the program get the username, password and filesystem information from there somehow?

Thank you for your time :-)

PS. Sorry if I posted in a wrong category, but this seemed the most suitable. ](*,)

---

### Post by jarcand on 2006-11-29
> **jimtb said:**
> 
I also have one question, whats the purpose of gmailfs.conf, if I still have to write my password in fstab or the shell command? Shouldnt the program get the username, password and filesystem information from there somehow?


I have not gotten [FONT="Courier New"]gmailfs[/FONT] working yet, but I can answer your question.  According to what I have read, [FONT="Courier New"]username[/FONT], [FONT="Courier New"]password[/FONT], and [FONT="Courier New"]fsname[/FONT] values stored in [FONT="Courier New"]gmailfs.conf[/FONT] are the "default" values used by [FONT="Courier New"]gmailfs[/FONT] when they are not specified in the command line or [FONT="Courier New"]fstab[/FONT] options.

What I still do not understand is why does [FONT="Courier New"]gmailfs[/FONT] throw warnings when the "default" values are used; seems to me that storing the values in [FONT="Courier New"]gmailfs.conf[/FONT] is safer than storing them in [FONT="Courier New"]fstab[/FONT].

---

