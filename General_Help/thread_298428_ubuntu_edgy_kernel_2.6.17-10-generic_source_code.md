---
title: "ubuntu edgy kernel 2.6.17-10-generic source code?"
date: 2006-11-12
forum: General Help
---

### Post by redsax on 2006-11-12
Where to download Ubuntu edgy kernel 2.6.17-10-generic
linux-source file?

I got one from 
[http://packages.ubuntulinux.org/edgy/devel/linux-source-2.6.17](http://packages.ubuntulinux.org/edgy/devel/linux-source-2.6.17),

but in its source-directory/kernel-version file, it says
2.6.17-10-generic,
while in its source-directory/include/linux/version.h file,
it says 2.6.17.13-ubuntu1.

I am trying to compile a driver, whose install.sh complains
about this difference and stops, ](*,) ,

Someone could point out where the source file to download
without this problem? Thanks!!!!!!!!!!!!!

---

### Post by pdub on 2006-11-12
You are probably looking for the kernel headers

You can get them like this:

```
sudo apt-get install linux-headers-2.6.17-10-generic
```

Then you will need to create a symbolic link:

```
sudo ln -s /usr/src/linux-headers-2.6.17-10-generic /usr/src/linux
```

You will also need build essential

```
sudo apt-get install build-essential
```

---

### Post by redsax on 2006-11-12
Hi, Thanks for your reply.
I know what you mean here.

I can use headers to recompile the driver,
but I plan to make a patch, which means that
I still need to recompile the kernel using the SOURCE
file? If it's not the right one, matching the kernel
that is running, I will be in trouble? :confused:

---

