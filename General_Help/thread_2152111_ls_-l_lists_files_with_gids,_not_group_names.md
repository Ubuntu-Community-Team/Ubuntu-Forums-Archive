---
title: "ls -l lists files with gids, not group names"
date: 2013-06-06
forum: General Help
---

### Post by rivercobble on 2013-06-06
Hi,

I accidentally wiped out some of my group membership settings, and restored them by rebooting in recovery mode, and doing
  ```
  cp -a /etc/group- /etc/group
```
Since I did this, whenever I run 
```
 ls -l
```
the groups are listed as gids, not names.

Can someone explain why this happens and how I can restore the names to the output?

Thanks.

---

### Post by capscrew on 2013-06-06
> **rivercobble said:**
> Hi,

I accidentally wiped out some of my group membership settings, and restored them by rebooting in recovery mode, and doing
  ```
  cp -a /etc/group- /etc/group
```
Since I did this, whenever I run 
```
 ls -l
```
the groups are listed as gids, not names.

Can someone explain why this happens and how I can restore the names to the output?

Thanks.

The OS lists the group ownership by GID if it can't find a mapping between the group name and the GID.  Is this problem only in your home directory?

---

### Post by rivercobble on 2013-06-06
It behaves the same if I ls -l another directory, and, I just noticed even if I'm logged in as another user.

---

### Post by capscrew on 2013-06-06
> **rivercobble said:**
> It behaves the same if I ls -l another directory, and, I just noticed even if I'm logged in as another user.

Post the output of ```
getent group
```

What user are you logged in as?

---

### Post by rivercobble on 2013-06-06
```
sudo getent group
``` as user rc gives me
```

root:x:0:
daemon:x:1:
bin:x:2:
lp:x:7:
    etc

```

EDIT: first two lines somehow got merged when I posted; I've unmerged them

---

### Post by steeldriver on 2013-06-06
Like capscrew said, it's a mismatch between the gid that origiannly belonged to the group, and the new one - for example if here my user private group 'steeldriver' is associated with gid 1002, so when the system sees files with gid = 1002 it interprets those as belonging to group 'steeldriver'

```

$ grep ^steeldriver /etc/group
steeldriver:x:1002:
$ 
$ ls -ldn /home/steeldriver
drwxr-xr-x 3 1002 1002 4096 Jun  4 11:49 /home/steeldriver
$ 
$ ls -ld /home/steeldriver/
drwxr-xr-x 3 steeldriver steeldriver 4096 Jun  4 11:49 /home/steeldriver/

```

But if I then change 'steeldriver's gid to something else in my /etc/groups, number 1002 no longer corresponds to a named group - so it just prints the number

```

$ sudo groupmod -g 1005 steeldriver
$ 
$ grep ^steeldriver /etc/group
steeldriver:x:[COLOR=#ff0000]**1005**[/COLOR]:
$ 
$ ls -ld /home/steeldriver/
drwxr-xr-x 3 steeldriver **[COLOR=#ff0000]1002[/COLOR]** 4096 Jun  4 11:49 /home/steeldriver/

```

You should be able to fix it either by figuring out the correct gids for each named group in your /etc/passwd file, and using groupmod (or an equivalent tool) to change them, or by using chgrp/chown to set the group ownerships of the files keeping the groups' new gids - personally I'd do the former, since I like to keep my uids and user private gids in sync

---

### Post by capscrew on 2013-06-06
This looks fine at this time.  Lets be more specific.

Post the output of ```
getent group|rchen
```...this will list all the groups your in.

In your home directory,  post the output of ```
ls -l
```...so we can see what you are talking about.

---

### Post by rivercobble on 2013-06-06
```
sudo getent group | grep rc
``` gives
```


adm:x:4:rclp:x:7:rcdialout:x:20:rccdrom:x:24:rcdip:x:30:rcplugdev:x:46:rclpadmin:x:110:rcadmin:x:119:rcrc:x:1000:sambashare:x:124:rcwireshark:x:1003:rc
```

```

ls -l /home/rc

``` gives

```

...
drwxr-xr-x  5 rc 1000    4096 2012-09-12 20:59 test
drwxr-xr-x  8 rc 1000    4096 2013-04-15 19:22 tmp
...

```

---

### Post by capscrew on 2013-06-06
> **rivercobble said:**
> ```
sudo getent group | grep rchen
``` gives
```

adm:x:4:rchen
lp:x:7:rchen
dialout:x:20:rchen
cdrom:x:24:rchen
dip:x:30:rchen
plugdev:x:46:rchen
lpadmin:x:110:rchen
admin:x:119:rchen
rchen:x:1000:
sambashare:x:124:rchen
wireshark:x:1003:rchen

```

```

ls -l /home/rchen

``` gives

```

...
drwxr-xr-x  5 rchen 1000    4096 2012-09-12 20:59 test
drwxr-xr-x  8 rchen 1000    4096 2013-04-15 19:22 tmp
...

```

Well that's not what we expected to see.

Post the output of ```
getent passwd|grep rchen
``` ... the username database.

---

### Post by rivercobble on 2013-06-06
I've compared the /etc/group and /etc/passwd, and all the group ids match up with the exception of these:
```

/etc/passwd        /etc/passwd     /etc/group
user               group           group
---------------------------------------------------
sync               65534     
nobody             65534     
hplip              7               lp
sshd               65534     
fetchmail          65534     
jetty              65534     
speech-dispatcher  29              audio
kernoops           65534     
usbmux             46              plugdev
festival           29              audio

```

Does any of this look problematic? What is gid=65534?

---

### Post by capscrew on 2013-06-06
The number 65534 is the last number available for either users or groups.  It is traditionally the number assigned to the user:nobody and the group:nogroup.

So you have added users that are sharing the same UID and GID.  You grid is confusing to me.  I'd prefer the data as:```
user:group UID:GID
```

what happens if you do this (in your home directory)```

sudo chgrp rchen *

```

---

### Post by rivercobble on 2013-06-06
chgrp'ing my home directory works fine, and everything looks the same as before; e.g.,
```

drwxr-xr-x  5 rc 1000    4096 2012-09-12 20:59 test
drwxr-xr-x  8 rc 1000    4096 2013-04-15 19:22 tmp

```

---

### Post by rivercobble on 2013-06-07
So I think something else is going on.

 I reverted /etc/group and /etc/passwd to earlier versions that were clean and working, and got the same behavior with **ls -l**.

Also, I rebooted into recovery mode, dropping into the root shell. Here **ls -l** correctly listed the groups by name. The files are the same as in the normal mode.

Anyone have any other ideas?

---

### Post by rivercobble on 2013-06-07
.

---

### Post by steeldriver on 2013-06-07
Could it be just that the permissions on your /etc/group are wrong? e.g.

```

$ ls -ld /home/steeldriver
drwxr-xr-x 3 steeldriver steeldriver 4096 Jun  4 11:49 /home/steeldriver
$ 
$ sudo chmod **o-r** /etc/group
$ 
$ ls -ld /home/steeldriver
drwxr-xr-x 3 steeldriver **1002** 4096 Jun  4 11:49 /home/steeldriver

```

It should be owner by root:root and mode 644

```

$ ls -l /etc/group
-rw-r--r-- 1 root root 827 Jun  7 01:39 /etc/group

```

if it's not, chmod/chown it

```

$ sudo chmod 644 /etc/group
$ 
$ sudo chown root:root /etc/group

```

---

### Post by rivercobble on 2013-06-07
Fixing the permissions did it. The backups have 700 which got transferred over when I did the cp -a.

Thanks much!

---

