---
title: "how to uninstall Grub? Pls HELP!!!!"
date: 2006-07-07
forum: General Help
---

### Post by Kouya on 2006-07-07
Hi all

I'm not sure if I am posting in the right place but I desperately need help. On one of my computers I need to uninstall ubuntu dapper. It is installed in my slave drive in a separate 20Gb harddrive. My windows OS is in another hard drive which is the master. 

I read somewhere to boot from WinXP disc and type fixmbr but it says it will destroy the partitions on my master disc..wat should i do??

Computer newbie here...pls help!! :confused:  :(  ](*,)

---

### Post by kb2wdi on 2006-07-07
The easiest way it to boot with a DOS 6.22 floppy;

[http://people.jyu.fi/~eejuviik/utils/boot622.exe](http://people.jyu.fi/~eejuviik/utils/boot622.exe)

and run "fdisk /mbr".

---

### Post by Jagot on 2006-07-07
The way you have done it with Windows will not destroy partitons and I'm sure it didn't say it would - it probably said something about destroying data on the MBR, which is what you want to do.  Try it again and read the warning it gives you properly.

Alternatively, you can do it the way kb2wdi has described, and if you don't have a flopp drive, you can do the same with the FreeDOS boot disk which comes in the form of a CD:

[http://www.freedos.org/](http://www.freedos.org/)

---

### Post by Kouya on 2006-07-07
i think it says it will destroy my partitions cos i do have other partitions on my master drive..

---

