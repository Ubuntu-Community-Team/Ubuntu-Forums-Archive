---
title: "Fix root bashrc"
date: 2014-03-23
forum: General Help
---

### Post by shibby4555 on 2014-03-23
Alright, I messed up big time here, I edited my bashrc file while I was in root. 

Nonroot user is fine, but I can't do anything whatsoever as root anymore. The paths are all messed up. So I can't simply sudo vi .bashrc

What do I do?

---

### Post by superdaveozzborn on 2014-03-23
try as superuser? just a first thought!

$ sudo su

---

### Post by shibby4555 on 2014-03-23
```

sudo su
vi /root/.bashrc

```
I get
```

Command 'vi' is available in '/usr/bin/vi'
The command could not be located because '/usr/bin' is not included in the PATH environment variable.
vi: command not found

```

I may have royally screwed myself.

---

### Post by superdaveozzborn on 2014-03-23
hmmm ... sorry was just an idea.

only other way i can think of is to use live cd and chroot into your system to modify that file.

---

### Post by shibby4555 on 2014-03-23
Solved. Found a work around. In case anyone else has this problem:
I copied /etc/skel/.bashrc

Appended:
```

export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

```


Then,
```

sudo source /path/to/new/.bashrc

```

Reloads .bashrc

---

### Post by Impavidus on 2014-03-23
> **shibby4555 said:**
> ```

sudo su
vi /root/.bashrc

```
I get
```

Command 'vi' is available in '/usr/bin/vi'
The command could not be located because '/usr/bin' is not included in the PATH environment variable.
vi: command not found

```

I may have royally screwed myself.
In that case, try **/usr/bin/vi /root/.bashrc**. Just using the explicit path.

---

### Post by shibby4555 on 2014-03-23
> **Impavidus said:**
> In that case, try **/usr/bin/vi /root/.bashrc**. Just using the explicit path.

Of course, that dawned on me immediately after I spent 20 minutes trying to fix it.
But thanks!

---

### Post by superdaveozzborn on 2014-03-23
;) at least ya got it working..

---

