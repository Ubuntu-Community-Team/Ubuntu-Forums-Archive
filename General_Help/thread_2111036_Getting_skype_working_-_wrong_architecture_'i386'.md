---
title: "Getting skype working - wrong architecture 'i386' ?"
date: 2013-01-31
forum: General Help
---

### Post by linux_newf on 2013-01-31
When i downloaded skpye from the skype site i get wrong architecture 'i386' when it opens up the software center.

I used the windows installer to install unbuntu precise a few days ago.

```
brad@ubuntu:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package skype

```

Pretty sure i need to enabled the partner respos.?

---

### Post by linux_newf on 2013-01-31
More

```
brad@ubuntu:~$ sudo apt-get update && sudo apt-get install skype
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by gifford on 2013-01-31
Yes, enable partners repositories. I'm not sure what version of Ubuntu you are using. 12.04 is multiarch and allows the easy use of i386 on a 64 bit system.

As for installing, after you enable the repositories you could just use the software center to install. I think that will install any additional files you may need.

One word of caution, installing the skype wrapper has presented problems for me in Ubuntu 12.04, so I have had to reinstall Skype without the wrapper.

---

