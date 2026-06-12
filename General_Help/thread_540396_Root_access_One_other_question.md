---
title: "Root access? One other question"
date: 2007-09-01
forum: General Help
---

### Post by Axis on 2007-09-01
When I try to use SU it asks for my password, I don't remember setting a password for root using wubi, so I tried to use my standard password and that did not work. So how do I find out/change my root password?

Also, I have read around (while trying to find the answer to my question) and there are people talking about 7.10. So I cannot upgrade to 7.10 if I installed with Wubi?

I'm not talking about using Wubi to install 7.10. I'm talking about just using all of my normal updates and getting to 7.10.

Thanks for your time, and also thanks for the great program (I wanted to dual boot before, but I was scared I would mess something up)

---

### Post by tuxcantfly on 2007-09-01
su isn't used in ubuntu, instead sudo is.

to get root access:

```
sudo -s
```

or

```
sudo su
```

or

```
sudo someapplicationyouwanttorunasroot
```

---

### Post by tuxcantfly on 2007-09-01
as for the upgrading to ubuntu 7.10, the application part should be doable within wubi, but you won't be able to upgrade the kernel, initrd, or some of the core boot scripts since they'll break the wubi loopmounted boot process. if you do want to upgrade to ubuntu 7.10 fully, kernel and everything, you'll need to transfer your install to a dedicated partition using LVPM at [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html) so that it behaves like a standard ubuntu install, and then you can upgrade it normally.

---

### Post by tuxcantfly on 2007-09-01
oh and of course the usual warning: ubuntu 7.10 hasn't been released yet (it'll only be released in october), don't use it on production systems or you may encounter breakage galore, it's meant only for developers and testers

---

### Post by Axis on 2007-09-02
Thanks, and I didn't plan on updating yet. I tried sudo aswell but the application said "this (something or other) dosen't have super cow powers" or something like that

---

### Post by aysiu on 2007-09-02
Instead of *something like that*, can you copy and paste exactly what you typed and exactly what the error message was?

Just highlight everything in the terminal and copy it back here.

---

### Post by tuxcantfly on 2007-09-02
super cow powers? sounds like aptitude or apt-get

I guess that must have been:

> This aptitude does not have Super Cow Powers.

which you get from entering

```
sudo aptitude --help
```

or

> This APT has Super Cow Powers.

which you get from entering

```
sudo apt-get --help
```

which I presume you were using to install software.

if you need a nice user-friendly way to install software, use synaptic in system -> administration -> synaptic package manager

if you need more details on using apt-get and synaptic, see [https://help.ubuntu.com/7.04/add-applications/C/advanced.html](https://help.ubuntu.com/7.04/add-applications/C/advanced.html)

---

### Post by Axis on 2007-09-03
I do use that normally, but I just wanted to install something really quick so I didn't want to go through all the trouble.

---

