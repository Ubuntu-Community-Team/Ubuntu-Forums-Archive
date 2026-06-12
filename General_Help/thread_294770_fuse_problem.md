---
title: "fuse problem"
date: 2006-11-07
forum: General Help
---

### Post by pgilmon on 2006-11-07
Hi all,

I use fuse to mount an sftp folder in my home folder. At the beggining everything works allright, and I'm able to work with the mounted folder as if it is just a local folder, but it always ends up making my system slow: nautilus never ends loading the files in that folder, some application won't even open (rhythmbox), etc.

I have tried with two different sftp servers, so looks like it has to do somthing with either fuse or my configuration. When I want to mount an sftp folder I use:

sshfs [email]username@server.net[/email]:/folder /home/user/mountpoint

Any ideas?

---

### Post by rfs1970 on 2007-06-28
Hi There,

I am having the very same problem here... sshfs make my nautilus very slow... 
did you find any solution for this problem ?

---

