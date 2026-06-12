---
title: "fstab parameter exec changed to noexec after boot"
date: 2013-02-23
forum: General Help
---

### Post by sapeurcamembert on 2013-02-23
Fresh install ubuntu 12.10 (up from 10.04).

I am not able to execute any bash script or user command from my own user directory /home/am/bin for example). User name is am.

I am able to execute the same command or program if moved to /usr/local/bin

Shell script example...for test..hard to beat !!!

#!/bin/bash
echo Hello Ubuntu

Script is executable    -rwxr--r-- 1 am am 30 Feb 23 17:14 myhello

/home/am/bin is in the path  

using command echo $PATH

/home/am/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games

Home directory in a dedicated partition mounted as (entry from fstab)

# /dev/sdc3     Home

UUID=6eaa21ae-a21a-4fbe-8ef1-6f713123ea30               /home   ext4    auto,exec,user,rw

BUT I discovered partition /dev/sdc3 (/home) is mounted (after boot) as

/dev/sdc3 on /home type ext4 (rw,noexec,nosuid,nodev)

**noexec explained that scripts can not be executed....**

**[COLOR=Blue]How a partition defined as auto,exec,user,rw can be mounted as[/COLOR]**

rw,noexec,nosuid,nodev  ?

**[COLOR=Blue] [/COLOR][COLOR=Blue]after boot ?[/COLOR]**

---

### Post by Morbius1 on 2013-02-23
Well, let's see:

"exec" = allows execution.
"user" = forces a "noexec"

So you turned it on then turned it off. Unless you have a compelling reason to have "user" in the list of options ( and I have as yet never heard one ) just remove it.

Or for clarity sake just replace the line you have with this one:
```
 UUID=6eaa21ae-a21a-4fbe-8ef1-6f713123ea30 /home   ext4    defaults 0 2
```

---

### Post by sapeurcamembert on 2013-02-23
Many Thanks Morbius1. 

I dit it in the meantime.

---

### Post by dcstar on 2013-02-24
> **sapeurcamembert said:**
> Many Thanks Morbius1. 

I dit it in the meantime.

If it is Solved, then MARK the thread.

---

