---
title: "VMWARE- wont power on"
date: 2007-03-17
forum: General Help
---

### Post by mills on 2007-03-17
hi all,

was trying to sort out a sound problem in vmware but now i have a completely new problem, when i try to power on a virtual machine i get this error

"Unable to change virtual machine power state: Could not execute /usr/lib/vmware/bin/vmware-vmx."

this only happened recently after my attempts to sort the sound out and i just cant remember what or if i changed anything important

vmware-vmx is read only and executable and root is the owner, should i change any of this?

thanks in advance for any help

---

### Post by mills on 2007-03-17
ok i think maybe i should start from scratch, how about a way to remove all of it, shouldd i purge ( if yes then how?) 

as you probably guessed iam a noob

---

### Post by zvacet on 2007-03-17
```
sudo aptitude remove file_name
```
```
sudo aptitude --purge file_name
```
VMware server will be my choice.

---

### Post by mills on 2007-03-17
apparently my aptitude doesnt have super cow powers....i think it wants some more info?

---

