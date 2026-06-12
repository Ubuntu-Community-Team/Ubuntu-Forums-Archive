---
title: "To upgrade from ubuntu 22.04 to 24.04.1 LTS issue"
date: 2024-11-21
forum: General Help
---

### Post by Ownager on 2024-11-21
Hello,

I am glad to be back here once again. I notice there is one issue. I am trying to upgrade from 22.04 to 24.04.1 LTS

I am going to put error message here. This issue may be common. 

> The following packages have been kept back:
  build-essential cpp g++ gcc gcc-multilib

I need a help with solving this issue. Thank you

---

### Post by Bashing-om on 2024-11-21
Ownager - Not to worry

Normal condition.
Please see:
[https://help.ubuntu.com/community/PhasedUpdates](https://help.ubuntu.com/community/PhasedUpdates)
[https://wiki.ubuntu.com/StableReleaseUpdates#Phasing](https://wiki.ubuntu.com/StableReleaseUpdates#Phasing)

when it is your turn
[INDENT]you'll get yours
[/INDENT]

---

### Post by Ownager on 2024-11-22
Hi, I am trying first link. It didn't solve at all.

---

### Post by Bashing-om on 2024-11-22
Ownager -
The links were not directed to solve, rather to explain.

Let's try a different approach to "see".
In terminal execute
```

apt policy gcc

```
in the output you can note the percentage of release.

Packages may be held such that in the event of reported issues the release is halted.

-continue on our merry way-

---

### Post by Ownager on 2024-11-22
I received the message after I followed your command.

gcc:
  Installed: 4:9.3.0-1ubuntu2
  Candidate: 4:11.2.0-1ubuntu1
  Version table:
     4:11.2.0-1ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 Packages
 *** 4:9.3.0-1ubuntu2 100
        100 /var/lib/dpkg/status

---

### Post by Bashing-om on 2024-11-22
Ownager - Hummmmm ...

That to me indicates that phasing for gcc is complete.
show us now:
```

sudo apt update
sudo apt upgrade

```

-see what tale gets told-

---

### Post by Ownager on 2024-11-22
update always works fine. upgrade should make a change at all. 

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Ownager on 2024-11-22
I finally solve upgrading to 24.04.1. I forced removing broken packages. You could do this. Broken packages are build-essential cpp g++ gcc gcc-multilib 

> sudo dpkg --purge --force-all <broken packages>

sudo dpkg --purge --force-all gcc-multilib

After you force removing broken packages, you can use software updater and click on upgrade. Problem solved

---

### Post by Bashing-om on 2024-11-22
Ownager
Good deal - ya done good.

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean, and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

-happy trails to you-

---

