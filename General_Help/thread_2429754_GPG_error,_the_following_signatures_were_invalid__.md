---
title: "GPG error, the following signatures were invalid / The repository is not sig"
date: 2019-10-22
forum: General Help
---

### Post by adavel on 2019-10-22
Hi, who is reading this. How are you?
  I turn to this forum as my last resort, because I was convinced that I would solve my problem by searching and reading a solution on the internet but nothing worked for me.
  I have this error when trying to update Kubuntu:


```
W: GPG error: [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) maverick Release: The following signatures were invalid: 630239CC130E1A7FD81A27B140976EAF437D05B5
E: The repository «[http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) maverick Release» is not signed.
N: You cannot update a repository like this securely and therefore it is disabled by default.
```


I already tried to update the public key of the repository, among other things.
  I hope someone can help me, thanks in advance.

---

### Post by guiverc on 2019-10-22
Ubuntu 10.10 (Maverick Meerket from 2010-October) was a standard release of Ubuntu with 15 months of supported life. It should not be used as it's years past EOL.  I would suggest re-installing a supported release of Ubuntu rather than try and fix your issue.

FYI: GPG keys used were changed well after 10.10 had reached EOL due to weaknesses detected in the then GPG strength then in use by Ubuntu (micrsoft and other companies/OSes).  OSes then in support/use were updated with stronger keys, but I can't recall what was done with EOL releases and if this is your issue.

---

### Post by adavel on 2019-10-23
I see.... But there is not another way to fix the problem without re-installing Ubuntu? Also, my version is the last one so far. 19.10

---

### Post by PaulW2U on 2019-10-23
adavel, I'm confused about the version and flavour of Ubuntu that you are having a problem with.

You mention Kubuntu, Ubuntu, 19.10 but are trying to download from archived 'maverick' repositories. Please confirm which version of Ubuntu you're using. If you're using Ubuntu 19.10 Eoan Ermine, which was released last week, why are you trying to download from 'old-releases? I suspect that you've read something on an out-of-date web page and have made the change as you were simply following instructions..

(If you are using Kubuntu or Ubuntu 19.10 then the simplest remedy is to remove those repositories.)

---

### Post by adavel on 2019-10-23
Yes, I think I did what you say. I read the instructions in an old forum and I think that was how that repository was added. I removed it but I am still unable to update.
edit: And yes, I confirm, I am using the latest version of Kubuntu, which is 19.10

---

### Post by PaulW2U on 2019-10-23
Ok, obviously a lesson learned then - only use repositories for the release that you are using.  :)

What errors are you getting? In a terminal run 
```
sudo apt update
```
and post the output between [NOPARSE]```

```[/NOPARSE] tags, thanks.

---

### Post by adavel on 2019-10-25
Hey buddy. I'm really sorry to answer too late, I've had a lot of work. But I still want to try to solve this.
  This is what happens when I use sudo apt update

[COLOR=#000000]```
[/COLOR]angel @ 300e4angel: ~ $ sudo apt update
Obj: 1 http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu eoan InRelease
Reading package list ... Done
Creating dependency tree
Reading status information ... Done
All packages are updated.[COLOR=#000000]
```

[/COLOR]Maybe I should mention that I translated the content of bash konsole into English, because my native language is Spanish

---

### Post by PaulW2U on 2019-10-26
You seem to have removed all the repositories rather than just those that you erroneously added and which were related to the maverick release.

In post #5 you said "I removed it" but what did you actually remove?

A default /etc/apt/sources.list for the eoan release after cleaning up should, for a UK user such as myself, look like:
```
deb http://archive.canonical.com/ubuntu/ eoan partner
deb http://gb.archive.ubuntu.com/ubuntu/ eoan main restricted universe multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ eoan-backports main restricted universe multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ eoan-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ eoan-security main restricted universe multiverse

```
What are the contents of **your** /etc/apt/sources.list?

---

