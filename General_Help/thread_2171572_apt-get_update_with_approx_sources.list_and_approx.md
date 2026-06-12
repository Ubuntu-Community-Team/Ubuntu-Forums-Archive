---
title: "apt-get update with approx: sources.list and approx.conf are messed up"
date: 2013-08-31
forum: General Help
---

### Post by ecowan on 2013-08-31
For months I have not been able to apply updates. I get no end of '404 Not Found', 'Ign' and 'Failed to fetch' errors whenever I try 'apt-get update'.
I have tried deleting everything in /var/lib/apt/lists, /var/lib/apt/lists/partial, and approx-cache. I've run 'apt-get clean' and 'approx-gc -v'.

Here are my latest efforts:

/etc/apt/sources.list:
```
deb http://localhost:9999/base/ precise main restricted universe multiverse
deb http://localhost:9999/base/ precise-security main restricted universe multiverse
deb http://localhost:9999/base/ precise-updates main restricted universe multiverse
deb http://localhost:9999/partner precise partner
deb http://localhost:9999/extras precise main
```

and my approx.conf:
```
base		http://ca.archive.ubuntu.com/ubuntu/
partner		http://archive.canonical.com/ubuntu
extras		http://extras.ubuntu.com/ubuntu

```

I'm reminded of the line in that old Rolf Harris song, 'My boomerang won't come back'. "I've practiced 'til I am black in the face ...."

It used to work just great.

---

### Post by rai_shu2 on 2013-08-31
Could be something about the way Ubuntu handles dnsmasq with localhost lately (see [DNS in 12.04]("http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/")).

I've noticed people discussing it tend to suggest apt-cacher-ng or just squid. Personally, I just copy files into an archive folder and then copy those into the /var/cache/apt/archives just before I update other machines (but then I'm only dealing with a couple of machines here).

---

### Post by grahammechanical on 2013-08-31
Your sources list directs apt-get to localhost and not to a Ubuntu repository/archive. Is that what you intend?

My sources list has stuff like this

> deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) raring main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) raring main restricted

I am using 13.04 and my updates come from a Ubuntu UK archive. This command will remove/delete all the scripts in /var/lib/apt/lists/

```
sudo rm /var/lib/apt/list/* -rf
```

And this command will replaced them with a fresh set.

```
sudo apt-get update
```

I have used it when I have been unable to update because of missing headers in the package lists. By the way IGN and Not Found messages may be due to PPAs that are not longer being maintained. A Personal Package Archive is useful for installing some software but if the archive is no longer maintained and apt-get cannot find anything at the address then apt-get will give those kind of errors.

The actual wording of those errors is a clue to what was causing this problem.

Regards.

---

### Post by bapoumba on 2013-08-31
Please see if these solutions work for you : [http://ubuntuforums.org/showthread.php?t=2125671](http://ubuntuforums.org/showthread.php?t=2125671)

---

### Post by ecowan on 2013-08-31
That did it.

---

### Post by rai_shu2 on 2013-08-31
So, permissions got messed up in your approx cache?

---

### Post by bapoumba on 2013-09-01
Glad to see you got it to work :)

---

