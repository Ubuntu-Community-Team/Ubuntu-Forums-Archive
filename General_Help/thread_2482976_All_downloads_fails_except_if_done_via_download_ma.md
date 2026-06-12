---
title: "All downloads fails except if done via download managers."
date: 2023-01-16
forum: General Help
---

### Post by sahil-thinkpad on 2023-01-16
I'm using Ubuntu 20.04.5 LTS version, and had the same issue while using 22.04 LTS. Basically while updating packages via apt, it shows hash sum mismatch and if I try and download files on the internet via firefox or brave they too just fail.
However if I use download via a download manager like(Xtreme download manager) the download works fine.

So far I've tried

sudo rm -rf /var/lib/apt/lists/*(Clear the  lists file)

sudo rm -rf /var/lib/apt/lists/partial
sudo apt-get update -o Acquire::CompressionTypes::Order::=gz
Update with a different compression method, so the files load correctly and the checksum succeeds.

Still the same problem persists.

---

### Post by ActionParsnip on 2023-01-16
[https://stackoverflow.com/questions/64120030/hash-sum-mismatch-when-apt-get-update-ubuntu-20-04-vm-with-multipass](https://stackoverflow.com/questions/64120030/hash-sum-mismatch-when-apt-get-update-ubuntu-20-04-vm-with-multipass)

---

### Post by sahil-thinkpad on 2023-01-17
I had already tried that solution. Also I'm not using virtual machine on windows to run Ubuntu. Its on dual boot along with windows.

---

### Post by ajgreeny on 2023-01-17
I wonder if you have corrupt packages in your apt cache. The system will use those if they exist so perhaps it's worth removing the cache files before trying again with ```
sudo apt clean
```.

I don't use ***apt-get*** any more but now use ***apt*** which does not keep that package cache so everything will be downloaded fresh again.

---

### Post by sahil-thinkpad on 2023-01-18
Tried it, same issue still exists and also I ve twice reinstalled ubuntu by formatting the root directory, and every time the same issue comes back.

---

### Post by ajgreeny on 2023-01-18
Strange!
Let's see your sources.list file with the output of ***cat /etc/apt/sources.list*** to see if that offers any clues.

Please use Code-tags for terminal output.

---

### Post by sahil-thinkpad on 2023-01-18
```

#deb cdrom:[Ubuntu 20.04.5 LTS _Focal Fossa_ - Release amd64 (20220831)]/ focal main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://in.archive.ubuntu.com/ubuntu/ focal main restricted
# deb-src http://in.archive.ubuntu.com/ubuntu/ focal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ focal-updates main restricted
# deb-src http://in.archive.ubuntu.com/ubuntu/ focal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ focal universe
# deb-src http://in.archive.ubuntu.com/ubuntu/ focal universe
deb http://in.archive.ubuntu.com/ubuntu/ focal-updates universe
# deb-src http://in.archive.ubuntu.com/ubuntu/ focal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ focal multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ focal multiverse
deb http://in.archive.ubuntu.com/ubuntu/ focal-updates multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ focal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu focal partner
# deb-src http://archive.canonical.com/ubuntu focal partner

deb http://security.ubuntu.com/ubuntu focal-security main restricted
# deb-src http://security.ubuntu.com/ubuntu focal-security main restricted
deb http://security.ubuntu.com/ubuntu focal-security universe
# deb-src http://security.ubuntu.com/ubuntu focal-security universe
deb http://security.ubuntu.com/ubuntu focal-security multiverse
# deb-src http://security.ubuntu.com/ubuntu focal-security multiverse

# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.


```

---

### Post by sahil-thinkpad on 2023-01-18
The sources.list doesnt contain much, since I tried a fresh install again.

One thing I noted was, everything worked fine as long as I m using the wifi in my hostel, but if I go to class and use the wifi in the academic building then this issue starts again, it wasnt a one time thing, I observed it continuosly over a week. Could it be possible the college internet has something to do with it?

---

### Post by ajgreeny on 2023-01-18
Yes, it could be the wifi at your college; do you have any idea if it uses a proxy for connection which I believe can cause connection problems, though I have no personal experience of using any proxy?

Why not speak with the college wireless/computer gurus who may also be able to help you.

---

### Post by Topsiho on 2023-01-20
+1 for ajgreeny's suggestion to talk to those who are responsible for the college's wifi.
It's clear as mud that the files you download using that wifi are corrupt.
I had the same situation (long time ago) with my provider, though only with very large files, such as  the iso-files of Ubuntu. After they corrected that (after some persuasion) there were no (that sort of) problems anymore.

Topsiho

---

### Post by Topsiho on 2023-01-20
Another thought: download managers keep downloading packages until they are correct. Same as torrents. So that checks well with your observation that files can be downloaded using a download manager. But the wifi should be OK without that.

Topsiho

---

### Post by sahil-thinkpad on 2023-01-21
I have send a mail for this issue already but do you think if wifi is the issue then download issues should occur irrespective of os, since I face no issues while downloading files on windows. What do you think?

---

### Post by ajgreeny on 2023-01-21
Sorry, but I can't tell you anything about web connection details in Windows which I havent really used for 17 years.

---

### Post by Topsiho on 2023-01-21
This problem is not, in any way, connected to the OS that you use. It is the signal itself hat is delivered by the college that is the problem, so any OS would be affected by it.

**Rubbish in means rubbish out**

Even if you are the only student that is hit by a bad connection. It is your connection that is faulty, which does not mean that other students can not be hit too.

You should talk to the responsible person for the wifi of this college.

Good luck!

Topsiho

---

### Post by Topsiho on 2023-01-27
As I got no answer to my previous post, I only now react because I feel that I have to.
Rereading all previous posts I noticed that I made an error, assuming that in Windows the same wifi error occurred as in Ubuntu, which is **not** so.
**In Ubuntu the wifi reception is not correct, and in Windows it is, apparently.**
That means that the wifi signal itself is OK but that the error must be in Ubuntu.
The difference in both OS's is the **wifi driver**. So for the wifi-driver in Ubuntu a bug report is needed, and/or you need to use a wiifi-adapter on a USB-stick.
Is all the other related hardware the same: cables, modems, and so?

Topsiho

---

