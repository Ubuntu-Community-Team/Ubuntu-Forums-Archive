---
title: "Ubuntu 24.04:  Software Updater or Synaptic are not working"
date: 2024-05-05
forum: General Help
---

### Post by Machster28 on 2024-05-05
Neither can the Ubuntu Software Updater or the Synaptic Package Manager be launched at all.  

Trying to update manually using ```
sudo apt update
``` or ```
sudo apt-get update
``` yields: 

```
E: Malformed entry 1 in sources file /etc/apt/sources.list.d/third-party.sources (URI parse)
E: The list of sources could not be read.
```.


In etc/apt/sources.list.d/ubuntu.sources
are the following entries:

```
Types: deb
URIs: http://archive.ubuntu.com/ubuntu
Suites: noble noble-updates noble-backports
Components: main restricted universe multiverse
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg

Types: deb
URIs: http://security.ubuntu.com/ubuntu
Suites: noble-security
Components: main restricted universe multiverse
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg


```

How can I get Ubuntu 24.04 updates working again?

---

### Post by Claus7 on 2024-05-05
Hello,

what does /etc/apt/sources.list.d/third-party.sources has as its contents? Why don't you check this file instead and comment out all its lines and see what you will get? I do not have such a file in my system.

Regards!

---

### Post by Machster28 on 2024-05-05
Update: I removed  /etc/apt/sources.list.d/third-party.sources which was the ISO file from the previous install. Incredible that a new Ubuntu should keep such a file from the previous ISO install and block all updating software because of it.

Now Software Updater is at least opening again, however, since upgrading to 24.04, it keeps reporting the error : **Failed to download repository information.** **Check your internet conection**. It refuses to complete the update.

---

### Post by Machster28 on 2024-05-05
The above internet connection seems to have been caused by a third party debian update channel. Not sure why this channel was causing an issue all of a sudden in 24.04. Unactivating it keeps the Software Updater from the failing internet connection. I have 2 applications updating through the debian channel, one works, one doesn't. How can we keep our debian apps updated then?

---

### Post by Claus7 on 2024-05-05
Hello,

why don't you try to issue the commands via terminal and post here the exact output? I think that terminal might be a better way to find out exactly what the problem is.
From what I understand you removed the third party file and now you have a problem about internet. I suppose that you are posting from the same computer, which means that indeed you have internet connection, yet software updater is complaining that internet is not available.

Regards!

---

### Post by Machster28 on 2024-05-05
The above internet connection seems to have been caused by the third party debian update channel. Not sure why this channel was causing an issue all of a sudden in 24.04. Unactivating it in the Other Software settings keeps the Software Updater from the failing internet connection error. It still appears to be a correct URL update channel, but Ubuntu 24.04 doesn't see it somehow. I would think the correct response should be to skip this particular channel and continue with the rest of the updates.

---

### Post by Claus7 on 2024-05-06
Hello,

it might be that these channels are not fully updated yet for noble. So waiting a little might solve the issue. Indeed skipping the issue for now might be the best solution.

Regards!

---

### Post by Machster28 on 2024-05-06
Thanks Claus7. You're awesome!

---

