---
title: "Can't find sshd server to install under Ubuntu 7.10"
date: 2008-01-03
forum: General Help
---

### Post by snowbug on 2008-01-03
I searched the forum but didn't find any related topics. It seems that I am missing something basic as other people didn't complained about this.

I can't seem to find the openssh-server or any ssh server from the "Add/Remove" application dialog. What is the package name that I need to install to enable ssh access? And what should I look for if that specific package does not show up in the available application list?

Thanks!

---

### Post by taurus on 2008-01-03
Maybe you didn't have all the repos available in /etc/apt/sources.list.  Click System -> Accessories -> Synaptic Package Manager -> Settings -> Repositories and make sure there is a check mark in front of all the lines except the last one, Source code and CDROM at the bottom window.  Close and click Refresh.  Now in the Search field, look for openssh-server again and install it.

---

### Post by snowbug on 2008-01-07
I actually already had those repositories checked. And I did find the openssh-server from the list in the Synaptic Package Manager. It turns out that this package is visible in the Synaptic Package Manager but not visible in the Add/Remove Applications dialog, and I was looking for it only in the add/remove app dialog. 

Many thanks for helping me get it solved!

Cheers!

---

