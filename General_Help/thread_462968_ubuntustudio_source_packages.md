---
title: "ubuntustudio source packages?"
date: 2007-06-03
forum: General Help
---

### Post by AzraelUK on 2007-06-03
Hi,
I recently installed the ubuntustudio-look package (among other ubuntustudio packages) and I've noticed a couple of bugs in the theme. Not being the sort of person to just complain about it I thought I would be able to download the source packages for ubuntustudio-theme, and change it. Apparently not: 
```
peter@N00B-PC:~/us$ apt-get source ubuntustudio-theme
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for ubuntustudio-look
peter@N00B-PC:~/us$ 

```

I've added the appropriate deb-src line to my /etc/apt/sources.list, and this happens for ALL the ubuntustudio packages I've tried.

Any chance of them getting added to the repos?

---

### Post by RAdams on 2007-06-06
The source packages are linked on Launchpad. (e.g.: [https://launchpad.net/ubuntu/feisty/+source/ubuntustudio-meta](https://launchpad.net/ubuntu/feisty/+source/ubuntustudio-meta))

---

