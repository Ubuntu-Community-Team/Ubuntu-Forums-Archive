---
title: "Help installing cdemu 0.8"
date: 2007-11-24
forum: General Help
---

### Post by MrNatewood on 2007-11-24
I tried to follow these instruction to install it:
[http://ubuntuforums.org/showthread.php?t=69530](http://ubuntuforums.org/showthread.php?t=69530)
But it didn't work. this is the errors i had after trying to "make":
```
mrnatewood@shimi:~/cdemu-0.8$ sudo ls -la /lib/modules/2.6.22-14-generic/build
lrwxrwxrwx 1 root root 40 2007-10-19 10:25 /lib/modules/2.6.22-14-generic/build -> /usr/src/linux-headers-2.6.22-14-generic
mrnatewood@shimi:~/cdemu-0.8$ sudo make
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/mrnatewood/cdemu-0.8/cdemu_mod.o
/home/mrnatewood/cdemu-0.8/cdemu_mod.c: In function ‘cdemu_exit’:
/home/mrnatewood/cdemu-0.8/cdemu_mod.c:198: error: too many arguments to function ‘invalidate_bdev’
make[2]: *** [/home/mrnatewood/cdemu-0.8/cdemu_mod.o] Error 1
make[1]: *** [_module_/home/mrnatewood/cdemu-0.8] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2

```
If I try to continue as if nothing happened this is the outcome:
```
mrnatewood@shimi:~/cdemu-0.8$ sudo make install
**** Installing files ****
install -D -m 644 cdemu.ko /lib/modules/2.6.22-14-generic/misc/cdemu.ko
install -D -m 644 libcdemu.py /usr/lib/python2.5/site-packages/libcdemu.py
install -D -m 755 cdemu /usr/bin/cdemu
install -D -m 755 create_cdemu_devs.sh /usr/bin/create_cdemu_devs.sh
sh create_cdemu_devs.sh
You have udev, nodes will be created automagically
mrnatewood@shimi:~/cdemu-0.8$ sudo modprobe cdemu
FATAL: Error inserting cdemu (/lib/modules/2.6.22-14-generic/misc/cdemu.ko): Invalid module format

```

Can anyone help me properly install cdemu?

---

### Post by ajmorris on 2007-11-24
i dont know what sort of source you got there, but, usually, before make, you need './configure'

So, since you're doing the make as root, do: ```
sudo ./configure
```

and then do sudo make

---

### Post by MrNatewood on 2007-11-24
There isn't a file named configure in the extracted directory.
Any other ideas?

---

### Post by ajmorris on 2007-11-24
hmm, strange, are those kernel headers the same version as the current kernel?

---

### Post by almostlinux on 2007-12-13
See this:
[http://ubuntuforums.org/showthread.php?t=69530&page=2](http://ubuntuforums.org/showthread.php?t=69530&page=2)

---

