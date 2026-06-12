---
title: "C header files for ubuntu?"
date: 2006-12-14
forum: General Help
---

### Post by jordn on 2006-12-14
hey,

installing vmware server on Ubuntu, and during the installation i get this:

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

i try and press enter to accept default, but i get this:

The path "/usr/src/linux/include" is not an existing directory.

which is true, as there is no such directory. i am following this guide:

[http://blog.wilf.me.uk/articles/2006/04/01/vmware-server-beta-on-ubuntu]("http://blog.wilf.me.uk/articles/2006/04/01/vmware-server-beta-on-ubuntu")

this may seem very trivial, but where would i find these C header files? are they available with the apt-get command?

thanks in advance, 

jordn

---

### Post by sefs on 2006-12-14
```
sudo apt-get install linux-headers-$(uname -r)
```

should install the headers for your distribution for the current kernel you have installed.

so for example if i were to run that it would place two directories i think in my /usr/src directory.

they would be....
1) /usr/src/linux-headers-2.6.17-10-386
2) /usr/src/linux-headers-2.6.17-10

Then at the appropriate point if it does not automatially detect them you can type it in as 
/usr/src/linux-headers-2.6.17-10-386/include

...something along those lines

---

