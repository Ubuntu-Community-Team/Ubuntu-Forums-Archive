---
title: "fontconfig on Ubuntu 20.04 with snap"
date: 2021-01-10
forum: General Help
---

### Post by franekw on 2021-01-10
Hello,

I am currently running Ubuntu 20.04. It has been sometime I have started having problems with `fontconfig`. I asked a question on AskUbuntu without success but somehow strong suggestion that I should solve problems by myself before asking. I am afraid I tried and I can't find any solution. The errors only occur when I try to refresh `snap`:

```
$ sudo snap refresh

error: cannot perform the following tasks:
- Run configure hook of "chromium" snap if present (run hook "configure":
-----
Fontconfig warning: "/etc/fonts/fonts.conf", line 5: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/fonts.conf", line 6: unknown element "its:translateRule"
Fontconfig error: "/etc/fonts/fonts.conf", line 6: invalid attribute 'translate'
Fontconfig error: "/etc/fonts/fonts.conf", line 6: invalid attribute 'selector'
Fontconfig error: "/etc/fonts/fonts.conf", line 7: invalid attribute 'xmlns:its'
Fontconfig error: "/etc/fonts/fonts.conf", line 7: invalid attribute 'version'
Fontconfig warning: "/etc/fonts/fonts.conf", line 9: unknown element "description"
free(): double free detected in tcache 2
/snap/chromium/1444/snap/command-chain/hooks-configure-desktop: line 43:   6755 Aborted                 (core dumped)  "${SNAP_DESKTOP_RUNTIME}/usr/bin/fc-cache" --force --system-only  --verbose
-----)
- Run configure hook of "zotero-snap" snap if present (run hook "configure":
-----
Fontconfig warning: "/etc/fonts/fonts.conf", line 5: unknown element "its:rules"
Fontconfig warning: "/etc/fonts/fonts.conf", line 6: unknown element "its:translateRule"
Fontconfig error: "/etc/fonts/fonts.conf", line 6: invalid attribute 'translate'
Fontconfig error: "/etc/fonts/fonts.conf", line 6: invalid attribute 'selector'
Fontconfig error: "/etc/fonts/fonts.conf", line 7: invalid attribute 'xmlns:its'
Fontconfig error: "/etc/fonts/fonts.conf", line 7: invalid attribute 'version'
Fontconfig warning: "/etc/fonts/fonts.conf", line 9: unknown element "description"
free(): double free detected in tcache 2
/snap/zotero-snap/23/snap/command-chain/hooks-configure-desktop: line  43:  6287 Aborted                 (core dumped)  "${SNAP_DESKTOP_RUNTIME}/usr/bin/fc-cache" --force --system-only  --verbose
-----)
```

I check `fontconfig` and it does not seem to be broken:

```
$ dpkg -l | grep fontconfig

ii  fontconfig                                    2.13.1-2ubuntu3                        amd64        generic font configuration library -  support binaries
ii  fontconfig-config                             2.13.1-2ubuntu3                        all          generic font configuration library -  configuration
ii  libfontconfig1:amd64                          2.13.1-2ubuntu3                        amd64        generic font configuration library -  runtime
```

I also checked if there are broken packages but things are ok:

```
$ sudo apt-get install -f
```

Anything I found and tried had no effect:

* clean the system:
```
$ sudo apt clean && sudo apt autoclean && sudo apt  autoremove && sudo apt update && sudo apt-get -y install  && sudo dpkg --configure -a
```

* rescan fonts:
```
$ sudo fc-cache -rv
$ cat /var/log/fontconfig.log
...
/var/cache/fontconfig: cleaning cache directory
fc-cache: succeeded
```

* reinstalling fontconfig:
```
$ sudo apt-get install --reinstall fontconfigfontconfig-config
```

* someone in `reddit` someone even suggested the full reinstall because I certainly broke something when upgrading the system:
```
$ sudo apt dist-upgrade && sudp apt upgrade && sudo apt update
```

which I believe was wrong suggestion. Anyway on a fresh system this problem came back to me again. At this point, I am totally clueless about what to do next. I tried to because

I found a post on [ArchLinux (https://bbs.archlinux.org/viewtopic.php?id=235643]("https://bbs.archlinux.org/viewtopic.php?id=235643")). Someone suggested to downgrade `fontconfig` from 2-13 to 2-12. I don't know if that is possible on Ubuntu. I guess something like `sudo apt-get install package=version` would do but I am not convinced this would work and I can't list different versions of the same package.

So I came here with hope that someone has similar problem to mine and have found something that works.

Thanks

---

