---
title: "how to move files from one pc to another using a P2P"
date: 2007-09-20
forum: General Help
---

### Post by kystorms on 2007-09-20
hi 

want to get files from one pc i have to my kids pc we are on net together, but not networking

anyway, is it possible to set up a private P2P just between their pc and mine, say with Frostwire, and if so, how would i do that?

:confused:

---

### Post by tszanon on 2007-09-20
> **kystorms said:**
> hi 

want to get files from one pc i have to my kids pc we are on net together, but not networking

anyway, is it possible to set up a private P2P just between their pc and mine, say with Frostwire, and if so, how would i do that?

:confused:
So both computers have internet connection, but they are not in the same LAN? Is that right?
You could use scp to copy the files. The server (your pc) must have a ssh server installed (if I recall correctly, it's called openssh-server, or just openssh).

---

### Post by kystorms on 2007-09-20
oh wow, okay, is this a program i can download via synaptic?

thanks for the reply to my question:)

---

### Post by tszanon on 2007-09-21
> **kystorms said:**
> oh wow, okay, is this a program i can download via synaptic?

thanks for the reply to my question:)
Yes, it's available in the repositories. The server (the machine that will receive the connection) needs openssh-server. Openssh-client is installed by default in Ubuntu. If I recall correctly, the command line should be like this:

1. If you are at your pc and wants to send the files to the other pc:
```
scp /path.to.file/filename user@ip.of.other.pc:/destination/path
```
Example:
```
scp /home/kystorms/myvideo.avi joe@200.10.20.100:/home/joe
```
In this case, the other pc will need openssh-server installed.

2. If you are at your kid's pc:
```
scp yourlogin@your.pc.ip.address:/path/to/file/filename /destination/path
```
Example:
```
scp kystorms@200.30.40.50:/home/kystorms/myvideo.avi /home/joe
```
In this case, your pc will need openssh-server installed.

Remember that you will have the same access permissions as the login you use to access the pc. When accessing your kid's pc from yours, you will have the same permissions that the user joe has.

scp uses ssh to make the connection and transfer the files. So, if the server has a router, you will probably need to open port 22 in the router.

---

### Post by kystorms on 2007-09-21
awesome thank you so much for the code

I am sorry i am just now getting back to you, hectic week!

again thanks so much for everyones help

:-)

---

### Post by tszanon on 2007-09-21
> **kystorms said:**
> awesome thank you so much for the code

I am sorry i am just now getting back to you, hectic week!

again thanks so much for everyones help

:-)
Nevermind, a lot of people here have a job too. We know what it means! :)
If you have any problems, just ask!

---

