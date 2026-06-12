---
title: "Error: No such file or directory"
date: 2008-02-27
forum: General Help
---

### Post by greenlime on 2008-02-27
I'm trying to run this client program for our daily server backups.  My question is about an error I'm seeing and it's more of a general Linux question than a specific one about the program I'm trying to run.  We have 2 Ubuntu servers (identical), one is running the program already and I'm trying to get it to run on the other server.  I ran the install.sh on the new server and everything worked as planned except for one thing.  On the new server I've installed it on when I try to run the client program (binary executable not a .sh script) I get the following error:

root@newserver:~$ /usr/local/dantz/client/retroclient start
unable to execute /usr/local/dantz/client/retroclient: No such file or directory

on the old server where it's been running it works just fine:

root@oldserver:~$ /usr/local/dantz/client/retroclient start
Retrospect client is already running

Now before someone tells me to call Retrospect support here's where it's a basic Linux question...  I've tar'ed, scp'ed, & untar'ed the file from the old server to the new server so it is absolutely identical.  Again the servers are identical hardware-wise.  Why does the new server refuse to acknowledge that the file even exists?  I've seen reports where it gives this message if a shell script is in dos format or whatever but I literally copied the same file from the old server to the new and the new server doesn't recognize it.  Any insight would be greatly appreciated.

---

### Post by Mr. C. on 2008-02-27
```
ls -l /usr/local/dantz/client
```

MrC

---

### Post by Nameless_one on 2008-02-27
It looks like a permissions problem. If you know what that is and have checked it, then sorry for the long post :D otherwise, here is a little info (MrC seems to think the same as me) :

Files have permissions, to read, write and execute them. Also, files belong to a user and a group of users, and each have different permissions on the file. Your problem seems to be that either you don't have execute permissions for the program, or it belongs to a different user, and the public permissions for the program do not allow execution.

You can check the permissions of the file by running the command MrC has posted above: 
```
ls -l /usr/local/dantz/client
```
There will be a line in the output that will look something like this:
```
-rwxr-xr-x  1 nameless nameless 5.6M 2007-07-12 16:56 RealPlayer10GOLD.bin
``` 

only for the retroclient program. What you want is, where it says 'nameless' in my example, to be your username. 
Also to the left, where there are lots of x's and r's and w's (actually eXecute, Read and Write permission flags), there has to be an 'x' on the fourth column. If it isn't like that, then that's the problem, so paste your terminal output here so that we can tell you how to fix it. If everything is fine, then it's something else.

---

### Post by greenlime on 2008-02-28
Thanks for replying.  Yes I already checked permissions and everything seems legit and absolutely matches what I have on the old server where it works fine.  Remember that I'm running this as root as well.  Here's an ls I copied for the new & old server:

root@newserver:~$ ls -l /usr/local/dantz/client/retroclient
-rwxr-xr-x 1 root root 509762 2004-12-13 10:24 /usr/local/dantz/client/retroclient

root@oldserver:~$ ls -l /usr/local/dantz/client/retroclient
-rwxr-xr-x 1 root root 509762 2004-12-13 10:24 /usr/local/dantz/client/retroclient

---

### Post by Mr. C. on 2008-02-28
I still want to see the permissions of the directory components leading up to the program.
```

ls -ld /usr
ls -ld /usr/local
ls -ld /usr/local/dantz
ls -ld /usr/local/dantz/client
```

Also, what is the executable type of that file?
What is the architecture of that file?

```
file /usr/local/dantz/client/retroclient
arch
uname -a
id

```

The messages is not coming from retroclient - that message is nowhere to be found in the 7.5, 7.0, nor 6.5 retroclient package for Linux.

MrC

---

### Post by greenlime on 2008-02-29
OK I've ran those commands on both my new machine and old machine (which works).  Here's the output:

New Machine:

```
root@newserver:# ls -ld /usr
drwxr-xr-x 11 root root 4096 2008-02-13 08:24 /usr
root@newserver: ls -ld /usr/local
drwxr-xr-x 10 root root 4096 2008-02-21 16:27 /usr/local
root@newserver:# ls -ld /usr/local/dantz
drwxr-xr-x 3 root root 4096 2008-02-21 16:27 /usr/local/dantz
root@newserver:# ls -ld /usr/local/dantz/client/
drwxr-xr-x 3 root root 4096 2008-02-25 12:23 /usr/local/dantz/client/
root@newserver:# file /usr/local/dantz/client/retroclient
/usr/local/dantz/client/retroclient: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.0.0, dynamically linked (uses shared libs), for GNU/Linux 2.0.0, not stripped
root@newserver:# arch
x86_64
root@newserver:# uname -a
Linux newserver 2.6.15-51-amd64-server #1 SMP Thu Dec 6 20:43:50 UTC 2007 x86_64 GNU/Linux
root@newserver:# id
uid=0(root) gid=0(root) groups=0(root)
```

Old Machine:

```
oldserver# ls -ld /usr
drwxr-xr-x 12 root root 4096 2006-08-17 12:44 /usr/
oldserver# ls -ld /usr/local
drwxr-xr-x 10 root root 4096 2006-09-06 09:00 /usr/local/
oldserver# ls -ld /usr/local/dantz
drwxr-xr-x 3 root root 4096 2006-09-06 09:00 /usr/local/dantz/
oldserver# ls -ld /usr/local/dantz/client/
drwxr-xr-x 2 root root 4096 2008-02-25 12:19 /usr/local/dantz/client//
oldserver# ls -ld /usr/local/dantz/client/
drwxr-xr-x 2 root root 4096 2008-02-25 12:19 /usr/local/dantz/client//
oldserver# file /usr/local/dantz/client/retroclient
/usr/local/dantz/client/retroclient: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.0.0, dynamically linked (uses shared libs), for GNU/Linux 2.0.0, not stripped
oldserver# arch
x86_64
oldserver# uname -a
Linux oldserver 2.6.15-27-amd64-server #1 SMP Fri Dec 8 18:02:49 UTC 2006 x86_64 GNU/Linux
oldserver# id
uid=0(root) gid=0(root) groups=0(root)
```

As you can see I think what it's saying is that the executable is 32-bit but the machine is 64-bit but like I said, it works on the old machine which has the same executable & architecture as the new machine.

---

### Post by Mr. C. on 2008-02-29
See: [http://ubuntuforums.org/showthread.php?t=468294](http://ubuntuforums.org/showthread.php?t=468294)

---

### Post by greenlime on 2008-02-29
I really appreciate the help.  I was missing linux32 and ia32-libs as was mentioned in the linked post & now all is well. :)

---

### Post by Mr. C. on 2008-02-29
You're welcome.  As soon as I saw the 64bit arch, I knew the solution.

Cheers.

---

