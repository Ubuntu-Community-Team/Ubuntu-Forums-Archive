---
title: "In startup script, file &quot;not found&quot;, but it exists..."
date: 2012-12-26
forum: General Help
---

### Post by apokkalyps on 2012-12-26
I'm trying to install ventrilo server on 12.04 using these instructions:
[http://ulyssesonline.com/2012/08/27/install-ventrilo-server-on-ubuntu-12-04/](http://ulyssesonline.com/2012/08/27/install-ventrilo-server-on-ubuntu-12-04/)

I followed it all exactly until I got the part where you start the server
```
$ sudo /etc/init.d/ventrilo start
```
it returns:
> sudo /etc/init.d/ventrilo start
 * Starting VOIP server ventrilo                                                [COLOR="Red"]sh: 1: /usr/bin/ventrilo_srv: not found[/COLOR]
cat: /etc/ventrilo/ventrilo_srv.pid: No such file or directory

Usage:
 renice [-n] <priority> [-p] <pid> [<pid>  ...]
 renice [-n] <priority>  -g <pgrp> [<pgrp> ...]
 renice [-n] <priority>  -u <user> [<user> ...]

Options:
 -g, --pgrp <id>        interpret as process group ID
 -h, --help             print help
 -n, --priority <num>   set the nice increment value
 -p, --pid <id>         force to be interpreted as process ID
 -u, --user <name|id>   interpret as username or user ID
 -v, --version          print version

For more information see renice(1).
                                                                         [ OK ]

But the file exists
> $ ls -la /usr/bin/ventrilo_s*
-rwxr-x--x 1 ventrilo ventrilo 468420 Nov 18  2008 /usr/bin/ventrilo_srv
-rwxr-x--x 1 ventrilo ventrilo  55032 Nov 18  2008 /usr/bin/ventrilo_status
(I chown-ed the files to ventrilo:ventrilo trying to get it to work but it had no effect)

The script is copied from the guide from this link
[http://www.benwagner.net/wp-content/uploads/2011/05/ventrilo.txt](http://www.benwagner.net/wp-content/uploads/2011/05/ventrilo.txt)

the error message is coming from line 14 which (variables expanded) reads:
```
 su ventrilo -c "/usr/bin/ventrilo_srv -f/etc/ventrilo/ventrilo_srv -d"
```

and it comes back saying /usr/bin/ventrilo_srv is not found when clearly it exists.

when I created the user (exactly as in the guide) I only did 
```
$ sudo useradd ventrilo
```
with no parameters or anything.
Later, I then did
```
$ sudo useradd ventrilo sudo
```
thinking it possibly needed sudo rights.  Same error message.

Is something wrong with the syntax of the script itself?

---

### Post by apokkalyps on 2012-12-27
Not sure why this thread got ignored.  The solution turned out to be that I needed to:

```
sudo apt-get install ia32-libs
```

---

