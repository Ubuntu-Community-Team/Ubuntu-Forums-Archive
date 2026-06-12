---
title: "ssh Permission denied (publickey,password)"
date: 2017-01-17
forum: General Help
---

### Post by pranithkumar2 on 2017-01-17
I am trying to ssh to my college server from home then I get this error after attempting to enter the password thrice.
The password is correct as I was able to login to the server locally.
Can I get any help.

---

### Post by QIII on 2017-01-17
Hello!

What error are you getting?

Have you spoken to the IT department at your school?

---

### Post by pranithkumar2 on 2017-01-17
$ ssh user@host
user@host's password: 
Permission denied, please try again.
user@host's password: 
Permission denied, please try again.
user@host's password: 
Permission denied (publickey,password).

---

### Post by efflandt on 2017-01-17
Your ~/.ssh directory and any files in it on client or server should only have permission for you (no permissions for group or others). So the directory should have 700 permission (-drw------) and any files in it should have 600 permission (--rw------). Otherwise ssh or sshd might not trust it if anybody else could access that directory or files. You may run into that problem if you use FAT32 flash or something to copy the directory to another machine, because FAT32 has no concept of permissions.

---

### Post by pranithkumar2 on 2017-01-18
Okay but can I do anything without accessing the server?

---

### Post by efflandt on 2017-01-22
Sorry I cannot tell if private message replies are working, since my Sent Items remains at 0.

If you cannot get any remote access to the server (ssh, telnet, ftp), you would need physical access to it.

To recursively change permissions of ~/.ssh and anything under it to remove any permissions for group or others on your client computer and server when you can access it:```
chmod -R go-rwx ~/.ssh
```Of course ssh running as you or sshd as root can still access that to get at authentication keys or known_hosts.

---

### Post by QIII on 2017-01-22
Hello!

If you are providing support via PM, please don't do that.  That robs the community of information that might be helpful to other members in the future.

Thanks!

---

### Post by The Cog on 2017-01-22
I think you should talk to the server admins. 
If I was setting a server up for the students like that, I would probably edit the config to only allow users to connect (correction: only allow login) if they were inside the campus network. Leaving an SSH server with multiple valid user/password open to the internet is asking to be hacked by password guessing bots. 
They may well have thought the same thing, in which case you won't get in from home at all.

EDIT. 
I meant only allow users to log in using name+password from the campus network. 
Some admins might be allowed to use passwordless (using keys) access from outside so they can administer from home if needed.

---

### Post by Habitual on 2017-01-22
> **pranithkumar2 said:**
> I am trying to ssh to my college server from home then I get this error after attempting to enter the password thrice.
The password is correct as I was able to login to the server locally.
Can I get any help.

I believe it wants a keyfile, something you and the server admin should have worked out.
```
ssh -i /home/user/.ssh/key user@host
```

There is nothing you can "do" without the server admin's help. IMO.
What you can "do" on a live server is not what you can do via ssh.
There's a few ways to inhibit dictionary attacks on guessing usernames via ssh, 
```
PasswordAuthentication no
``` is one of them.

---

### Post by pranithkumar2 on 2017-01-23
The problem is solved.
Thanks.

---

