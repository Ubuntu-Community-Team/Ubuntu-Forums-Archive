---
title: "own repository + customized debs"
date: 2007-02-03
forum: General Help
---

### Post by seppo on 2007-02-03
Currently I'm working on a Linux Enterprise desktop for a small organization. One of the things we would like to do, is to create a local apt repository with apt-mirror to make our own patch management. We would like to do 2 things:

- add our own debs for post-configuration tasks
- customize existing packages (i.e.[I]kubuntu-default-settings)

[/I]I know how to make my own debs, but I don't know how to merge them within a local repository. How do I prevent a customized deb (i.e.*kubuntu-default-settings)* being overruled with a newer version of the kubuntu official mirror? Is it possible to exclude packages with apt-mirror?

Any recommendations/ experiences would be great to hear!

---

### Post by seppo on 2007-02-04
subtile kick

To be clear: I'm building an apt-mirror and a custom repository with self-compiled packages to feed my workstation clients with packages. The problem is that Iwant to distribute a custom kubuntu-default-settings deb. Do I need to filter out the offical kubuntu-default-settings package in the apt-mirror config (how do I do that?) or is there a way to overrule the kubuntu-default-settings with my custom kubuntu-default-settings?

---

### Post by seppo on 2007-02-12
Update

It looks like apt-pinning is the (only) way to go. If somebody else is interested:
[http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)

---

