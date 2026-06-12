---
title: "sudo with npm"
date: 2015-09-09
forum: General Help
---

### Post by Sky_Dog on 2015-09-09
Hi all,

I have executed ```
npm install -g embark-framework grunt-cli
```, but I get the following error 


```
 npm ERR! Error: EACCES, unlink '/usr/bin/grunt'
```



[http://paste.ubuntu.com/12323643/](http://paste.ubuntu.com/12323643/)

Is it really recommended to use npm with sudo?

Regards
SkyDog

---

### Post by sandyd on 2015-09-09
You asked npm to install Grunt, and npm is attempting to install it in /usr/bin, which requires sudo permissions.

If grunt is already installed, then remove it, and then run again with sudo.

---

### Post by Sky_Dog on 2015-09-12
> **sandyd said:**
> You asked npm to install Grunt, and npm is attempting to install it in /usr/bin, which requires sudo permissions.

If grunt is already installed, then remove it, and then run again with sudo.

Hi Sandyd,

is there a way to know how a program was installed? I tried to deinstall "grunt", but no way ... :-(

skydog@Merlin:~$ sudo npm uninstall -g grunt
[sudo] password for skydog: 
npm WARN uninstall not installed in /usr/lib/node_modules: "grunt"
skydog@Merlin:~$ npm uninstall -g grunt
npm WARN uninstall not installed in /usr/lib/node_modules: "grunt"

I thought that I installed it with npm

---

### Post by Sky_Dog on 2015-09-12
> **sandyd said:**
> You asked npm to install Grunt, and npm is attempting to install it in /usr/bin, which requires sudo permissions.

If grunt is already installed, then remove it, and then run again with sudo.

Hi Sandyd,

I've been able to deinstall it with "sudo npm -g uninstall grunt-cli"

The problem is that when I execute "[COLOR=#000000]npm install -g embark-framework grunt-cli[/COLOR]", I get the error 

**npm ERR! Error: EACCES, symlink '../lib/node_modules/grunt-cli/bin/grunt'**

[http://paste.ubuntu.com/12378110/](http://paste.ubuntu.com/12378110/)

Any idea what is happening now? I already deinstalled it and it still have problems with grunt

---

### Post by Sky_Dog on 2015-09-13
ok, I used sudo to resolve it

---

