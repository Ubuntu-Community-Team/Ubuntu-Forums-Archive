---
title: "Tor Browser not installing"
date: 2020-06-05
forum: General Help
---

### Post by doc1623 on 2020-06-05
Seems as if this hasn't been updated. I ran into several issues but finally got the launcher installed but when I run, it gets stuck here every time. 

```
$ torbrowser-launcher 
Tor Browser Launcher
By Micah Lee, licensed under MIT
version 0.3.2
https://github.com/micahflee/torbrowser-launcher
Downloading Tor Browser for the first time.
Downloading https://aus1.torproject.org/torbrowser/update_3/release/Linux_x86_64-gcc3/x/en-US
Latest version: 9.5
Downloading https://dist.torproject.org/torbrowser/9.5/tor-browser-linux64-9.5_en-US.tar.xz.asc
Downloading https://dist.torproject.org/torbrowser/9.5/tor-browser-linux64-9.5_en-US.tar.xz
Verifying Signature
Extracting tor-browser-linux64-9.5_en-US.tar.xz
TypeError: error() missing 1 required positional argument: 'message'
```



from uname

```
5.3.0-51-generic #44~18.04.2-Ubuntu SMP Thu Apr 23 14:27:18 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by DuckHook on 2020-06-05
[list=1]
[*]Which version and flavour of Ubuntu are you using? Your kernel is not the latest Focal kernel. Are you still on Eoan?
[*]How did you install torbrowser-launcher?
[LIST]
[*]From the Ubuntu Repos?
[*]From Tor's repos?
[*]From PPA?
[*]By standalone .deb file?
[*]Describe in as much detail as you can the steps that you took.
[/LIST][*]Is your base OS an upgraded install or a virgin install from USB?
[/list]

---

### Post by QIII on 2020-06-05
Moved to General Help.

Installation & Upgrades is for questions about installation or upgrade of the OS.

---

### Post by ActionParsnip on 2020-06-06
What is the output of:
```

lsb_release -a; uname -a; apt-cache policy torbrowser-launcher

```
Thanks

---

