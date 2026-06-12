---
title: "Trouble with alien"
date: 2007-12-17
forum: General Help
---

### Post by kenan6346 on 2007-12-17
I've just installed alien after much trouble; I looked up another post that had a similar problem that I had (I couldn't install dpkg-dev), I added more repositories and that seemed to be all fixed up. Then I installed alien that that seemed alright aswell, but after I tried to turn an rpm into a deb, I got this error message (I'll just copy out the entire terminal)

```
kenan@kenan-desktop:~$ cd /home/kenan/Desktop
kenan@kenan-desktop:~/Desktop$ su
Password: 
root@kenan-desktop:/home/kenan/Desktop# alien -d xorg.rpm
warning: xorg.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: xorg.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: xorg.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: xorg.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: xorg.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: xorg.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: xorg.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: xorg.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: xorg.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: xorg.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: xorg.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: xorg.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: xorg.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: xorg.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: xorg.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
warning: xorg.rpm: Header V3 DSA signature: NOKEY, key ID 4f2a6fd2
mkdir: cannot create directory `xorg-x11-devel-6.8.2': File exists
unable to mkdir xorg-x11-devel-6.8.2:  at /usr/local/share/perl/5.8.8/Alien/Package.pm line 257.
```

Can someone tell me whats goin on? Cheers

---

### Post by vapore0n on 2007-12-17
use sudo also

sudo alien -d

---

### Post by PmDematagoda on 2007-12-17
Personally I would recommend using Alien only **after** all other methods such as compiling and the repositories failed.

What are you planning to convert using Alien anyway and what do you want it for?

---

### Post by kenan6346 on 2007-12-17
@vapore0n: ```
kenan@kenan-desktop:~/Desktop$ sudo alien -i xx.rpm
warning: xx.rpm: Header V3 DSA signature: NOKEY, key ID db42a60e
warning: xx.rpm: Header V3 DSA signature: NOKEY, key ID db42a60e
warning: xx.rpm: Header V3 DSA signature: NOKEY, key ID db42a60e
warning: xx.rpm: Header V3 DSA signature: NOKEY, key ID db42a60e
warning: xx.rpm: Header V3 DSA signature: NOKEY, key ID db42a60e
warning: xx.rpm: Header V3 DSA signature: NOKEY, key ID db42a60e
warning: xx.rpm: Header V3 DSA signature: NOKEY, key ID db42a60e
warning: xx.rpm: Header V3 DSA signature: NOKEY, key ID db42a60e
warning: xx.rpm: Header V3 DSA signature: NOKEY, key ID db42a60e
warning: xx.rpm: Header V3 DSA signature: NOKEY, key ID db42a60e
warning: xx.rpm: Header V3 DSA signature: NOKEY, key ID db42a60e
warning: xx.rpm: Header V3 DSA signature: NOKEY, key ID db42a60e
warning: xx.rpm: Header V3 DSA signature: NOKEY, key ID db42a60e
warning: xx.rpm: Header V3 DSA signature: NOKEY, key ID db42a60e
warning: xx.rpm: Header V3 DSA signature: NOKEY, key ID db42a60e
warning: xx.rpm: Header V3 DSA signature: NOKEY, key ID db42a60e
warning: xx.rpm: Header V3 DSA signature: NOKEY, key ID db42a60e
```
p.x the reason it doesn't ask me to put in my sudo password is because I had just used it a second before to install a different program

@PmDematagoda: Well I just want to use it so I can install .rpm files because the system doesn't automatically recognize them and from the various forums on the internet I've looked at, alien is one of the best at doing that.

If there is some other program I can use instead of alien, please let me know about it.
Cheers

---

