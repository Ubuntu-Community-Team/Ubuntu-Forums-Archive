---
title: "sudo: unable to resolve host (none)"
date: 2014-04-17
forum: General Help
---

### Post by ITDEPT on 2014-04-17
I have setup ubuntu 12.04 LTS with Zimbra 8.0.6 

It was fine until a few days ago, everything overall still works, it used to show 

```
user@mail:/# 
```

but now at the terminal it shows 

```
user@(none):/#
```

And if i try run this command

```
# sudo chmod +x filename
```

It still works, but i also get this error

```
sudo: unable to resolve host (none) 
```

I have rechecked, changed and changed back again my etc/hosts and etc/hostname file.

etc/hosts
```
127.0.0.1       localhost
10.0.1.5        mail.mydomain.com    mail


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback localhost
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

/etc/hostname

```
10.0.1.5   mail.mydomain.com   mail



```

i really can't find anything on this, all searches seem to tell me to fix my hosts files, but they are OK i think (i didn't change them.)

The only thing i can think i did was when i was doing a backup i ran this command 

```
# rsync -avHK --delete --exclude 'data/ldap/mdb/db/' /opt/zimbra/ /mnt;
```

and it seemed to start deleting things from my /opt/zimbra/zmstat folder (it was supposed to delete files from the /mnt). I canceled it when i saw what it was doing.

Any in-site into this?

---

### Post by steeldriver on 2014-04-17
Shouldn't the /etc/hostname file just contain the unqualified name of the host (mail)? I don't think that other stuff belongs there

---

### Post by Bashing-om on 2014-04-17
ITDEPT; Hello,

My /etc/hosts and /etc/hostname files for reference:
```

sysop@1310mini:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       1310mini

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
sysop@1310mini:~$ 

sysop@1310mini:~$ cat /etc/hostname
1310mini
sysop@1310mini:~$ 

```

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by Habitual on 2014-04-18
Shouldn't that be
```
127.0.0.1 localhost.localdomain localhost
```
?

---

### Post by ITDEPT on 2014-04-23
thanks guys, i think i got it figured, i needed to put in > mail.mydomain.com and nothing else
I rememebr now i had some issues with email and had changed that and thought it fixed it.

---

