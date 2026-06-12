---
title: "RO can't edit?"
date: 2004-11-07
forum: General Help
---

### Post by Nomad on 2004-11-07
My /ect/apt/sources.list is RO?  How do I uncomment lines to get universal?

---

### Post by im_ka on 2004-11-07
you need root privileges to edit it.

```
sudo gedit /etc/apt/sources.list
```

---

### Post by mercurus on 2004-11-08
Your best option is to use Synaptic which is available from:
Computer -> System Configuration -> Synaptic

You will be prompted for your password, supply that, and when the program opens go to:
Settings -> Repositories

You can find the universal repository in the greyed out lists below. Select each deb (not deb-src) repository and look at the bottom section of the window for the word "universal". Once that repository is selected, close the repository settings window and click "Re-load" from the Synaptic toolbar. After a short download, APT will be aware of all the packages in the universal repository.

Then you can use apt-get or Synaptic to retrieve the packages you want.

Cheers
mercurus

---

