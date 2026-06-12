---
title: "failed installation of apt-show-versions"
date: 2015-07-02
forum: General Help
---

### Post by dragonfly41 on 2015-07-02
Recently I started testing a Ubuntu 14.04 container on nitrous.io (free account).  
The container info is Ubuntu 14.04.2 LTS 3.16.0-34-generic.

I have installed packages such as PHP5/Apache2/MySQL on nitrous.io Ubuntu container without encountering problems.
But when I try to install package apt-show-versions on nitrous.io Ubuntu container I hit these errors.

...
...
[COLOR=#0000cd]Setting up apt-show-versions (0.22.3) ...
** initializing cache. This may take a while **
Error: No information about packages! (Maybe no deb entries?)
dpkg: error processing package apt-show-versions (--configure):
 subprocess installed post-installation script returned error exit status 255
Errors were encountered while processing:
 apt-show-versions
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]

...

Now I have searched around and followed the clue about postinstallation script error.

[http://serverfault.com/questions/227190/how-do-i-ask-apt-get-to-skip-any-interactive-post-install-configuration-steps](http://serverfault.com/questions/227190/how-do-i-ask-apt-get-to-skip-any-interactive-post-install-configuration-steps)

So reading suggestions from above I tried

[COLOR=#0000cd]export DEBIAN_FRONTEND=noninteractive
apt-get -y install apt-show-versions[/COLOR]

But I still see ...

[COLOR=#0000cd]Errors were encountered while processing:
 apt-show-versions[/COLOR]

I also tried purging, cleaning up and reinstalling as follows ..

[COLOR=#0000cd]sudo dpkg -P apt-show-versions
sudo apt-get update
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update && sudo apt-get upgrade
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get -y install apt-show-versions[/COLOR]

Any suggestions to troubleshoot this particular road block with apt-show-versions?
Where is the post-installation script for apt-show-versions package?

---

### Post by dino99 on 2015-07-02
sorry i have no clue about 'container'; but that let me thinking first of a path issue. May be dig around container/lxc+path declaration

---

### Post by steeldriver on 2015-07-02
What happens if you try running

```

sudo apt-show-versions -i -v

```

---

### Post by dragonfly41 on 2015-07-02
If I run sudo apt-show-versions -i -v
on my local Ubuntu
I see a stream of lines Parsing 

here is one line ..

Parsing /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_trusty-updates_restricted_binary-i386_Packages... completed.

and parsing completes without errors.

...

If I now run the same command sudo apt-show-versions -i -v
on nitrous.io Ubuntu

I see ..
Error: No information about packages! (Maybe no deb entries?)

...

[added note]

Incidentally "container" is a nitrous.io term
I have a test workspace and in nitrous.io I can install multiple pre-packaged containers such as Ubuntu, Node.js, etc.
I am starting with Ubuntu.
But apt-show-versions is a dependency for webmin.

---

### Post by dragonfly41 on 2015-07-02
More info ... differences between local and remote Ubuntu configurations.

In nitrous.io Ubuntu

/var/lib/apt/lists all contents end in .gz


In local Ubuntu
/var/lib/apt/lists contents do not end in .gz (i.e. not compressed)

In nitrous.io Ubuntu
/etc/apt/apt.conf.d

02compress-indexes
02compress-indexes.save


and running sudo nano /etc/apt/apt.conf.d/02compress-indexes

I see ..
Acquire::GzipIndexes "true";


In local Ubuntu
there is no compress-indexes file.


...
[added note]

So something related to compressed lists in /var/lib/apt/lists?

[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=617856](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=617856)

---

