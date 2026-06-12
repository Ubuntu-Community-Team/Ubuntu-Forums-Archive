---
title: "Change in mounting iso images?"
date: 2016-02-06
forum: General Help
---

### Post by lieven-debels on 2016-02-06
In recent ubuntu versions (15.10, but also in debian 8, if that matters) I'm having problems mounting an iso image correctly.
The command to do so should be:

```
sudo mount -o loop /path/to/iso /mountpoint
```
Terminal output shows: ```
mount: /dev/loop0 is write-protected, mounting read-only
```

The problem is, Wine cannot see the mounted image. I'm posting here because I guess the problem is not Wine-related.
In ubuntu 14.04 LTS however, when executing the same command as above, I get different terminal output:

```
mount: block-device /path/to/iso is write-protected, mounting read-only
```

Here Wine does see the mounted image.
Why do I get a message about /dev/loop0 in 15.10, when I'm just mounting an iso, and more importantly, why can't Wine access the iso contents?

Thanks for helping out.

---

### Post by lieven-debels on 2016-02-09
Ok, found the solution.
Seems from now on it's needed to install recommended packages of wine and playonlinux.
I used to install like this (to have less bloat)
```
sudo apt-get install --no-install-recommends playonlinux
```
This command automatically pulls in wine, but apparently not all that is needed.
So I changed it to:
```
sudo apt-get install playonlinux
``` (omitted --no-install-recommends)
Now Wine can see the mounted image.

---

