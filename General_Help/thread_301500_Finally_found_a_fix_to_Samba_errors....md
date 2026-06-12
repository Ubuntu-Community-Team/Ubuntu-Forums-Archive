---
title: "Finally found a fix to Samba errors..."
date: 2006-11-17
forum: General Help
---

### Post by drewnoakes on 2006-11-17
I hope that this will help someone else out.

This was my first experience with setting up a Samba server.  I learned quite a bit about Samba while working through this one.

Firstly, to determine if Samba is even running:

```
drew@ubuntu:/var/log/samba$ ps -ef | grep mbd
root     12210     1  0 12:45 ?        00:00:00 /usr/sbin/nmbd -D
root     12728     1  0 12:57 ?        00:00:00 /usr/sbin/smbd -D
root     12734 12728  0 12:57 ?        00:00:00 /usr/sbin/smbd -D
drew     12760 10872  0 12:58 pts/0    00:00:00 grep mbd
```

If not, then try starting it yourself:

```
drew@ubuntu:/etc/samba$ sudo /etc/init.d/samba start
 * Starting Samba daemons...                                 [fail]
```

In this example, you can see that mine was failing.  But why?

There are three daemons used by a Samba server:

nmbd - used for name registration and resolution
smbd - used for file and print operations
winbindd - used with windows domains

I'm using Samba with a WORKGROUP setup so I don't need the third service.  Of the three, nmbd must be started first.  Let's try running it in interactive mode to see how it behaves:

```
sudo nmbd -i -S -d 10
```

This runs it interactively (i), logging to STDOUT (S) and with the highest debug level (d 10).  You can drop the debug level if needed.

For me at least, nmbd started up and ran perfectly.  I hope this is the same for you!

Let's do the same with smbd:

```
sudo smbd -i -S -d 10
```

I saw a lot of output, but the process eventually exits with a message:

```
User smbguest in passdb, but getpwnam() fails!
attempting to free (and zero) a server_info structure
ERROR: failed to setup guest info.
```

I had previously seen this message in one of the Samba log files, located (by default for me at least) in /var/log/samba

```
drew@ubuntu:/var/log/samba$ cat log.smbd 
[2006/11/17 12:57:24, 0] smbd/server.c:main(805)
  smbd version 3.0.22 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2006
[2006/11/17 12:57:24, 1] auth/auth_util.c:make_server_info_sam(876)
  User smbguest in passdb, but getpwnam() fails!
[2006/11/17 12:57:24, 0] smbd/server.c:main(829)
  ERROR: failed to setup guest info.
```

Well it seems simple now, but it took me a while to work it out.  To resolve this problem, I deleted the smbguest account:

```
drew@ubuntu:/var/log/samba$ sudo smbpasswd -x smbguest
Deleted user smbguest.
```

Then, tried starting Samba:

```
drew@ubuntu:/etc/samba$ sudo /etc/init.d/samba start
 * Starting Samba daemons...                                [ ok ]
```

Wow, it started!  Let's check the log file (which I had previously wiped):

```
drew@ubuntu:/var/log/samba$ cat log.smbd 
[2006/11/17 12:57:57, 0] smbd/server.c:main(805)
  smbd version 3.0.22 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2006
```

Finally, checking my process list, I see them:

```
drew@ubuntu:/var/log/samba$ ps -ef | grep mbd
root     12210     1  0 12:45 ?        00:00:00 /usr/sbin/nmbd -D
root     12728     1  0 12:57 ?        00:00:00 /usr/sbin/smbd -D
root     12734 12728  0 12:57 ?        00:00:00 /usr/sbin/smbd -D
drew     12760 10872  0 12:58 pts/0    00:00:00 grep mbd
```

I'm no Samba guru, but I hope that this walk-through either:

[LIST=1]
[*] prompts someone to tell me if I've done something wrong,
[*] helps you debug a different Samba problem if you feel as lost as I did,
[*] solves your exact problem.
[/LIST]

:)

---

