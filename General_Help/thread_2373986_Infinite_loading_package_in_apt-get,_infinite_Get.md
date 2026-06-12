---
title: "Infinite loading package in apt-get, infinite Get"
date: 2017-10-11
forum: General Help
---

### Post by slavamokerov on 2017-10-11
Ubuntu 16.04.3 xenial

**apt-get update** is not working. Apt-get endlessly tries to get a package:

```
ams@ubuntu-ams:~$ sudo apt-get update
Get:1 http://ru.archive.ubuntu.com/ubuntu xenial InRelease [247 kB]
Get:2 http://ru.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Get:3 http://ru.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]
Get:4 http://ru.archive.ubuntu.com/ubuntu xenial/main amd64 Packages [1,201 kB]
Get:5 http://ru.archive.ubuntu.com/ubuntu xenial/main i386 Packages [1,196 kB]
Get:5 http://ru.archive.ubuntu.com/ubuntu xenial/main i386 Packages [1,196 kB]
Get:5 http://ru.archive.ubuntu.com/ubuntu xenial/main i386 Packages [1,196 kB]
Get:5 http://ru.archive.ubuntu.com/ubuntu xenial/main i386 Packages [1,196 kB]
...

```

I changed the addresses of the mirrors in the file **/etc/apt/sources.list**.
I've tried these addresses: ru.archive.ubuntu.com, archive.ubuntu.com, de.archive.ubuntu.com. But it did not help.

The problem is not this: [https://askubuntu.com/questions/774918/apt-get-is-stuck-at-fetched-xxkb-in-xxsec](https://askubuntu.com/questions/774918/apt-get-is-stuck-at-fetched-xxkb-in-xxsec)

I also tried and that did not help:
```

#houseclean
sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get clean

#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
sudo apt-get dist-upgrade

# fix Broken packages -f 
sudo apt-get -f install
sudo dpkg --configure -a

# Remove lock
# If you are absolutely sure you do not have another upgrade process running.
# Locked dpkg - only if sure you are not running another update.
sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a

# problems with hash sum mismatch
sudo rm /var/lib/apt/lists/*
sudo apt-get update

# Package Manager & Update Manager problems
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get update

```

Nothing helped. After sudo apt-get update is still looping:
```
... archive.ubuntu.com/ubuntu xenial/main i386 Packages
```

[B]What's going on?

[/B]Here it worked by itself: [https://askubuntu.com/a/677313/746294](https://askubuntu.com/a/677313/746294). What I need to do to fix it and not to wait until the cache is somewhere updated?

---

### Post by ian-weisser on 2017-10-11
None of your 'tried' solutions would help. Those would help different problems that occur *after *your package database is updated.

Avoid shotgunning random solutions that you find on the dirty, dirty internet. One of those might break your system quite horribly.
Do not attempt to install software while your apt package database is out-of-date. If you think you have problems now....

How long has this issue been happening? More than 48 hours?
Are you using some kind of proxy, like a caching proxy? Or a school network proxy?
If so, is it properly configured in apt?

---

### Post by slavamokerov on 2017-10-11
> **ian-weisser said:**
> How long has this issue been happening? More than 48 hours?
Less than 48 hours, about 20 hours.

> **ian-weisser said:**
> Are you using some kind of proxy, like a caching proxy?
Yes, there seems to be a proxy. I don't know how to check it. But if I go to the gateway:8080 via browser, I was redirected to the gateway:8081. And I see the cover with the message: 503 - Service Unavailable, try later.
Internet is available without any proxy settings on the client.

> **ian-weisser said:**
> If so, is it properly configured in apt?
How to correctly configure it? I found some instructions, so I'm not sure whether to use it.
What to do if there is no access as the proxy server?
How to configure to not use proxy?

---

### Post by ian-weisser on 2017-10-11
If it's not your proxy, then you must ask whoever owns the network. They put the proxy there for a reason, and it's a violation of our Code of Conduct to help users violate their Terms of Service.

If it's a normal caching proxy (like you would find on many school or corporate networks), then the problem will solve itself in a day or so when the cache refreshes.

---

### Post by slavamokerov on 2017-10-11
> **ian-weisser said:**
> 
If it's a normal caching proxy (like you would find on many school or corporate networks), then the problem will solve itself in a day or so when the cache refreshes.

Is it possible not to wait a whole day? How to avoid such problems in the future?

---

### Post by ian-weisser on 2017-10-11
It's possible to not wait. You simply need to tell (somebody else's) caching proxy to reload...if you have permission from the network owner to do so.

---

### Post by slavamokerov on 2017-10-11
The problem in proxy server.
Quick solution: in **[font=courier]/etc/apt/sources.list[/font]** replace mirrors **[font=courier]http[/font]** to **[font=courier]https[/font]**. For example,  **[font=courier]http://ru.archive.ubuntu.com[/font]** replace with **[font=courier]https://mirror.yandex.ru[/font]** works for me.

---

