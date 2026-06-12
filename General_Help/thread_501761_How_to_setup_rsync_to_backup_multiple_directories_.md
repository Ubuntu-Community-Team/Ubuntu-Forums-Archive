---
title: "How to setup rsync to backup multiple directories on different drives?"
date: 2007-07-15
forum: General Help
---

### Post by george_k on 2007-07-15
Hi,

I'm trying to figure out how to get rsync to backup various folders (some located on different drives) onto an external USB hard drive (i.e. a local backup)

How do you get rsync to backup multiple directories?

---

### Post by HermanAB on 2007-07-15
Simple: Make a script and call rsync multiple times.

---

### Post by george_k on 2007-07-24
Thanks Herman

Just a few follow-up questions about the script, here's what I got so far:

```

# rsync backup script
rsync -av /home/george/test1 /media/nexstar
rsync -av /home/george/test2 /media/nexstar
rsync -av /home/george/test3 /media/nexstar

```

1) Will such a piece of code execute all three commands at the same time or will it be done sequentially?

2) If I wanted to add the --log-file option do I need to enter it for every entry like I've done below:
```

rsync -av --log-file/media/nexstar/rsync.log /home/george/test1 /media/nexstar
rsync -av --log-file/media/nexstar/rsync.log /home/george/test2 /media/nexstar
rsync -av --log-file/media/nexstar/rsync.log /home/george/test3 /media/nexstar

```

3) I noticed that if I delete a file from src and then re-run rsync the same file doesn't get deleted on the destination drive...is there a way to setup this type of mirror that way the destination is always a mirror of the source?

4) In what instance would it make sense to use the rsync daemon as opposed to what I'm doing now?

Thanks :-)

---

### Post by HermanAB on 2007-07-24
Hmm, scripts are executed line by line, top to bottom, just as if you typed the commands manually.  Each line stands on its own legs.

Deleting files at the destination is dangerous and probably best avoided, since an error can cause enormous grief.  It can be done using the '--delete' option, but I sure won't use it!

Rsync work like a better copy command when run on a single machine.  When you wish to transfer files over a network to another machine, then you need something at the distant machine that will listen for a connection attempt and do whatever needs to be done over yonder.  If the two machines are on a safe and secure LAN, then you can use the rsync daemon.  If the distant machine is somewhere else on the internet, then you need to use SSH as the distant daemon, since is safe and secure.  

I have never used the rsync daemon, but I use SSH every day and I have several machines that run automated backups using rsync and sshd.  This can even be made to work on Windows, using Cygwin and OpenSSH.

'Hope that helps!

Herman

---

### Post by MobiusNZ on 2008-01-13
It's been a while since any posts on this, but you don't have to put them on separate lines.
```
rsync /source/dir1 /source/dir2 .... /dest
```
Much easier!

---

