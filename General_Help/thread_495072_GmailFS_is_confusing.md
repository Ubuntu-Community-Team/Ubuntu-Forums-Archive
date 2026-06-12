---
title: "GmailFS is confusing"
date: 2007-07-07
forum: General Help
---

### Post by rsvirani on 2007-07-07
There is many directionson how to install gmailfs, but all are outdated.  I did the most recent, a simple apt-get install gmailfs.  Now what?  how do I mount hte drive?  How do I set it to mount automatically at boot?

---

### Post by bmorency on 2007-07-07
> **rsvirani said:**
> There is many directionson how to install gmailfs, but all are outdated.  I did the most recent, a simple apt-get install gmailfs.  Now what?  how do I mount hte drive?  How do I set it to mount automatically at boot?


here are a couple examples how to mount the drive.

      mount -t gmailfs none /path/of/mount/point -o  username=gmailuser,pass&#8208;
       word=gmailpass,fsname=zOlRRa

or 

       mount.gmailfs    none    /mnt   -o   username=gmailuser,password=gmail&#8208;
       pass,fsname=zOlRRa

it might not be a good idea to mount it automatically because you would need to have your username and password in a config file. the fsname in the examples is kinda like an extra password. you should change it to something difficult.

there is also a man page for mount.gmailfs for other options.

---

### Post by onegreenparker on 2007-07-25
Tried mount.gmailfs.....username....password......etc
I got:

```

Traceback (most recent call last):
  File "/usr/bin/mount.gmailfs", line 162, in ?
    main(mountpoint, odata, useEncfs)
  File "/usr/bin/mount.gmailfs", line 88, in main
    gmailfs.main(mountpoint, odata)
  File "/usr/share/gmailfs/gmailfs.py", line 1133, in main
    server = Gmailfs(mountpoint, odata)
  File "/usr/share/gmailfs/gmailfs.py", line 603, in __init__
    self.ga.login()
  File "/usr/lib/site-python/libgmail/__init__.py", line 318, in login
    pageData = self._retrievePage(redirectURL)
  File "/usr/lib/site-python/libgmail/__init__.py", line 331, in _retrievePage
    resp = urllib2.urlopen(req)
  File "/usr/lib/python2.4/urllib2.py", line 130, in urlopen
    return _opener.open(url, data)
  File "/usr/lib/python2.4/urllib2.py", line 356, in open
    req = meth(req)
  File "/usr/lib/python2.4/urllib2.py", line 943, in do_request_
    raise URLError('no host given')
urllib2.URLError: <urlopen error no host given>

```

the other method showed that gmailfs is an unknown fs.

---

### Post by secretkeeper81 on 2007-08-01
I didn't install any packets but did everything manually following the instructions on the official GmailFS website: 

[http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem-installing.html](http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem-installing.html)

and it works fine when I try mounting it as root!

To mount it as non root, first I run some commands like:

```
chown root:fuse /usr/bin/fusermount
chmod 4750 /usr/bin/fusermount
mkdir /mnt/gmail
chown root:fuse /mnt/gmail
chmod 777 /mnt/gmail

```

Then to mount it (make sure your user belongs to fuse group!):

```
mount.gmailfs /usr/local/bin/gmailfs.py /mnt/gmail
```

And to unmount it: 

```
fusermount -u /mnt/gmail
```

Otherwise you can add a line to /etc/fstab (I think it's safer to store your username, password and fsname in /etc/gmailfs.conf):

```

/usr/local/bin/gmailfs.py      /mnt/gmail         gmailfs      rw,noatime,users,exec,dev,suid,noauto      0      0
```

and then just mount as non root using this command:

```
mount /mnt/gmail
```

---

