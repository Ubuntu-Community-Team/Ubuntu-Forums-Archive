---
title: "sshfs bandwidth problem"
date: 2014-08-22
forum: General Help
---

### Post by Peptid on 2014-08-22
Dear All,

I am working on a SGE cluster which has around 16 cores. Since I cannot run specific programs on it, I rather to mount my cluster directories onto my laptop, edit files (using vim)/perform some calculations (with MATLAB or Julia) and then use them in the cluster. I do this via sshfs since it automatically updates my files on the cluster as I change them locally. However, I received an email from sysad telling me that 'my sshfs mount saturates 1Gbps ethernet interface and causing wait i/o problems. I do not think that I can use such a bandwidth and therefore I am suspicious that something else might be going on. My first inclanation was to think if there is an indexing going on as I use sshfs. So, my first question is if it is possible to saturate such an ethernet interface. Secondly, since I think I am using it in a very low pace, I wonder what might be happening.

I am using Kubuntu 14.04. All the operations I perform locally are changing several files with vim etc. whcih is not larger then a Mb.

Cheers.

---

