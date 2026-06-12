---
title: "mount -t cifs using credentials file doesn't work??"
date: 2005-10-20
forum: General Help
---

### Post by tvh on 2005-10-20
Is this a bug, my n00bish fault or something else?

I cannot mount a samba share using a credentials file, like this:

```
mount -t cifs -o credentials=/home/foo/.smbpwd //server/share /home/foo/files
```

credential file /home/foo/.smbpwd is 
```
username=foo
password=plaintext
```

and the error in syslog is ```
CIFS VFS: No username specified
[4295079.940000]  CIFS VFS: cifs_mount failed w/return code = -22

```

But I can mount the share by passing the username and password in the command line:
```
mount -t cifs -o user=foo,password=plaintext //server/share /home/user/files
```
Actually, I cannot mount a share without passing the password on the command line. I read on the manpage that if no password is passed, mount command should ask for it. I get the same error than above if no password is passed on the command line. 

Any ideas?

---

### Post by tvh on 2005-10-21
Problem solved!

mount.cifs was not installed. I had to compile it from samba sources and mv to /sbin. After that all the problems were gone.

---

### Post by exobuzz on 2005-10-23
easier to type

apt-get install smbfs

(which contains your mount.cifs) :)

---

### Post by tigon5 on 2008-02-15
I had the same problem in a fresh install of Gutsy - problem solved with above solution.  

surely mount shouldn't accept the -t cifs option without complaining that mount.cifs isn't installed - seems stupid to me!

---

