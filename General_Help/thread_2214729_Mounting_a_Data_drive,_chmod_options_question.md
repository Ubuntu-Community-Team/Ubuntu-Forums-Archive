---
title: "Mounting a Data drive, chmod options question"
date: 2014-04-02
forum: General Help
---

### Post by mikodo on 2014-04-02
Hi,

When setting up mounting of a data drive, I was told by oldfred to use Chmod thusly, with the following options for it.

```
sudo chmod -R a+rwX /mnt/data
```

I just saw in another thread where oldfred suggested these chmod options:

```
sudo chmod -R a+rwX,[COLOR=#0000ff]o-w[/COLOR] /mnt/data
```

[Penquin Guy]("http://ubuntuforums.org/showthread.php?t=1252905") explains the chmond options of [COLOR=#0000ff]o-w[/COLOR] as (deny others from editing the file).

I am the only user on this system.

 **Should I bother adding the chmod[COLOR=#0000ff] o-w[/COLOR] options?**

Thanks.

---

### Post by Tristan_Williams on 2014-04-02
If you are the only user, no don't worry about it.

Those options are for multi-user systems and systems on a network in which someone on the network could access your system.

---

### Post by bab1 on 2014-04-02
> **mikodo said:**
> ...

I am the only user on this system.

 **Should I bother adding the chmod[COLOR=#0000ff] o-w[/COLOR] options?**

Thanks.
You are not the only user of the system.  You may be the only mortal (human) user.  There are system users to worry about also.  When an application runs it runs under at system users control.  It's not in your best interests to make a directory available for reading and writing to or worse yet; available for a script to be executed in.  The *others* group is all the users (mortal or system) that operate on the host (system).  The question is;  how big a risk is this?  That depends upon your situation.  Is this host connected to the Internet?  What applications are installed and used?  In my opinion there is no need to allow *others* to have that type of authorization.  So I make the others permissions at read only.

To see what users are running at the moment you can run either of these commands at the terminal prompt```
ps -ef

top
```

---

### Post by mikodo on 2014-04-02
Thanks guys,

I don't what all the services are, that are running when I check with ps -ef and top. 

So, I am going to include the chmod o-w options. It won't hurt and may be helpful, some day.

---

