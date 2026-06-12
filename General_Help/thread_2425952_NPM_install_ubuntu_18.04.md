---
title: "NPM install ubuntu 18.04"
date: 2019-09-02
forum: General Help
---

### Post by indynaessens on 2019-09-02
Hi,

I wanted to install nodejs and npm for a project at work but for some reason it's not possible to install npm and I get the following error:

> Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/universe amd64 npm all 3.5.2-0ubuntu4 [1,586 kB]
Ign:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/universe amd64 npm all 3.5.2-0ubuntu4
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/universe amd64 npm all 3.5.2-0ubuntu4 [1,586 kB]
Err:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/universe amd64 npm all 3.5.2-0ubuntu4                                                                                                                               
  Undetermined Error [IP: 91.189.88.175 80]
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/n/npm/npm_3.5.2-0ubuntu4_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/n/npm/npm_3.5.2-0ubuntu4_all.deb)  Undetermined Error [IP: 91.189.88.175 80]                                                                     
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

I already tried the provided solution. Nodejs installed just fine.

---

### Post by Bashing-om on 2019-09-02
indynaessens; Hello - Welcome to the forum

On an adventure of discovery for npm
terminal:
```

sysop@x1804mini:~$ apt list npm
Listing... Done
npm/bionic,bionic 3.5.2-0ubuntu4 all
sysop@x1804mini:~$

```
so OK ! The package is in the repository.

More info:
```

sysop@x1804mini:~$ apt show npm
Package: npm
Version: 3.5.2-0ubuntu4
Priority: extra
Section: universe/web
<snip>
APT-Sources: http://mirror.steadfast.net/ubuntu bionic/universe amd64 Packages
Description: package manager for Node.js
<snip>

```
Now we know that npm resides in the universe repo (as well as nodejs)

The link is valid:
per:
[http://archive.ubuntu.com/ubuntu/pool/universe/n/npm/](http://archive.ubuntu.com/ubuntu/pool/universe/n/npm/)

And I am able to download npm with no issues.

So that begs the question of what is different in your system ?

What results with
```

sudo apt update
sudo apt upgrade
sudo apt install npm

```
And post back these full results.

see what we can do
[INDENT][INDENT]to see what is not going on
[/INDENT][/INDENT]

---

### Post by indynaessens on 2019-09-03
It installed just fine when I arrived at home and tried it again.
It is possible that it was a network issue at work.

Closing this thanks for the reply!

---

