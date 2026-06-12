---
title: "kubuntu 14.04 - do I  need mlocate?"
date: 2015-08-20
forum: General Help
---

### Post by apmcd47 on 2015-08-20
I'v just installed Kubuntu 14.04 (Trusty) onto a new system and checking which packages are installed on my old system for installation on the new. I saw that the mlocate package is installed, the database file taking about 30Mb of disk space on my current system. While this is not an awful lot for modern disks it does seem like an overhead that is worth reducing if I can, as I intend copying over the entire home directory of the old system.

So  if I  remove mlocate what would I be breaking? A file manager? The only file managers I use are the command line (I don't use anything like midnight commander) and dolphin.

Before I posted this query I searched these fora for anything on locate/mlocate. and the general impression I get is the package is useless. Typing:```
locate foo
``` is the equivalent of ```
find / -type f -print | grep foo
``` (except that for the first find it is quicker). I normally look from the current location down the filestore. I normally look for particular files by name, but locate searches for patterns in the full filepath. To make locate do anything sensible you would have to write shell wrappers. And then there is the problem of new files. If I extract files from a tar of zip archive, or download a project from an SVN or git repository I cannot use locate until I've cached the files. And assuming I had permissions to use sudo to run the updatedb command would it not be quicker to just run find?

So, back the the subject line: given mlocate has no value to me, can I remove it safely without breaking anything?

While I am interested specifically in Kubuntu Trusty it may be useful to know of specific flavours or releases where it is not safe to do so for future reference.

Andrew

---

### Post by dino99 on 2015-08-20
i should not say it useless :o (but as i have no clue about Kubuntu, maybe they have set an alternative)

mlocate is a new implementation of locate, a tool to find files anywhere in the filesystem based on their name, using a fixed pattern or a regular expression. Unlike other tools like find(1), locate uses a previously created database to perform the search, allowing queries to execute much faster. This database is updated periodically from cron.

---

### Post by matt_symes on 2015-08-20
Hi

These are the reverse dependencies of mlocate.
```

matthew-laptop:/home/matthew:5 % acrd mlocate
mlocate
Reverse Depends:
  kubuntu-active
  mlocate:i386
  xfce4-linelight-plugin
 |texmacs
  phatch-cli
  kubuntu-active
 |gnome-do-plugins
 |catfish
  ubuntu-standard
 |findutils
matthew-laptop:/home/matthew:5 %
```

Do you use any of them ?

EDIT: BTW findutils only suggests mlocate.

```
matthew-laptop:/home/matthew:5 % acde findutils
findutils
  PreDepends: libc6
 |Suggests: mlocate
  Suggests: locate
    locate:i386
  Conflicts: findutils:i386
matthew-laptop:/home/matthew:5 % 
```

Kind regards

---

### Post by tgalati4 on 2015-08-20
mlocate/locate is a framework like many that linux is built on.  Who knows what application will use mlocate when you really need it?  If you delete it, then you save some space, but somewhere down the line, you will break something that uses it.  Because it is an indexed framework, it can find things much quicker.

It might even break *apropos*:

```
apropos locate
```

Although *which* doesn't use it, *whereis* might.

```
which which
whereis which
which whereis
```

I wouldn't delete it, but then it's your system.  You are allowed to break your own system.

---

### Post by matt_symes on 2015-08-20
Hi

@tgalati4. I always thought mlocate was taken out of findutils because it wasn't a core component.

You've really got me thinking so I'm going to have a play as you post some good stuff.

Kind regards

---

### Post by apmcd47 on 2015-08-20
Thank you all for taking the time to reply. I'm sorry if this makes me sound like a complete jerk, but:
> **dino99 said:**
> 
mlocate is a new implementation of locate, a tool to find files anywhere in the filesystem based on their name, using a fixed pattern or a regular expression. Unlike other tools like find(1), locate uses a previously created database to perform the search, allowing queries to execute much faster. This database is updated periodically from cron.
This sounds like it came out of the manual page. I know the above - I found it out by reading the documentation and other posts on this forum. Find creates a cache when it runs the first time, making subsequent finds faster, and the cache is fresher!

> **matt_symes said:**
> Hi

These are the reverse dependencies of mlocate.
```

matthew-laptop:/home/matthew:5 % acrd mlocate
mlocate
Reverse Depends:
  kubuntu-active
  mlocate:i386
  xfce4-linelight-plugin
 |texmacs
  phatch-cli
  kubuntu-active
 |gnome-do-plugins
 |catfish
  ubuntu-standard
 |findutils
matthew-laptop:/home/matthew:5 %
```

Do you use any of them ?

EDIT: BTW findutils only suggests mlocate.

```
matthew-laptop:/home/matthew:5 % acde findutils
findutils
  PreDepends: libc6
 |Suggests: mlocate
  Suggests: locate
    locate:i386
  Conflicts: findutils:i386
matthew-laptop:/home/matthew:5 % 
```

Kind regards
Thanks for this. Are acde and acre your own utilities? I couldn't find them on my system, or in the repository. Of the packages above, the only ones I would want on my system have mlocate as suggestions rather than required, so I may be safe there.

> **tgalati4 said:**
> mlocate/locate is a framework like many that linux is built on. Is it a framework? Or is it just a utility? >  Who knows what application will use mlocate when you really need it?  If you delete it, then you save some space, but somewhere down the line, you will break something that uses it.  Because it is an indexed framework, it can find things much quicker.Aren't you just turning round the question I asked above? I asked if it will break something, and you are saying it **will** break something. But I want to know what.> 

It might even break *apropos*:

```
apropos locate
```
I think apropos is part of the man-db package, which does not mention locate/mlocate in it dependencies or suggestions.> 
Although *which* doesn't use it, *whereis* might.

```
which which
whereis which
which whereis
```

I wouldn't delete it, but then it's your system.  You are allowed to break your own system. I suspect which and whereis (neither of which I have used for over 20 years) both predate mlocate enough to not depend on it. 

So, to my question "is it safe to remove mlocate or will it break something?" you answer "you can remove it if you like but don't blame me if it breaks something"

As I said before, thanks for your time, and sorry if I sound ungrateful or like a jerk.

Andrew

---

### Post by matt_symes on 2015-08-20
Hi

acde and acrd are aliases I have stored in a file that gets referenced by my .zshrc file. I use zsh as my shell and not bash.

All the reverse dependencies are recommends or suggests and not hard dependencies.

I've been looking at some of the lower utilities such as whereis and apropos. You'll be fine with them as they don't use locate or the locate database at all and I'm pretty sure the rest of the lower level utilities will be as well.

I have verified this using strace, readelf, ldd and objdump so far. I can post it later if you like.

So it all depends on what forks and execs mlocate at a higher level in kubuntu....

I use xubuntu but I may install kubuntu in a VM and play more tomorrow evening.

Do heed tgalati's warning though. If you want to be more sure then wait and I'll keep looking.

Kind regards

---

### Post by apmcd47 on 2015-08-20
Thanks for looking into this, Matt, but you really don't need to put so much effort into it. 

Andrew

---

### Post by matt_symes on 2015-08-20
Hi

Thanks Andrew :)

One of the reasons I post on this forum is because I can look at problems that may not happen on my machines so it has been no problem. 

That being said, I have been meaning to add a WOL and shutdown option to openELEC on my Raspberry Pi to wake and shutdown my media server and so save me electricity. That'll now be my evening planned tomorrow then.

I think you'll be fine uninstalling mlocate but if you have the least bit of doubt then image your partition first so you can restore.

Kind regards

---

### Post by tgalati4 on 2015-08-20
The only reason I call *mlocate* a framework is because it creates a database and updates that database every time something new is installed to the system.  So it acts as a system resource, more than just a simple utility.  It is possible that other system utilities use *mlocate* to find binaries needed to perform some action like compiling a package or determining a system installation state before installing something new.

I am not recommending removing it, but if you do, please share what breaks.

On my system, the database file is 6.4 MB.

> tgalati4@Mint17 ~ $ ls -la /var/lib/mlocate/mlocate.db
-rw-r----- 1 root mlocate 6436365 Aug 20 07:00 /var/lib/mlocate/mlocate.db

---

