---
title: "Help: purging parallels"
date: 2007-12-06
forum: General Help
---

### Post by JaggedOne on 2007-12-06
I recently installed [Parallels]("http://www.parallels.com/") on my computer and uninstalled it. However it is not entirely gone. Sometimes when I shut down my machine I see some text flash by about loading parallels. Also, in my restricted drivers menu there are two parallels drivers: "main module for parallels virtual machine" and "parallels hypervisor". I have them both disabled, but the hypervisor still says it is in use.

A friend of mine recently had his ubuntu machine go haywire and he blames parallels. I want the software off my system. Can anyone help?

If any more information is needed to help solve the problem I will be glad to give it.

---

### Post by JaggedOne on 2007-12-06
Anyone?

---

### Post by JaggedOne on 2007-12-07
Someone? I could really use an answer.

---

### Post by mali2297 on 2007-12-07
How did you uninstall it? 

There is an option in Synaptic to remove a package totally.

---

### Post by JaggedOne on 2007-12-07
There was an uninstall script that came with the tarball I downloaded. I just searched for "parallel" in synaptic. Nothing came up as installed.

---

### Post by stoodleysnow on 2007-12-07
Synaptic is very finicky about spellings. 'parallel' will not necessarily bring up 'parallels'
Also, try doing a wide Beagle search for parallels, see what files come up and post a list of them on here, then we can tell you which ones need deleting or editing.:)

---

### Post by mali2297 on 2007-12-07
There is a deb package on their web site:
[http://www.parallels.com/en/download/workstation/](http://www.parallels.com/en/download/workstation/)

You could try to install the deb package, then remove it totally in Synaptic.

If that doesn't work, remove the directories/files
> 
/usr/lib/parallels/
/usr/share/doc/parallels/
/usr/sbin/parallels-config


Then check for broken links:
```

sudo apt-get install symlinks
symlinks -r /usr | grep ^dangling

```
If you want to remove the dangling links, run
```

sudo symlinks -rd /usr

```

---

