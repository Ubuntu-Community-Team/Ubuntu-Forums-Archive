---
title: "install ppa"
date: 2018-05-08
forum: General Help
---

### Post by MikeCyber on 2018-05-08
Hi
how to install:
[https://launchpad.net/~opentx-test/+archive/ubuntu/rel/+packages](https://launchpad.net/~opentx-test/+archive/ubuntu/rel/+packages)
on 16.04?
Thanks

---

### Post by slickymaster on 2018-05-08
If your referring to the OpenTX test PPA, in a terminal window run```
deb http://ppa.launchpad.net/opentx-test/rel/ubuntu xenial main 
deb-src http://ppa.launchpad.net/opentx-test/rel/ubuntu xenial main 
```

---

### Post by MikeCyber on 2018-05-08
```
michael@michael-All-Series:/$ deb [http://ppa.launchpad.net/opentx-test/rel/ubuntu](http://ppa.launchpad.net/opentx-test/rel/ubuntu) xenial main
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'dex' from package 'dex' (universe)
 Command 'derb' from package 'icu-devtools' (main)
 Command 'xdeb' from package 'xdeb' (universe)
 Command 'dub' from package 'dub' (universe)
 Command 'debi' from package 'devscripts' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'deb3' from package 'quilt' (universe)
deb: command not found
```

why not something alike sudo add-apt-repository ppa:? Thanks

---

### Post by slickymaster on 2018-05-08
Sorry, my previous instructions were meant to add the PPA manually to your system's software sources. What you want/need is ```
sudo add-apt-repository ppa:opentx-test/rel
sudo apt-get update
```

---

### Post by MikeCyber on 2018-05-08
Thanks

---

