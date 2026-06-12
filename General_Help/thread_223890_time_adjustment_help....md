---
title: "time adjustment help..."
date: 2006-07-27
forum: General Help
---

### Post by Xzallion on 2006-07-27
I just set up a webserver for a project im working on. I installed ubuntu server on it, got it all set up, and everything is working perfectly.  I just needed a way to transfer files to it easily.  so I set up a ssh server on the server, and connect to it through ssh.  I only know one way to transfer files to it, which is ```
scp <file> <username>@<ip address or hostname>:<destination directory>
```
Since that only transfers one file, I figured I would just create a .tar.gz file of all the files I would transfer to it, transmit the archive, and extract it on the server.  Thats where the problem comes in.  The servers clock is behind a few hours, so It says my archive is in the future.  using the ```
date
``` command...

Server: Wed Jul 26 22:38:58 CDT 2006
My pc: Thu Jul 27 03:42:26 CDT 2006

Now I don't know how to set the servers time through a terminal, can someone please tell me how to set the time through the terminal?

---

### Post by melissawm on 2006-07-27
I just did a

```
date --help
```

in my terminal: from what i gather, basically you have to do

```
sudo date --set=STRING 
```

where STRING is the date in the format you want, i.e.

```
date --set="Thu Jul 26 10:59:52 CEST 2006"
```

or something like this. Hope this helps...

---

### Post by Xzallion on 2006-07-27
Thanks, that did help.  I couldn't make heads or tails out of the man page for date, but then again it was 4 am in the morning also...

Thanks again!

---

