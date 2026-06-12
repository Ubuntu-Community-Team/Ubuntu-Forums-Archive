---
title: "Multiple user accounts - one home folder"
date: 2008-06-24
forum: General Help
---

### Post by x300 on 2008-06-24
I'd like to have multiple users on my server, but they shouldn't have different home folders (though some might have their own folders and limited restrictions). Example:

user a -> /home/a
user b -> /home/a
user c -> /home/a
user d -> /home/d

How do I do this?

---

### Post by rubicon on 2008-06-24
*adduser --home <dir>* ? Also, *man adduser* may help a lot.

---

### Post by x300 on 2008-06-24
Thanks, there's but one problem now.. when I login as [email]b@server.com[/email] I have to write 'bash' to actually load bash.. (the commands, the prompt, the tab-thingy...)

How do I do so that bash is automatically loaded? Cause everything else is fine now, the prompt is b@server:~$ and the home is a's.

edit: it's the same when i just make a new account... have to write bash to load bash...

---

### Post by Zorael on 2008-06-24
On a side note, you could just make the second user's home directory a symbolic link to your first user's.

```
$ sudo ln -s /home/firstuser /home/seconduser
```

---

### Post by x300 on 2008-06-24
Yeah, I actually tried that before I posted here, but then I got the problem with having to write bash whenever I log in, so I thought I'd try posting here... so it really doesn't change anything :P

thx anyway

---

### Post by rubicon on 2008-06-24
So, you're typing it on console? Then you got sh (/bin/sh) or some other shell at least (gladly not /usr/sbin/nologin :D ). You can specify user's shell by adduser switch (*--shell*, when creating user) or by *chsh* command (at later a time).

---

### Post by x300 on 2008-06-25
Thanks :D

Now it all works great. I just have to figure out how to give restricted access to some users. 

It may be off topic, but can anyone tell me how to give a user access to only read,write, and so on, in his OWN home folder. I don't even want him to have the access to see other directories!

---

### Post by rubicon on 2008-06-25
[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

---

### Post by x300 on 2008-06-25
thanks, but there must be a way to say that a certain user or group only has permission access a certain folder... not set the permissions for all files that they _can't_ access?

---

### Post by rubicon on 2008-06-25
So you want to forbid some user to access everything BUT his own folder (without much effort :D ), eh? 

Actually, what do you look for is ACL (as far as I understand you), it is supported for ext2 and ext3 volumes. Can't say anything particural &#8212; have never used acls since windows &#8212; but google helps a lot.

But you should know that everything a user launches **should** have access to /etc, /usr, and god-knows-what-else that's apparently not in his own home folder. Otherwise it is very likely **nothing** will work right or work at all. If I were you, I'd just lower access rights for users (exclude them from groups *src*, *admin*, *adm* and so on) so they *would* *see* all folders but just *couldn't write* there. This won't break anything and is very close to what I believe your intent is.

---

