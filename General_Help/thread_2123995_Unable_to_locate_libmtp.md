---
title: "Unable to locate libmtp?"
date: 2013-03-09
forum: General Help
---

### Post by gotnexusbluz on 2013-03-09
I have just installed Xubuntu, and am now trying to get mtpfs working on it.  After checking all of the available repository boxes in Software  Sources, here is what happened when I tried to install libmtp:
```

Me@MyPC:~$ sudo apt-get install libmtp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libmtp

```

I wondered if there are other repos which I should enable, and I found there are some they call "universal" on this page:
[URL="http://ubuntuguide.org/wiki/Ubuntu_Quantal_Repositories"]http://ubuntuguide.org/wiki/Ubuntu_Quantal_Repositories
[/URL]
When I attempted to connect with this command
```

Me@MyPC:~$ deb http://archive.ubuntu.com/ubuntu/ quantal main restricted
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
 Command 'xdeb' from package 'xdeb' (universe)
 Command 'dwb' from package 'dwb' (universe)
deb: command not found

```
I  nearly hit the floor - I know I've run this command before with at least one  installation of Ubuntu! I'm currently running Xubuntu now, but  anyway can anybody make sense of this? Is it normal in Xubuntu  QuantalQuetzel? 

Which repo is libmtp located on, and should I be able to connect to it while running Xubuntu 12.10?

---

### Post by schragge on 2013-03-09
Try ```
sudo apt-get install libmtp9
```

FYI ```

[COLOR=#008000]$[/COLOR] apt-cache pkgnames libmtp
[COLOR=#008000]libmtp9
libmtp-runtime
libmtp-dbg
libmtp-dev
libmtp-doc
libmtp-common[/COLOR]

```
Also, if you're doing it in bash,
```
[COLOR=#008000]$[/COLOR] sudo apt-get install libmtp**<Tab>**
``` should give you possible completions

---

### Post by gotnexusbluz on 2013-03-09
> **schragge said:**
> Try ```
sudo apt-get install libmtp9
```

FYI ```

[COLOR=#008000]$[/COLOR] apt-cache pkgnames libmtp
[COLOR=#008000]libmtp9
libmtp-runtime
libmtp-dbg
libmtp-dev
libmtp-doc
libmtp-common[/COLOR]

```
Also, if you're doing it in bash,
```
[COLOR=#008000]$[/COLOR] sudo apt-get install libmtp**<Tab>**
``` should give you possible completions

Thanks, it works! I guess xfce uses bash, and the tutorial I was using was for another shell?

---

### Post by schragge on 2013-03-09
> **gotnexusbluz said:**
> Thanks, it works! I guess xfce uses bash, and the tutorial I was using was for another shell?Nope, all Ubuntu flavours use bash by default. Rather the tutorial is either obsolete or wrong. Or both.

BTW, usually you don't install libmtp directly. Instead, install mtp-tools, and it will pull the right libmtp version as dependency:
```
sudo apt-get install mtp-tools
```

Dry run:
```

[COLOR=green]$[/COLOR] apt-get --dry-run install mtp-tools
[COLOR=green]NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libmtp-common libmtp-runtime libmtp9
The following NEW packages will be installed:
  libmtp-common libmtp-runtime libmtp9 mtp-tools
0 upgraded, 4 newly installed, 0 to remove and 1 not upgraded.
Inst libmtp-common (1.1.3-35-g0ece104-4 Debian:testing [all])
Inst libmtp9 (1.1.3-35-g0ece104-4 Debian:testing [amd64])
Inst libmtp-runtime (1.1.3-35-g0ece104-4 Debian:testing [amd64])
Inst mtp-tools (1.1.3-35-g0ece104-4 Debian:testing [amd64])
Conf libmtp-common (1.1.3-35-g0ece104-4 Debian:testing [all])
Conf libmtp9 (1.1.3-35-g0ece104-4 Debian:testing [amd64])
Conf libmtp-runtime (1.1.3-35-g0ece104-4 Debian:testing [amd64])
Conf mtp-tools (1.1.3-35-g0ece104-4 Debian:testing [amd64])[/COLOR]

```

---

