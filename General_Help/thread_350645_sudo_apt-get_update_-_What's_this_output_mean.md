---
title: "sudo apt-get update - What's this output mean?"
date: 2007-01-31
forum: General Help
---

### Post by Roasted on 2007-01-31
Fetched 10.8kB in 1s (8215B/s)
Reading package lists... Done
W: GPG error: [http://ubuntu.moshen.de](http://ubuntu.moshen.de) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC0A1CC62F306651
W: You may want to run apt-get update to correct these problems
jason@jason:~$ 


I just ran it like 9 times. What can I do?

---

### Post by taurus on 2007-01-31
Edit /etc/fstab

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of that line, [http://ubuntu.moshen.de](http://ubuntu.moshen.de), to comment it out.  Save it and then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by chalex on 2007-01-31
by /etc/fstab he means /etc/apt/sources.list :)

Apt-get is complaining because you're trying to get a package list from a repository.  Each list is signed by a signature, but in the case of moshen.de, you do not have their signature installed on your system.  In the name of security, apt-get won't let you get the package list from there.  You have to import the repo's key/signature first.

---

### Post by jjalocha on 2008-01-20
I've had the same question. But where are these keys usually found? and how do you install them? Would be nice to know... :P

---

### Post by jjalocha on 2008-01-20
Nevermind... this does the trick:

```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -

```

(From [http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy).)

---

