---
title: "uuencode/uudecode"
date: 2005-06-24
forum: General Help
---

### Post by xjlx on 2005-06-24
I don't know if I am in the right topic category or not but I was having trouble finding information on uuencode/uudecode it sounded like it was included with unix (maybe older distro's) 

I tried to apt-get it, but it wasn't there

I'm messing around on the Mod-X page and I'm pretty sure this is the encoding they are hinting at.

Thanks for any help.

---

### Post by ubuntujonez on 2008-04-06
hopefully you haven't been waiting almost 3 years for me to find this thread!

regards.

```
$ apt-cache search uuencode
sharutils - shar, unshar, uuencode, uudecode

$ sudo apt-get install sharutils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  mailx
The following NEW packages will be installed:
  sharutils
0 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
Need to get 108kB of archives.
After unpacking 991kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com gutsy/main sharutils 1:4.6.3-1build1 [108kB]
Fetched 108kB in 1s (56.1kB/s)   
Selecting previously deselected package sharutils.
(Reading database ... 109737 files and directories currently installed.)
Unpacking sharutils (from .../sharutils_1%3a4.6.3-1build1_i386.deb) ...
Setting up sharutils (1:4.6.3-1build1) ...

$ uuencode uuencoded 
begin 644 uuencoded
leet^D
%;&5E=`H`
`
end

```

---

### Post by vanadan on 2008-04-12
thanx :D

---

### Post by dcstar on 2008-04-12
> **ubuntujonez said:**
> hopefully you haven't been waiting almost 3 years for me to find this thread!
........

Or taking 30 seconds to do a search for "uuencode" in Synaptic would have produced many answers, why don't people do the simple option?

---

