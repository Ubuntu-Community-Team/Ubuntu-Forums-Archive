---
title: "i38 instead of i386? failure in synaptic update ubuntu 18.04LTS"
date: 2018-10-22
forum: General Help
---

### Post by Robbyx on 2018-10-22
I was having trouble with a stript that did not install some printer drivers because it was pointing to i38 instead of i386. To try to find the cause I unticked all the main repositories in synaptic, exited, and then did a sudo apt-get update. I see that I get a lot of messages like the following:

> Reading package lists... Done 
N: Skipping acquire of configured file 'main/binary-i38/Packages' as repository 'http://dl.winehq.org/wine-builds/ubuntu artful InRelease' doesn't support architecture 'i38'
N: Skipping acquire of configured file 'main/binary-i38/Packages' as repository 'http://ppa.launchpad.net/jaap.karssenberg/zim/ubuntu bionic InRelease' doesn't support architecture 'i38'



I need help getting the architecture reference corrected.

My system is the AMD-64.

---

### Post by dino99 on 2018-10-22
wine-builds artful  : update the version, artful is now dead since a while.

Looks like you have mixed 32 & 64 bits there.

---

### Post by Robbyx on 2018-10-22
How do I correct the versions? I have many more similar problems. Note that each entry is showing the binary-i38 instead of i386. How do I correct the truncated binary reference?

Is it possible that the ability to run i386 programs has been applied within synaptic? Could you please suggest what i should remove?

```
N: Skipping acquire of configured file 'main/binary-i38/Packages' as repository 'http://dl.winehq.org/wine-builds/ubuntu artful InRelease' doesn't support architecture 'i38'
N: Skipping acquire of configured file 'main/binary-i38/Packages' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't support architecture 'i38'
N: Skipping acquire of configured file 'universe/binary-i38/Packages' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't support architecture 'i38'
N: Skipping acquire of configured file 'restricted/binary-i38/Packages' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't support architecture 'i38'
N: Skipping acquire of configured file 'multiverse/binary-i38/Packages' as repository 'http://archive.ubuntu.com/ubuntu bionic InRelease' doesn't support architecture 'i38'
N: Skipping acquire of configured file 'main/binary-i38/Packages' as repository 'http://ppa.launchpad.net/jaap.karssenberg/zim/ubuntu bionic InRelease' doesn't support architecture 'i38'
N: Skipping acquire of configured file 'main/binary-i38/Packages' as repository 'http://linux.teamviewer.com/deb stable InRelease' doesn't support architecture 'i38'
N: Skipping acquire of configured file 'main/binary-i38/Packages' as repository 'http://deb.xanmod.org releases InRelease' doesn't support architecture 'i38'
N: Skipping acquire of configured file 'partner/binary-i38/Packages' as repository 'http://archive.canonical.com/ubuntu bionic InRelease' doesn't support architecture 'i38'
N: Skipping acquire of configured file 'main/binary-i38/Packages' as repository 'http://linux.teamviewer.com/deb preview InRelease' doesn't support architecture 'i38'
N: Skipping acquire of configured file 'main/binary-i38/Packages' as repository 'http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu bionic InRelease' doesn't support architecture 'i38'
N: Skipping acquire of configured file 'non-free/binary-i38/Packages' as repository 'https://deb.opera.com/opera-beta stable InRelease' doesn't support architecture 'i38'
N: Skipping acquire of configured file 'non-free/binary-i38/Packages' as repository 'https://deb.opera.com/opera-stable stable InRelease' doesn't support architecture 'i38'
N: Skipping acquire of configured file 'main/binary-i38/Packages' as repository 'http://ppa.launchpad.net/teejee2008/ppa/ubuntu bionic InRelease' doesn't support architecture 'i38'
N: Skipping acquire of configured file 'restricted/binary-i38/Packages' as repository 'http://archive.ubuntu.com/ubuntu bionic-updates InRelease' doesn't support architecture 'i38'
N: Skipping acquire of configured file 'multiverse/binary-i38/Packages' as repository 'http://archive.ubuntu.com/ubuntu bionic-updates InRelease' doesn't support architecture 'i38'
N: Skipping acquire of configured file 'universe/binary-i38/Packages' as repository 'http://archive.ubuntu.com/ubuntu bionic-updates InRelease' doesn't support architecture 'i38'
N: Skipping acquire of configured file 'main/binary-i38/Packages' as repository 'http://archive.ubuntu.com/ubuntu bionic-updates InRelease' doesn't support architecture 'i38'
N: Skipping acquire of configured file 'restricted/binary-i38/Packages' as repository 'http://security.ubuntu.com/ubuntu bionic-security InRelease' doesn't support architecture 'i38'
N: Skipping acquire of configured file 'multiverse/binary-i38/Packages' as repository 'http://security.ubuntu.com/ubuntu bionic-security InRelease' doesn't support architecture 'i38'
N: Skipping acquire of configured file 'universe/binary-i38/Packages' as repository 'http://security.ubuntu.com/ubuntu bionic-security InRelease' doesn't support architecture 'i38'
N: Skipping acquire of configured file 'main/binary-i38/Packages' as repository 'http://security.ubuntu.com/ubuntu bionic-security InRelease' doesn't support architecture 'i38'
N: Skipping acquire of configured file 'restricted/binary-i38/Packages' as repository 'http://archive.ubuntu.com/ubuntu bionic-backports InRelease' doesn't support architecture 'i38'
N: Skipping acquire of configured file 'multiverse/binary-i38/Packages' as repository 'http://archive.ubuntu.com/ubuntu bionic-backports InRelease' doesn't support architecture 'i38'
N: Skipping acquire of configured file 'universe/binary-i38/Packages' as repository 'http://archive.ubuntu.com/ubuntu bionic-backports InRelease' doesn't support architecture 'i38'
N: Skipping acquire of configured file 'main/binary-i38/Packages' as repository 'http://archive.ubuntu.com/ubuntu bionic-backports InRelease' doesn't support architecture 'i38'

```

---

### Post by Robbyx on 2018-10-22
I am wondering if a fresh install would correct this problem of the wrong repository reference. Root and home are separate directories and I do not know where the refence is stored. If it is in the home directory my limited reinstall  would not correct it.

---

### Post by Holger_Gehrke on 2018-10-22
I'd try to remove the misspelled architecture with 'sudo dpkg --remove-architecture i38' then add the correct spelling with 'sudo dpkg --add-architecture i386'. If that has the desired effect, I'd edit /etc/apt/sources.list and the source list fragments in /etc/apt/sources.list.d/* to update all the references to 'artful' to 'bionic'.

Holger

---

### Post by dino99 on 2018-10-22
From synaptic, you can easily watch the active ppas: check if they point to bionic as your system. Possibly downgrade to genuine version to see if that help resolving the errors.
 Then Use gtkorphan & bleachbit (as root, select carefully settings)
Why have you a separate /root set ?

---

### Post by Robbyx on 2018-10-22
> **Holger_Gehrke said:**
> I'd try to remove the misspelled architecture with 'sudo dpkg --remove-architecture i38' then add the correct spelling with 'sudo dpkg --add-architecture i386'. If that has the desired effect, I'd edit /etc/apt/sources.list and the source list fragments in /etc/apt/sources.list.d/* to update all the references to 'artful' to 'bionic'.

Holger

Thank you for your comment I ran your remove and add-architecture suggestions and it cleared up the update problem. I saw nothing in the source lists to indicate there was an error there and so left it alone. It seems to be working properly now.

---

### Post by Robbyx on 2018-10-22
> **dino99 said:**
> From synaptic, you can easily watch the active ppas: check if they point to bionic as your system. Possibly downgrade to genuine version to see if that help resolving the errors.
 Then Use gtkorphan & bleachbit (as root, select carefully settings)
Why have you a separate /root set ?

Thank you for your help. As you can see I first followed Holger's advice above. Should I still follow your recommendation to use gtkorphan and bleachbit as the error messages have gone away without them?

What I really meant was that home is in a separate partition from the root.

---

### Post by dino99 on 2018-10-22
Cleaning the system should be done once a month at least during development or when using third party repo.

---

### Post by Robbyx on 2018-10-22
> **dino99 said:**
> Cleaning the system should be done once a month at least during development or when using third party repo.


Thank you.

---

