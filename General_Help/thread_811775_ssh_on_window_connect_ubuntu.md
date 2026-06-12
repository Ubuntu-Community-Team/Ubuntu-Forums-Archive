---
title: "ssh on window connect ubuntu"
date: 2008-05-29
forum: General Help
---

### Post by moonhk on 2008-05-29
Hi All

ubuntu before is 6.06. Now Upgraded to 8.04

Below problem how to fix ?

It try to remove /home/Administrator/.ssh/known_hosts. Not ok

c:\temp>ssh moonhk@hex
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@       WARNING: POSSIBLE DNS SPOOFING DETECTED!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
The RSA host key for hex has changed,
and the key for the according IP address 192.168.0.99
is unknown. This could either mean that
DNS SPOOFING is happening or the IP address for the host
and its host key have changed at the same time.
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
3b:ea:a8:e4:73:a2:af:51:*******************
Please contact your system administrator.
Add correct host key in /home/Administrator/.ssh/known_hosts to get rid of this message.
Offending key in /home/Administrator/.ssh/known_hosts:3
RSA host key for hex has changed and you have requested strict checking.
Host key verification failed.

c:\temp>moonhk@hex:~$

---

### Post by EndPerform on 2008-05-29
Since you upgraded, new keys were generated, it seems.  Just remove the known_hosts file and it will create a new one.

---

### Post by moonhk on 2008-05-29
Tried. OK Not.

---

### Post by Joeb454 on 2008-05-29
You need to change the keys on your Window machine as well, though I can't give much advice on that :)

---

### Post by Slim Odds on 2008-05-29
> **Joeb454 said:**
> You need to change the keys on your Window machine as well, though I can't give much advice on that :)

Not true......

It's complaining about the host, not the client

It is actually telling exactly which line in the known_host file that is doesn't like:

>>> Offending key in /home/Administrator/.ssh/known_hosts:3

Line 3

---

### Post by lotsofish on 2008-05-29
Are you trying to log in with SSH from Windows or from Linux?

The line: 
c:\temp>moonhk@hex:~$
: confuses me.

If you are logging in to SSH from Linux, then you need to edit or delete your /home/Administrator/.ssh/known_hosts file. If you are trying to log in from Windows, I know putty will give you a warning but let you use the new key anyway.

---

### Post by Slim Odds on 2008-05-30
> **lotsofish said:**
> Are you trying to log in with SSH from Windows or from Linux?

The line: 
c:\temp>moonhk@hex:~$
: confuses me.

If you are logging in to SSH from Linux, then you need to edit or delete your /home/Administrator/.ssh/known_hosts file. If you are trying to log in from Windows, I know putty will give you a warning but let you use the new key anyway.

Dude, a little reading comprehension?

His **title** says "ssh on WINDOWS to UBUNTU". 

that would be **FROM WINDOWS**  ---> [B]TO LINUX.

[/B]Don't be confused, his command line was-> c:\temp>ssh moonhk@hex

So he's using ssh, not putty

---

### Post by Joeb454 on 2008-05-30
putty is an ssh client for Windows from what I recall. And there's no need to get all offensive to lotsofish, I got confused the first time I saw it, I had to re-read it

---

### Post by dagnabit dang doohickey on 2008-05-30
The known_hosts file on the computer you're connecting **from** has a mismatched/obsolete/just-plain-wrong host key in it. Deleting the offending key or the whole file should solve the problem.

The original post/title is so vague and lacking in detail, the thread is turning into Abbott and Costello's *Who's On First* bit.

---

### Post by Francewhoa on 2009-06-26
Removing file 'known_hosts' works for me.

This file is located on your local computer. Not the remote computer. File location is:
/home/Administrator/.ssh/known_hosts

In above path 'Administrator' should be replace by the Ubuntu username you're currently using. If unsure delete the file 'known_hosts' for all Ubuntu username folders.

If you can't find the folder '.ssh' it's because this folder is a hidden folder. If you are using gnome you would go to the home folder and then View > Show Hidden Files (or hit Ctrl + H). You should be able to find .ssh after that.

---

