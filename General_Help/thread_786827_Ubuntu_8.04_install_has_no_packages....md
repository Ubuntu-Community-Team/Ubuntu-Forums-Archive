---
title: "Ubuntu 8.04 install has no packages..."
date: 2008-05-08
forum: General Help
---

### Post by Ancientmtk on 2008-05-08
I did a fresh install of Ubuntu 8.04, and I cannot find alot of the packages that normally come with other linux distro, such as ssh client, autofs, nfs, csh, etc.

Are those apps not included in the default installation?  I cannot use apt-get since my comp has firewall that does not allow me to get thru.

Thx all:popcorn:

---

### Post by Ancientmtk on 2008-05-08
Am i missing some steps during installation, or Ubuntu 8.04 don't include these apps?

---

### Post by chrisccoulson on 2008-05-08
The default Ubuntu Desktop installation includes the packages that are most commonly used by the average home desktop user, and the default packages are selected to minimize redundancy.

There is no nfs server on the default install.

autofs isn't installed by default, as it is redundant on a default installation of Ubuntu, where auto-mounting is handled by GVFS (Hardy) or gnome-volume-manager (pre-Hardy).

csh is included in the default install though), as is an SSH client (openssh-client)

---

### Post by dinofelis on 2008-06-19
> **Ancientmtk said:**
> Am i missing some steps during installation, or Ubuntu 8.04 don't include these apps?

I seem to have the same problem.  I installed Kubuntu 8.04, and when I type csh in a terminal, I get:
```
mypc@MYPC-UBUNTU:/$ csh
The program 'csh' can be found in the following packages:
 * csh
 * tcsh
Try: sudo apt-get install <selected package>
bash: csh: command not found
mypc@MYPC-UBUNTU:/$   
```

when I do that, I get:

```
mypc@MYPC-UBUNTU:/$ sudo apt-get install tcsh
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package tcsh
mypc@MYPC-UBUNTU:/$       
```

Now, I'm also behind a proxy, but synaptic seems to get through (I did install a few packages).  In synaptic, I found (and installed) the zsh, but not csh or tcsh which wasn't available...

---

### Post by dinofelis on 2008-06-19
Ooops, sorry.  I refreshed synaptic, and there was the csh package...

---

