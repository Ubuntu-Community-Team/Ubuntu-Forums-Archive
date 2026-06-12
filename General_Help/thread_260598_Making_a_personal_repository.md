---
title: "Making a personal repository"
date: 2006-09-19
forum: General Help
---

### Post by Fred Doolie on 2006-09-19
After reinstalling U/K/X/Edubuntu and waiting so very long for all those downloads for the 100th time I wondered two things.

1) Where are those downloaded files stored?
2) Can I move them into a partiton or a CD and use that for a local repository? Then I can reinstall a LOT LOT faster?
3) How would I do #2, the local repository part I mean?

---

### Post by Wolki on 2006-09-19
> **Fred Doolie said:**
> 
1) Where are those downloaded files stored?
2) Can I move them into a partiton or a CD and use that for a local repository? Then I can reinstall a LOT LOT faster?
3) How would I do #2, the local repository part I mean?

1) /var/cache/apt/archives.
2) Probably. It would probably be faster and easier to just backup that directory, and copy the files back after a new install. apt will not download them again if you already have the latest archive cached.

---

### Post by Fred Doolie on 2006-09-19
Oh OK. That'll work too. Thanks.

I was thinking though if I had my own CD repository I could install Ubuntu on other's systems that didn't have an Internet connection.

---

### Post by textguru on 2006-10-18
> **Wolki said:**
> 1) /var/cache/apt/archives.
2) Probably. It would probably be faster and easier to just backup that directory, and copy the files back after a new install. apt will not download them again if you already have the latest archive cached.

How can I use these updates? I have tried this option but when I do the command:

```
sudo apt-get update
```

It is still getting updates on the internet. Do I need to change the repository list?

---

### Post by Wolki on 2006-10-18
> **textguru said:**
> How can I use these updates? I have tried this option but when I do the command:

```
sudo apt-get update
```

It is still getting updates on the internet. Do I need to change the repository list?

apt-get update updates the package list, that means it chacks the internet for which packages are available. This will pretty much need an internet connection, unless you do a local repo.

The actual updates, performed with "apt-get upgrade", "apt-get dist-upgrade" or the update manager/synaptic, will not be downloaded again, as long as there are no newer ones.

If you have no internet connection on that pc, you can still install the upgrades manually by clicking them or doing "dpkg -i filename.deb". This can be quite a lot of work, though.

---

### Post by textguru on 2006-10-18
what if I wanted to upgrade firefox from version 1.5.0.5 to 1.5.0.7 where I have already downloaded to the local /var/cache/apt/archives , how can I execute the update without connecting to the internet?

---

### Post by Wolki on 2006-10-19
According to packages.ubuntu.com, the package's name is firefox_1.5.dfsg+1.5.0.7-ubuntu0.6.06_i386.deb (if you're not on i386, check what it is for your architecture).

This should probably do the trick:
```
sudo dpkg -i /var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.7-ubuntu0.6.06_i386.deb
```

---

### Post by textguru on 2006-10-19
I have tried it but it seems that I need to install also the dependencies. Hope you can help me.

```
ubuntu@mypc:~$ sudo dpkg -i /var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.7-ubuntu0.6.06_i386.deb
Password:
(Reading database ... 53782 files and directories currently installed.)
Preparing to replace firefox 1.5.dfsg+1.5.0.5-0ubuntu6.06.1 (using .../firefox_1.5.dfsg+1.5.0.7-ubuntu0.6.06_i386.deb) ...
Unpacking replacement firefox ...
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on libnspr4 (>= 2:1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06); however:
  Version of libnspr4 on system is 2:1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06.1.
 firefox depends on libnss3 (>= 2:1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06); however:
  Version of libnss3 on system is 2:1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06.1.
dpkg: error processing firefox (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 firefox
ubuntu@mypc:~$

```

---

### Post by Wolki on 2006-10-19
Without using apt, you'll have to resolve the dependencies  yourself.

If you copied the stuff from another system where it was already installed, the dependencies should already be present. Looking at the output you posted, the missing stuff is libnspr4 and libnss3. I'm too lazy to look uo the exact versions, but we can use tab-completion.

Paste ```
sudo dpkg -i /var/cache/apt/packages/libnspr4
``` and press tab. It should either suggest you several things, of which you should choose the latest, or autocomplete it if there is only one package possible. Then do the same for the other required lib.

---

