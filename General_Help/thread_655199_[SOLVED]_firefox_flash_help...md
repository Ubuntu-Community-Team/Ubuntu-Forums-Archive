---
title: "[SOLVED] firefox flash help.."
date: 2008-01-01
forum: General Help
---

### Post by illbashu on 2008-01-01
ok, i click on the thing that says download plugin and it goes finds the plugin and when i try to install it it says "flash-nonfree installed"(well something like that) then it closes the pluging finder/installer and refreshes the page and it say "click here to download plugin" again, is there a fix for this?

---

### Post by nick_h on 2008-01-01
Type 
```
about:plugins
```
in the address bar.  Is the flash plugin listed?

---

### Post by jespdj on 2008-01-01
This is a known bug in Ubuntu 7.10.

Unfortunately, the easy Flash install feature of Ubuntu 7.10 is broken because Adobe published a new version of Flash, and Ubuntu's easy installer gets confused by it.

See this thread for more info and a workaround:
[Bug #173890 flashplugin-nonfree md5 mispatch support thread]("http://ubuntuforums.org/showthread.php?t=636397")

Also see this one: [Workaround for adobe flash problem](http://ubuntuforums.org/showthread.php?t=639029)

[size="1"](p.s.: Please search before you post)[/size]

---

### Post by illbashu on 2008-01-01
i did use search... i downloaded the tar.gz file of flash 9 and i used the installer file in there with the terminal and it fixed the problem...

---

### Post by fparri on 2008-01-02
Other solution is downloading this backport from Hardy 8.04 and install it:

[http://rapidshare.com/files/80562619/flashplugin-nonfree_9.0.115.0ubuntu2_7.10prevu1_i386.deb.html](http://rapidshare.com/files/80562619/flashplugin-nonfree_9.0.115.0ubuntu2_7.10prevu1_i386.deb.html)

---

