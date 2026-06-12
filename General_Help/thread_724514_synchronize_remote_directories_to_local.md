---
title: "synchronize remote directories to local"
date: 2008-03-14
forum: General Help
---

### Post by BLWedge09 on 2008-03-14
Ok, here's the situation.  I have a web hosting account where I am currently running a couple websites.  I have ssh, sftp, and ftp access to this account.  I have a directory on this server where I create database backups nightly.  I would like to be able to schedule something to run from my local pc, connect to my hosting account, and download the changed files from the db backup directory to my local pc.  I've looked around and haven't found exactly what I'm looking for.  I'm sure I could set up some sort of shell script that would do this for me, but I just haven't figured it out yet.  Surely someone out there already does this and could share a little knowledge. :)

---

### Post by bbukh on 2008-03-15
I use **rsync** for this purpose. Basically "rsync -r servername:dirname/ localdir/" is what you want. Depending on your configuration you might want to add additional options besides -r (see man page). For this the remote host needs to be have rsync installed (most standard install have it), and ssh. Use cron or anacron to schedule it to be run periodically. However, if you schedule it, note that you cannot enter the password at the terminal, and so you need to copy your private ssh key to .ssh/authorized_keys on the server (see ssh-keygen man page for more information). 

Boris

---

### Post by kevdog on 2008-03-16
You could also use a tool named unison, that runs rsync down below, but provides a slightly more feature rich set:
[http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)

---

### Post by BLWedge09 on 2008-03-16
> **kevdog said:**
> You could also use a tool named unison, that runs rsync down below, but provides a slightly more feature rich set:
[http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)

Unison requires that it be installed on both systems which is not an option for me on the remote machine.

---

### Post by BLWedge09 on 2008-03-16
> **bbukh said:**
> I use **rsync** for this purpose. Basically "rsync -r servername:dirname/ localdir/" is what you want. Depending on your configuration you might want to add additional options besides -r (see man page). For this the remote host needs to be have rsync installed (most standard install have it), and ssh. Use cron or anacron to schedule it to be run periodically. However, if you schedule it, note that you cannot enter the password at the terminal, and so you need to copy your private ssh key to .ssh/authorized_keys on the server (see ssh-keygen man page for more information). 

Boris

I'm running the rsync on one folder right now, however this intitial sync (which has to copy everything) is very slow.  It is slower than any copies that I have done via FTP or SFTP.  I realize this won't be much of an issue later when I'm copying only a few files nightly, but is there any particular reason why you'd expect this to be slow?

---

### Post by wieman01 on 2008-03-18
> **BLWedge09 said:**
> Unison requires that it be installed on both systems which is not an option for me on the remote machine.
Unison only requires a SSH server on the remote machine. You don't need to install 'rsync' or 'unison' if I remember correctly.

---

### Post by kevdog on 2008-03-18
I believe actually unison needs to be installed on the remote machine, since this is how it calculates if differences are present on the server since the last sync.  The same process happens simaltaneously on the client and at the end the two compare their results and then transfer using rsync the differences they find after conflicts presented to the user have been decided.

If you use rsync, this usually is installed by default on most linux installs so no need to install this!

Other than rsync/unison, I'm not aware of any tool that might do what you want.

---

### Post by wieman01 on 2008-03-18
> **kevdog said:**
> I believe actually unison needs to be installed on the remote machine, since this is how it calculates if differences are present on the server since the last sync.  The same process happens simaltaneously on the client and at the end the two compare their results and then transfer using rsync the differences they find after conflicts presented to the user have been decided.

If you use rsync, this usually is installed by default on most linux installs so no need to install this!

Other than rsync/unison, I'm not aware of any tool that might do what you want.
OK, I will confirm it tonight. You might be right, and I am not in front of my own machine. I recommend Unison nevertheless.

---

### Post by wieman01 on 2008-03-18
You were right, Kevdog, it's installed on both client and server. My bad.

---

### Post by kevdog on 2008-03-19
I used to use unison a lot but not so much anymore (gotten lazy with my backups).  I wanted to sync like 10GB replicas (I wanted to let the process run overnight so I didnt care if it were slow), but found thefollowing problems:

1. The connection would terminate in the middle of unison calculation (or time out)
2. If the connection started transferring files I could at most transfer 2Gb and then the systems would halt.  I noticed this too from my laptop to server using LAN router than even if using the cp command about 2Gb would be transferred before the connection would hang.

I got really discouraged after this!!

---

### Post by wieman01 on 2008-03-19
> **kevdog said:**
> I used to use unison a lot but not so much anymore (gotten lazy with my backups).  I wanted to sync like 10GB replicas (I wanted to let the process run overnight so I didnt care if it were slow), but found thefollowing problems:

1. The connection would terminate in the middle of unison calculation (or time out)
2. If the connection started transferring files I could at most transfer 2Gb and then the systems would halt.  I noticed this too from my laptop to server using LAN router than even if using the cp command about 2Gb would be transferred before the connection would hang.

I got really discouraged after this!!
Via SSH or SAMBA? SSH is really stable in my case.

---

### Post by kevdog on 2008-03-20
Both -- although SAMBA was a little bit more unstable crashing before the 2 Gb limit.  Never figured it out.  
This problem with the inability to sync really large file 2-3GB (movies) makes unison in some cases inconvienient.

---

