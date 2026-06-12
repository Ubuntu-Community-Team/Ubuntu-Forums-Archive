---
title: "is this librewolf messege should worry me?"
date: 2024-08-23
forum: General Help
---

### Post by ronjjjg8885 on 2024-08-23
complicated to understand

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294119&stc=1[/IMG]

---

### Post by currentshaft on 2024-08-23
libre

---

### Post by &amp;KyT$0P# on 2024-08-23
That message also exists in Firefox code.  In Firefox, I think it would be related to [Ubuntu 24.04 unprivileged user namespace restrictions changes]("https://discourse.ubuntu.com/t/ubuntu-24-04-lts-noble-numbat-release-notes/39890#unprivileged-user-namespace-restrictions").

> **currentshaft said:**
> Is LibreWolf that thing where someone takes Firefox source code and builds it on less secure infrastructure, ensuring you are always behind published CVEs and other vulnerabilities?

Last I checked, LibreWolf is [this thing]("https://github.com/privacytools/privacytools.io/issues/2184#issuecomment-823802415").

---

### Post by ronjjjg8885 on 2024-08-23
so you are saying that i need to uninstall librewolf?

i can use brave instead.. i guess..

let me know..
if yes, does librewolf provide info on how it is uninstalled completely?

i hope i understand you correctly..

---

### Post by &amp;KyT$0P# on 2024-08-23
> **ronjjjg8885 said:**
> so you are saying that i need to uninstall librewolf?

Well, I wouldn't use it.

> does librewolf provide info on how it is uninstalled completely?

It depends, how did you install LibreWolf?

---

### Post by ronjjjg8885 on 2024-08-24
> **halogen2 said:**
> Well, I wouldn't use it.



It depends, how did you install LibreWolf?

i installed it like detailed here
[https://librewolf.net/installation/debian/](https://librewolf.net/installation/debian/)

---

### Post by ronjjjg8885 on 2024-08-24
would appreciate uninstallation instruction

and also.
which browser won't leave much fingerprints except for brave?

---

### Post by currentshaft on 2024-08-24
add

---

### Post by &amp;KyT$0P# on 2024-08-24
> **ronjjjg8885 said:**
> would appreciate uninstallation instruction

```
sudo apt --autoremove purge librewolf
sudo rm -v /etc/apt/sources.list.d/librewolf.sources /usr/share/keyrings/librewolf.gpg
sudo apt update
```

It probably also left behind caches in a subdirectory of [FONT=monospace]~/.cache[/FONT]

> which browser won't leave much fingerprints 

Tor Browser or Mullvad Browser

---

### Post by ronjjjg8885 on 2024-08-24
thank you for the information!!!

---

### Post by ronjjjg8885 on 2024-08-24
can i use the tor browser without the tor network?
i know protonvpn is not ideal but i use it as a vpn instead of slow tor.

let me know if tor can be used without the tor network.
i will try the  mullvad browser..

is there anything else you need to know about Brave?

edit..
do i need to install something called curl?..
```
sudo curl -fsSLo /usr/share/keyrings/mullvad-keyring.asc https://repository.mullvad.net/deb/mullvad-keyring.asc
sudo: curl: command not found

```

---

### Post by &amp;KyT$0P# on 2024-08-24
> **ronjjjg8885 said:**
> can i use the tor browser without the tor network?

That's what Mullvad Browser is.

> do i need to install something called curl?

You could:
```
sudo apt install curl
```

Alternatively, you could instead do that step with [FONT=monospace]wget[/FONT]
```
wget -O- https://repository.mullvad.net/deb/mullvad-keyring.asc | sudo tee /usr/share/keyrings/mullvad-keyring.asc
```

---

### Post by ronjjjg8885 on 2024-08-24
Big thanks

---

### Post by ronjjjg8885 on 2024-08-24
> **currentshaft said:**
> None, they all leave a fingerprint. Tor Browser is probably the one that leaves the smallest one.

Brave is a browser made by an ad company. Why anyone would think it makes for privacy is hilarious.

by the way.. what do you mean by ad company?

i'm using brave on android a lot [grapheneos]

---

### Post by currentshaft on 2024-08-24
http

---

### Post by ronjjjg8885 on 2024-08-25
why does mullvad browser is version 115 and firefox is 129?
i'm curious
shouldn't they be the same?

---

### Post by currentshaft on 2024-08-25
No

---

### Post by ronjjjg8885 on 2024-08-25
:)

---

