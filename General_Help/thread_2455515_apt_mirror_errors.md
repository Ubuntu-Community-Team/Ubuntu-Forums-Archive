---
title: "apt mirror errors"
date: 2020-12-21
forum: General Help
---

### Post by rich7 on 2020-12-21
Hi All,

I run a server in Hetzner but Ubuntu in is not my forte so usually google whatever I need to accomplish.  But for this one, I'm unsure where to turn.

I get the following output with mixture of errors when running any form of sudo apt update.


```
Hit:1 [http://mirror.hetzner.de/ubuntu/packages](http://mirror.hetzner.de/ubuntu/packages) disco InRelease
Ign:2 [http://mirror.hetzner.de/ubuntu/packages](http://mirror.hetzner.de/ubuntu/packages) disco-backports InRelease
Ign:3 [http://mirror.hetzner.de/ubuntu/packages](http://mirror.hetzner.de/ubuntu/packages) disco-security InRelease
Ign:4 [http://mirror.hetzner.de/ubuntu/packages](http://mirror.hetzner.de/ubuntu/packages) disco-updates InRelease
Hit:5 [http://mirror.hetzner.de/ubuntu/packages](http://mirror.hetzner.de/ubuntu/packages) bionic InRelease
Hit:6 [http://mirror.hetzner.de/ubuntu/packages](http://mirror.hetzner.de/ubuntu/packages) bionic-updates InRelease
Hit:7 [http://mirror.hetzner.de/ubuntu/packages](http://mirror.hetzner.de/ubuntu/packages) bionic-backports InRelease
Hit:8 [http://mirror.hetzner.de/ubuntu/packages](http://mirror.hetzner.de/ubuntu/packages) bionic-security InRelease
Hit:9 [http://repo.ombi.turd.me/develop](http://repo.ombi.turd.me/develop) jessie InRelease
Err:10 [https://apt.dockerproject.org/repo](https://apt.dockerproject.org/repo) ubuntu-xenial InRelease
 Something wicked happened resolving 'apt.dockerproject.org:https' (-5 - No address associated with hostname)
Err:11 [http://mirror.hetzner.de/ubuntu/packages](http://mirror.hetzner.de/ubuntu/packages) disco-backports Release
 404  Not Found [IP: 2a01:4f8:0:1::1:97 80]
Err:12 [http://mirror.hetzner.de/ubuntu/packages](http://mirror.hetzner.de/ubuntu/packages) disco-security Release
 404  Not Found [IP: 2a01:4f8:0:1::1:97 80]
Err:13 [http://mirror.hetzner.de/ubuntu/packages](http://mirror.hetzner.de/ubuntu/packages) disco-updates Release
 404  Not Found [IP: 2a01:4f8:0:1::1:97 80]
Ign:14 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) trusty InRelease
Hit:15 [http://download.mono-project.com/repo/ubuntu](http://download.mono-project.com/repo/ubuntu) xenial InRelease
Hit:16 [http://download.mono-project.com/repo/debian](http://download.mono-project.com/repo/debian) jessie InRelease
Ign:17 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty InRelease
Hit:18 [https://downloads.plex.tv/repo/deb](https://downloads.plex.tv/repo/deb) public InRelease
Ign:19 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) disco InRelease
Hit:20 [http://apt.sonarr.tv](http://apt.sonarr.tv) develop InRelease
Hit:21 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) trusty-updates InRelease
Hit:22 [http://ppa.launchpad.net/certbot/certbot/ubuntu](http://ppa.launchpad.net/certbot/certbot/ubuntu) disco InRelease
Hit:23 [https://apt.sonarr.tv/debian](https://apt.sonarr.tv/debian) stretch InRelease
Hit:24 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty Release
Hit:25 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) trusty-backports InRelease
Ign:26 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) disco-updates InRelease
Hit:27 [https://download.mono-project.com/repo/ubuntu](https://download.mono-project.com/repo/ubuntu) stable-bionic InRelease
Hit:28 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) disco InRelease
Hit:29 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) trusty-proposed InRelease
Ign:30 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) disco-backports InRelease
Hit:31 [http://ppa.launchpad.net/jcfp/ppa/ubuntu](http://ppa.launchpad.net/jcfp/ppa/ubuntu) disco InRelease
Get:32 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) disco InRelease [44.4 kB]
Hit:33 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) trusty Release
Err:34 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) disco Release
 404  Not Found [IP: 141.30.62.24 80]
Hit:35 [http://packages.cloud.google.com/apt](http://packages.cloud.google.com/apt) cloud-sdk-disco InRelease
Err:36 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) disco-updates Release
 404  Not Found [IP: 141.30.62.24 80]
Hit:37 [http://ppa.launchpad.net/jcfp/sab-addons/ubuntu](http://ppa.launchpad.net/jcfp/sab-addons/ubuntu) disco InRelease
Err:38 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) disco-backports Release
 404  Not Found [IP: 141.30.62.24 80]
Hit:39 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security InRelease
Ign:40 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security InRelease
Err:41 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security Release
 404  Not Found [IP: 2001:67c:1562::15 80]
Reading package lists... Done
E: The repository 'http://mirror.hetzner.de/ubuntu/packages disco-backports Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://mirror.hetzner.de/ubuntu/packages disco-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://mirror.hetzner.de/ubuntu/packages disco-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://de.archive.ubuntu.com/ubuntu disco Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://de.archive.ubuntu.com/ubuntu disco-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://de.archive.ubuntu.com/ubuntu disco-backports Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://security.ubuntu.com/ubuntu disco-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Skipping acquire of configured file 'stable/source/Sources' as repository 'https://download.docker.com/linux/ubuntu disco InRelease' does not seem to provide it (sources.list entry misspelt?)
W: Skipping acquire of configured file 'edge/source/Sources' as repository 'https://download.docker.com/linux/ubuntu disco InRelease' does not seem to provide it (sources.list entry misspelt?)

```

Updates do still come down, but unsure why this is happening? Guess some of those sources are out of date or something?  Any help on how to resolve would be appreciated.

Thanks,
Rich

---

### Post by ActionParsnip on 2020-12-21
Disco is EOL and no longer supported. If you are running Disco then you should uninstall this and reinstall with a clean version of Focal. Focal is LTS and supported until April 2025. If you are using Trusty then I recommend the same. Its an old old release.

---

### Post by rich7 on 2020-12-21
First step.. find out what I'm using! :D

---

### Post by deadflowr on 2020-12-21
> **rich7 said:**
> First step.. find out what I'm using! :D
```
lsb_release -a
```
will give you what the system thinks it is.

Frankenbuntu can never be a good thing.
Sounds like cleaning up via backup and clean install is in it's future.

---

### Post by Impavidus on 2020-12-21
I see a mixture of disco, xenial, trusty, bionic and some non-ubuntu sources. Disco and trusty are dead, xenial is nearly dead. I have to agree with deadflowr.

---

### Post by rich7 on 2020-12-22
Right, that set me on the right direction.  Tidied up loads of sources and upgraded to focal 20.04 with help from this guide [https://www.knowledgepublisher.com/article/1452/solution-an-upgrade-from-disco-to-focal-is-not-supported-with-this-tool.html](https://www.knowledgepublisher.com/article/1452/solution-an-upgrade-from-disco-to-focal-is-not-supported-with-this-tool.html)

757 packages upgraded, 247 newly installed :o.

> **Impavidus said:**
> Disco and trusty are dead

I've got rid of everything Disco & trusty now from the sources.list and everything inside etc/apt/sources.list.d/ , updating them where nessesary.  Sent me down many a rabbit hole upgrading, removing, changing xyz.. but it all now looks good! And more importantly, it's all working still!

> Hit:1 [http://mirror.hetzner.de/ubuntu/packages](http://mirror.hetzner.de/ubuntu/packages) focal InRelease
Hit:2 [http://mirror.hetzner.de/ubuntu/packages](http://mirror.hetzner.de/ubuntu/packages) focal-backports InRelease
Hit:3 [http://mirror.hetzner.de/ubuntu/packages](http://mirror.hetzner.de/ubuntu/packages) focal-security InRelease
Hit:4 [http://mirror.hetzner.de/ubuntu/packages](http://mirror.hetzner.de/ubuntu/packages) focal-updates InRelease
Hit:5 [http://download.mono-project.com/repo/ubuntu](http://download.mono-project.com/repo/ubuntu) xenial InRelease
Hit:6 [http://download.mono-project.com/repo/debian](http://download.mono-project.com/repo/debian) jessie InRelease
Hit:7 [http://apt.sonarr.tv](http://apt.sonarr.tv) develop InRelease
Hit:8 [http://repo.ombi.turd.me/develop](http://repo.ombi.turd.me/develop) jessie InRelease
Hit:9 [https://downloads.plex.tv/repo/deb](https://downloads.plex.tv/repo/deb) public InRelease
Hit:10 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) focal InRelease
Hit:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease
Hit:13 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal InRelease
Hit:14 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) focal InRelease
Hit:15 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) focal-updates InRelease
Hit:16 [https://apt.sonarr.tv/debian](https://apt.sonarr.tv/debian) stretch InRelease
Hit:17 [https://download.mono-project.com/repo/ubuntu](https://download.mono-project.com/repo/ubuntu) stable-bionic InRelease
Hit:18 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) focal-backports InRelease
Hit:19 [https://packages.cloud.google.com/apt](https://packages.cloud.google.com/apt) cloud-sdk InRelease
Reading package lists... Done
Building dependency tree
Reading state information... Done
All packages are up to date.

Thanks for pointing me in the right direction!

Rich

---

### Post by CelticWarrior on 2020-12-22
You still have a duplicated "mono-project" repository and neither is for focal. I suggest you remove the debian jessie one and edit the other replacing "xenial" with "focal". 

There is also another Debian repo that probably shouldn't be there. And only enable "backports" if there's really a reason for that, very likely there isn't.

When you don't even know which release you're running you definitely shouldn't be adding third-party repos willy-nilly. Do NOT blindly copy random web instructions without assuring that you know what you're doing, that the instructions including additions to the software sources support your specific release and that you understand and accept the risks.

---

### Post by ActionParsnip on 2020-12-22
> **rich7 said:**
> First step.. find out what I'm using! :D

Instead of silly games, why not just tell us. It helps nobody...most of all **you**&#8203;

---

