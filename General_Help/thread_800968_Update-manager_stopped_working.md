---
title: "Update-manager stopped working"
date: 2008-05-20
forum: General Help
---

### Post by Faceache on 2008-05-20
Hi,

There were a bunch of updates which I applied yesterday (through update manager) and since then I get the following error when launching update-manager from the terminal:

current dist not found in meta-release file

Does anyone have a solution?

TIA,

Faceache

---

### Post by ibuclaw on 2008-05-20
What does the current sources.list file look like?
Open up a terminal and paste the output of
```
cat /etc/apt/sources.list | grep -v "##" | awk '{if ($1!="#") print}' | sort | uniq 
```

Also, what repository are you tied to?

Regards
Iain

---

### Post by noynac on 2008-05-20
I've gotten the same message since early beta, and other users have reported the same thing. I have always assumed that it meant that no updates are available.

I did find the following bug report:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/174266](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/174266)

---

### Post by noynac on 2008-05-20
---

---

### Post by Faceache on 2008-05-20
Hi Iain,

```
deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security universe

```

When I launch update-manager from the GUI it hangs and I have to kill the process.

---

### Post by Kevbert on 2008-05-20
Try the following code in terminal:
```
sudo apt-get update
```
This should be a temporary fix.  It's interesting that you're not the first person to have this problem.

---

### Post by ibuclaw on 2008-05-20
```
gksu wget http://changelogs.ubuntu.com/meta-release-development -O /var/lib/update-manager/meta-release
```

Then try ```
gksu update-manager --dist-upgrade
```

[QUOTE=Kevbert]This should be a temporary fix. It's interesting that you're not the first person to have this problem. [/QUOTE]
Personally, I always use my trusty "aptitude" program to handle all my package installment/removals as it has a more "**intelligent**" way of dealing with dependancies.

Regards
Iain

---

### Post by Faceache on 2008-05-20
Thanks Iain, that sorted it.

---

