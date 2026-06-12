---
title: "Install docker on 17.04"
date: 2017-04-04
forum: General Help
---

### Post by drsinger111 on 2017-04-04
Hi, 


I am looking for a way to install Docker on zesty. 

root@server:/usr/src# cat /etc/*-releaseDISTRIB_ID=Ubuntu
DISTRIB_RELEASE=17.04
DISTRIB_CODENAME=zesty
DISTRIB_DESCRIPTION="Ubuntu Zesty Zapus (development branch)"
NAME="Ubuntu"
VERSION="17.04 (Zesty Zapus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu Zesty Zapus (development branch)"
VERSION_ID="17.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=zesty
UBUNTU_CODENAME=zesty

In reviewing the dox for docker, I tried installing via the script 

curl -fsSL [https://get.docker.com/](https://get.docker.com/) | sh

and after it pulled the gpg key, added the repo and searched, I see that zesty does not have a release available:

Reading package lists... Done
W: The repository 'https://download.docker.com/linux/ubuntu zesty Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'https://apt.dockerproject.org/repo ubuntu-zesty Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [https://download.docker.com/linux/ubuntu/dists/zesty/stable/binary-amd64/Packages](https://download.docker.com/linux/ubuntu/dists/zesty/stable/binary-amd64/Packages)  404  Not Found
E: Failed to fetch [https://apt.dockerproject.org/repo/dists/ubuntu-zesty/main/binary-amd64/Packages](https://apt.dockerproject.org/repo/dists/ubuntu-zesty/main/binary-amd64/Packages)  403  Forbidden
E: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists...
Building dependency tree...
Reading state information...
E: Unable to locate package docker-engine


questions is, is there a way around this other than installing from source?

---

### Post by Frogs Hair on 2017-04-04
Docker as in KDE system tray or docker.io (Linux container Runtime) ? If it is the latter . ```
sudo apt install docker.io
```

---

### Post by Habitual on 2017-04-04
Docker proper requires a 64 bit architecture.

---

### Post by auspex on 2017-06-03
> **Frogs Hair said:**
> Docker as in KDE system tray or docker.io (Linux container Runtime) ? If it is the latter . ```
sudo apt install docker.io
```

Well it's obviously the containers (docker.com, as the OP said), but isn't docker.io *hugely* obsolete?

As usual, Ubuntu version numbers tend not to match anybody else's, but if I am interpreting correctly, the current version is 17.05 (or maybe greater—thhat's what I currently have) and the docker.io version is 12!  I suspect one might have trouble with the docker config files you download, as there's a good chance of an API change in there.

---

### Post by Habitual on 2017-06-03
may not be a zesty release *yet*?
Older version of docker should still work, if the 64 bit and kernel min. is adhered to.

Docker requires a 64-bit installation.
Ubuntu: kernel must be 3.10 at minimum.

Installation
Code:
```

apt-get install -y curl && curl -sSL https://get.docker.com/ | sh
```
may be the ticket.

```
You're using 'linuxmint' version 'rosa'.
Upstream release is 'ubuntu' version 'trusty'.
[sudo] password for jj: 
```

No "zesty" at [https://store.docker.com/editions/community/docker-ce-server-ubuntu](https://store.docker.com/editions/community/docker-ce-server-ubuntu)

[https://docs.docker.com/engine/userguide/](https://docs.docker.com/engine/userguide/)

---

### Post by Frogs Hair on 2017-06-03
> [COLOR=#000000]Well it's obviously the containers (docker.com, as the OP said), but isn't docker.io [/COLOR]*hugely obsolete?*

I was using 17.04 when I found docker . io in synaptic and still see it in the Artful  development release , but I'm running an upgrade.

---

