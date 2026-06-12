---
title: "Can't install apps"
date: 2008-01-01
forum: General Help
---

### Post by Red Badger on 2008-01-01
I tried to uninstall Firestarter, but Ubuntu froze during the uninstall. When I rebooted I can no longer install applications from Add/Remove or Synaptic. I tried installing using apt-get install, but I get an error message 'Segmentation fault (core dumped)'.
I had a look in the dpkg log and it says:

2008-01-01 13:06:18 startup packages remove
2008-01-01 13:06:18 status installed firestarter 1.0.3-6ubuntu1
2008-01-01 13:06:29 remove firestarter 1.0.3-6ubuntu1 1.0.3-6ubuntu1
2008-01-01 13:06:29 status half-configured firestarter 1.0.3-6ubuntu1
2008-01-01 13:06:36 status half-installed firestarter 1.0.3-6ubuntu1
2008-01-01 13:06:38 status config-files firestarter 1.0.3-6ubuntu1
2008-01-01 13:06:38 status config-files firestarter 1.0.3-6ubuntu1

Anything I can do?

---

### Post by taurus on 2008-01-01
What happens when you run these two command from a terminal?

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by xeth_delta on 2008-01-01
Then you could also give the following command  try:
```
sudo apt-get -f uninstall
```

---

### Post by Red Badger on 2008-01-01
Hi xeth_delta & taurus

I tried the commands both you guys recommended and they didn't work, but I've managed to fix the problem by adding a CD to the sources. After that I was able to run Add/Remove & Synaptic.

Thanks anyway.  :)

---

### Post by xeth_delta on 2008-01-01
> **Red Badger said:**
> Hi xeth_delta & taurus

I tried the commands both you guys recommended and they didn't work, but I've managed to fix the problem by adding a CD to the sources. After that I was able to run Add/Remove & Synaptic.

Thanks anyway.  :)

Are you sure you were connected to the network when you were trying to install and got all those problems?

---

### Post by Red Badger on 2008-01-01
Hi xeth_delta

Yes, I definitely had an network connection as I was searching the Ubuntu forums for a solution.
I have been plagued with Gutsy freezing on me, so perhaps it froze while I was uninstalling Firestarter.

As I said, it seems okay now.

Cheers

---

### Post by taurus on 2008-01-01
Maybe your network is working but you don't have any repos available in /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by ~LoKe on 2008-01-01
The CD wouldn't have fixed anything specific like that without you manually doing it...so I'm leaning towards a problem with your repositories as well.

---

### Post by Red Badger on 2008-01-01
I've got repos in /etc/apt/sources.list 
I've added a few repos to install software and then removed the repo.
Would that cause a problem?

---

### Post by ~LoKe on 2008-01-01
Depends if you added/removed them properly.  You might have made a typo.

---

