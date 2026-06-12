---
title: "Update error - Brave Browser has been removed?"
date: 2023-07-17
forum: General Help
---

### Post by Alligator on 2023-07-17
I'm having problems with Gnome, mostly cursor and typing not happening. Batteries have been changed.

```

An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: https://brave-browser-apt-release.s3.brave.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8580BDC82D3DC6C
W: Failed to fetch https://brave-browser-apt-release.s3.brave.com/dists/stable/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8580BDC82D3DC6C
W: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  gjs libgjs0g

```

---

### Post by TheFu on 2023-07-17
```
$ dpkg -l |grep brave
ii  brave-browser                          1.52.130                                                             amd64        The web browser from Brave
```

That's a 20.04 system. Seems fine to me, but I patch only on the weekends.

```
$ inxi -r
Repos:
  Active apt repos in: /etc/apt/sources.list 
  1: deb http://us.archive.ubuntu.com/ubuntu focal main restricted
  2: deb http://us.archive.ubuntu.com/ubuntu focal-updates main restricted
  3: deb http://us.archive.ubuntu.com/ubuntu focal universe
  4: deb http://us.archive.ubuntu.com/ubuntu focal-updates universe
  5: deb http://us.archive.ubuntu.com/ubuntu focal multiverse
  6: deb http://us.archive.ubuntu.com/ubuntu focal-updates multiverse
  7: deb http://us.archive.ubuntu.com/ubuntu focal-backports main restricted universe multiverse
  8: deb http://us.archive.ubuntu.com/ubuntu focal-security main restricted
  9: deb http://us.archive.ubuntu.com/ubuntu focal-security universe
  10: deb http://us.archive.ubuntu.com/ubuntu focal-security multiverse
...
**  Active apt repos in: /etc/apt/sources.list.d/brave-browser-release.list **
...

```
seems fine.

So, what do you think caused it to be removed?  Does the APT history file have any hints?  Here's where those files are on my system.
```
$ locate history |grep /var
/var/log/apt/history.log
/var/log/apt/history.log.1.gz
/var/log/apt/history.log.2.gz

```
To be fair, my system was a fresh 20.04 install in May, so it is fairly clean.

---

### Post by Alligator on 2023-07-17
I uninstall brave, but the repos still remains
```

Ubuntu 22.04.2 LTS \n \l

Repos:
  Active apt repos in: /etc/apt/sources.list
    1: deb http://ca.archive.ubuntu.com/ubuntu/ jammy main restricted universe
    2: deb http://ca.archive.ubuntu.com/ubuntu/ jammy-updates main restricted universe
    3: deb http://ca.archive.ubuntu.com/ubuntu/ jammy multiverse
    4: deb http://ca.archive.ubuntu.com/ubuntu/ jammy-updates multiverse
    5: deb http://ca.archive.ubuntu.com/ubuntu/ jammy-backports main restricted multiverse universe
    6: deb http://ca.archive.ubuntu.com/ubuntu/ jammy-security main restricted universe
    7: deb http://ca.archive.ubuntu.com/ubuntu/ jammy-security multiverse
  No active apt repos in: /etc/apt/sources.list.d/anydesk-stable.list
  Active apt repos in: /etc/apt/sources.list.d/brave-browser-release.list
    1: deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg] https://brave-browser-apt-release.s3.brave.com/ stable main
  Active apt repos in: /etc/apt/sources.list.d/graphics-drivers-ubuntu-ppa-jammy.list
    1: deb https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu/ jammy main
  No active apt repos in: /etc/apt/sources.list.d/virtualbox.list
```

---

### Post by Alligator on 2023-07-17
brave-browser does not appear in "Software & Updates" but still remains in /etc/apt/sources.list.d   - Should I simply delete the file from /etc/apt/sources.list.d

---

### Post by Frogs Hair on 2023-07-18
Yes you can, but check the other software tab in software & updates first.

---

### Post by TheFu on 2023-07-19
You could reinstall the PPA, if you'd like to keep brave.  This should force an updated GPG key.

---

