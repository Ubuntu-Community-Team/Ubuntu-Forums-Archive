---
title: "Ubuntu 14.04, Remastersys, ssh error"
date: 2016-11-01
forum: General Help
---

### Post by johnnyysg on 2016-11-01
I use remastersys to clone an Ubuntu 14.04 installation which has numerous additional packages / software installed.

Everything works as expected on the cloned machine except ssh. 

On the cloned machine, I can ssh to its local ssh server without issue. i can also ssh to other machines without issue.

However from another machine, if i try to ssh into the cloned machine, i get the error 'no hostkey alg' on the client side.

The only solution i have found so far is to purge and reinstall openssh-server on the cloned machine, however this is not the ideal solution that i seek. 

Any reason for or solution to this error ? I dont understany why everything is cloned perfectly except ssh.

Any input is much appreciated.

---

