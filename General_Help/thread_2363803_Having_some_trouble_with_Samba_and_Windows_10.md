---
title: "Having some trouble with Samba and Windows 10"
date: 2017-06-14
forum: General Help
---

### Post by Cursed Lemon on 2017-06-14
Alright, so purely as an exercise of "because I can", I have a small spare computer operating as a kind of media server running Ubuntu Server 16.04 on it, along with a separate XFS partition that holds said media which is shared via Samba. 

What I am trying to accomplish is to have this XFS media partition accessible as read-only to guests, but writable by the "master" account. The problem is that Windows 10 is able to access this Samba share as a network place, and write to it regardless of who is connected to it. This occurs whether I just open it through Windows' network browser, or map the share as a network drive. 

The relevant fstab entry: 

```
UUID=(SOME NUMBERS AND LETTERS)                   /mnt/Samba                 xfs              defaults                0                 2
```

Testparm gives me:

```
[XFS Share]
       path = /mnt/Samba
       valid users = master
       write list = master
```

The relevant smbd.conf section:

```
[XFS Share]
       path = /mnt/Samba
       guest = ok
       valid users = master
       read only = yes
       write list = master
```

Not really sure why my testparm is different than my smbd.conf.

I noticed that when I tried mounting the XFS partition as "ro" for read-only in fstab, access was properly restricted (albeit to everyone, including the master account). 

Anyone got any bright ideas as to what I'm screwing up?

---

### Post by aromo2 on 2017-06-14
filesystem should be mounted read-write, otherwise, as you experieced, no-one (including root in a shell session) won't be able to write on it.
in smbd.conf, read only should be set to no to make the share read-writeable. Then you control who can read or write with valid users and write list.

---

### Post by Morbius1 on 2017-06-14
I'm actually having a problem understanding your description of how this is working for you.
> Not really sure why my testparm is different than my smbd.conf.
> [XFS Share]
       path = /mnt/Samba
       guest = ok
       valid users = master
       read only = yes
       write list = master

[COLOR=#0000cd]**First off there is no such thing as "guest = ok" so I'm assuming you meant to post "guest ok = yes".**[/COLOR]

testparm is an interpreter so it sees that you will allow anyone access ( guest ok = yes ) but then you specify only one user has access ( master ) so it's no longer a guest share. Similarly, you made it read only which is the default on all shares so that will be ignored by testparm. But then you specify a write list to the only user that has access to it in the first place. A "write list" always overrides a "read only" setting. The result is samba ( testparm ) throwing out the things that are irrelevant or overridden:
> [XFS Share]
       path = /mnt/Samba
       valid users = master
       write list = master
The part of your post I'm having a problem with is this:

> The problem is that Windows 10 is able to access this Samba share as a 
network place, and write to it regardless of who is connected to it.
That share should only be accessible to the user "master".

Anyhoo, I don't like to create convoluted share definitions so what I would do is create two shares - with different names - one allowing write access only to "master" and another one that allows anyone access - but read only:
> [XFS Share-Public]
       path = /mnt/Samba
       guest ok = yes
read only = yes
       
[COLOR=#0000cd]*I added the "read only = yes" so that it's apparent what I'm doing. If you were to run testparm that line would be removed.*[/COLOR]

---

### Post by Cursed Lemon on 2017-06-14
> **Morbius1 said:**
> I'm actually having a problem understanding your description of how this is working for you.



[COLOR=#0000cd]**First off there is no such thing as "guest = ok" so I'm assuming you meant to post "guest ok = yes".**[/COLOR]Yeah I mistyped that, I was just copying it down from another screen. 

> testparm is an interpreter so it sees that you will allow anyone access ( guest ok = yes ) but then you specify only one user has access ( master ) so it's no longer a guest share. Similarly, you made it read only which is the default on all shares so that will be ignored by testparm. But then you specify a write list to the only user that has access to it in the first place. A "write list" always overrides a "read only" setting. The result is samba ( testparm ) throwing out the things that are irrelevant or overridden:

I'm not too sure which variables override others and in what order, which is why I did a lot of mixing and matching before making this thread. 

> The part of your post I'm having a problem with is this:


That share should only be accessible to the user "master".

It's quite accessible by navigating through Windows' network browser, selecting the machine on the network, then selecting the share. No login prompted, no difficulty writing to the share. 

> Anyhoo, I don't like to create convoluted share definitions so what I would do is create two shares - with different names - one allowing write access only to "master" and another one that allows anyone access - but read only:

[COLOR=#0000cd]*I added the "read only = yes" so that it's apparent what I'm doing. If you were to run testparm that line would be removed.*[/COLOR]

Wasn't aware that you could create two shares referencing the same resource, that might be easier then. I'll give it a shot.

---

### Post by Morbius1 on 2017-06-14
> It's quite accessible by navigating through Windows' network browser,  selecting the machine on the network, then selecting the share. No login  prompted, no difficulty writing to the share. 
The only way I know of where that is possible relies on a curious quirk in Windows where the user automatically passes - without his knowledge - his own login user name and login password when accessing a share.

But for it to work in this case:

"master" has to be the user that is currently logged into Windows.
The Samba server must have the same user with a samba password that matches the Windows user's login password on the Windows box.

Then access to the share appears to be seamless since the correct user name and password has already been sent.

---

### Post by Cursed Lemon on 2017-06-14
The two accounts are definitely different, I can tell you that. It's pretty mystifying.

---

### Post by sp40140 on 2017-06-15
Since your testparm and conf provide different info, is it possible that you have more than one smb.conf files?
Can you confirm which one are you editing? and after each edit are you re-starting samba service?

Edit: which version of Ubuntu / samba are you using? May be there is mismatch with samba server and win10!

---

### Post by Cursed Lemon on 2017-06-15
> **sp40140 said:**
> Since your testparm and conf provide different info, is it possible that you have more than one smb.conf files?
Can you confirm which one are you editing? and after each edit are you re-starting samba service?

Edit: which version of Ubuntu / samba are you using? May be there is mismatch with samba server and win10!

Definitely only one smb.conf file in the /etc/samba directory. 

Whatever Samba version is what Ubuntu Server installed on the initial installation, where you can pick extra features/utilities, and the system is up to date. 

Later on tonight I'll do a clean installation again, and maybe do a screen capture video showing my woes.

---

### Post by Morbius1 on 2017-06-16
>  Later on tonight I'll do a clean installation again, and maybe do a screen capture video showing my woes.         
If you are doing a re-installation because of a samba issue that may not be necessary. All you need to do is reset smb.conf.

Make a backup copy of the one you are using now
```
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.bak
```
Then copy over a backup default config file that Ubuntu always has for situations like this:
```
sudo cp -a /usr/share/samba/smb.conf /etc/samba/
```
Make whatever changes you want to make in that file then restart smbd:
```
sudo service smbd restart
```

[COLOR=#0000cd] Side note: This is probably not the way you want to use this share but you might consider the following:[/COLOR]

** Create a share that looks like this:
```
[XFS Share]
       path = /mnt/Samba
       read only = yes
       write list = master                      
```

The "write list" will cause the server to ask everyone who tries to access that share for credentials so that it can determine if that user is on the list. What I do is create a guest user called smbguest and give it a samba password of smbguestpw ( literally - something easy to remember ).

When Agnes tries to access the share she will provide the smbguest/smbguestpw  combination and will be limited to read only access. When master accesses the share with his credentials he will will be granted write access.

BTW, If you do a testparm -s your [XFS Share] will look like this - without the read only line - which is fine:
```
[XFS Share]
       path = /mnt/Samba
       write list = master                      
```

---

### Post by Cursed Lemon on 2017-06-18
Checking back in. So I got it working and I have absolutely zero idea why or how, since this is not really any different from what I was trying before. 

Share is formatted like so:

```
[XFS Media Share][INDENT]path = /mnt/Samba
browsable = yes
guest ok = yes
read only = yes
write list = master
create mask = 0755[/INDENT]

```

Testparm says: 

```
[XFS Media Share][INDENT]path = /mnt/Samba
write list = master
create mask = 0755
guest ok = Yes[/INDENT]

```
The XFS partition is owned by the user "master". I'm now able to read the share but not write to it in Windows unless I map the share as a network drive and provide credentials for the "master" account. 

To this I give the biggest SHRUG in history.

---

