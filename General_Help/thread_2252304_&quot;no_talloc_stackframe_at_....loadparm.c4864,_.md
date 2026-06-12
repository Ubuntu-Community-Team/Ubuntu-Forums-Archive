---
title: "&quot;no talloc stackframe at ....loadparm.c:4864, leaking memory&quot;"
date: 2014-11-10
forum: General Help
---

### Post by CyborgAlpha on 2014-11-10
**not resolved**
> no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory

> That said, my post was asking if this was a fresh install or an upgrade from saucy?
I had this problem from an upgrade, and seemed to have marked that bug as affecting me.
(I don't remember doing so, and thought it was for sudo)
Don't know if it fixed, since that install is gone now.

Haven't seen it with a fresh install, though.
[ [http://ubuntuforums.org/showthread.php?t=2214042&p=12972563#post12972563](http://ubuntuforums.org/showthread.php?t=2214042&p=12972563#post12972563) ]

Brand new install of Kubuntu 14.04 64bit,
```
sudo xxx
``` 
and after the password
```
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
```

Who else is experiencing this?

---

### Post by cariboo on 2014-11-11
To ge rid of the error, run:

```
pam-auth-update
```

then remove:

```
SMB password synchronization
```

You may have to remember your samba password, if it doesn't match your user password.

The problem did get resolved in 14.10, but if you are running the LTS version that isn't much help.

---

### Post by CyborgAlpha on 2014-11-12
> **cariboo907 said:**
> To ge rid of the error, run:

```
pam-auth-update
```

then remove:

```
SMB password synchronization
```

You may have to remember your samba password, if it doesn't match your user password.

The problem did get resolved in 14.10, but if you are running the LTS version that isn't much help.

I'm testing it on one system to see if it causes any log-in issues. Basically, the solution* is turn off password syncing, which was the prime reason for installing it.

Do you know why a memory leak wasn't a priority to actually fix?

---

### Post by Doug S on 2014-11-12
> **CyborgAlpha said:**
> Do you know why a memory leak wasn't a priority to actually fix?It is an upstream issue, and these things take time. I don't know that it actually is a memory leak. Myself, I  have just been ignoring the error ever since [URL="https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1257186"]I first reported it. 



[/URL]

---

### Post by CyborgAlpha on 2014-11-13
I have it in my bug track list. Samba shows fixed, the issue is further downline;

[quote="[monochromec (monochromec)]("https://launchpad.net/%7Emonochromec")             wrote             on 2014-11-10 in Bug #1257186"]

This still might point back to the talloc issue I pointed out earlier in this thread.

Checking libtalloc2 on both trusty and utopic (14.04.1 and 14.10) reveals the following:

trusty: 49704 Oct 21 2013 /usr/lib/x86_64-linux-gnu/libtalloc.so.2.1.0
utopic: 59560 Jul 6 07:12 /usr/lib/x86_64-linux-gnu/libtalloc.so.2.1.1

So different versions, patchlevels and sizes...

Apparently the talloc2 patch present in 14.10 didn't make into 14.4.1; if somebody upstream is reading this it would be great to have a timeline for inclusion into the 14.4 base.
[/quote]

---

