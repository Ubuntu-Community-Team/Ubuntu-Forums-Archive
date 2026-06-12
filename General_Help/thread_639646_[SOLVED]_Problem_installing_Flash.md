---
title: "[SOLVED] Problem installing Flash"
date: 2007-12-13
forum: General Help
---

### Post by posterberg on 2007-12-13
I've just tried to install the non-free flash player on two machines without success.

```

sudo apt-get install flashplugin-nonfree
...
...
...
18:11:07 (172.87 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.
```I've tried to throw the -f option at apt-get to make it install even though the integrity check fails, that doesn't help either...

/p

---

### Post by foolsh on 2007-12-13
I had a similar problem but I got the flash-nonfree package to install but any sites requiring it said it wasn't installed.
so I went to the adobe site and downloaded the tar.gz pakage and followed the instructions on the abobe web site and now it works fine
note: when it asks you where to install "i.e /usr/lib/mozilla" type /usr/bin/firefox
try that it worked for me only hope it works for you.

---

### Post by Seisen on 2007-12-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.edge.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890](https://bugs.edge.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This link with explain everything

[http://ubuntuforums.org/showthread.php?t=636397]("http://ubuntuforums.org/showthread.php?t=636397")

---

### Post by posterberg on 2007-12-14
Thanks, worked like a charm!

---

