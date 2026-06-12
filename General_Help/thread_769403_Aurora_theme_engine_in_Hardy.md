---
title: "Aurora theme engine in Hardy?"
date: 2008-04-26
forum: General Help
---

### Post by rainwalker on 2008-04-26
I LOVE the Aurora theme engine, but it's never included with Ubuntu (I'm guessing it's not open-source). In the past I could always find a .deb and be totally set, but I just installed Hardy and I can't find a .deb anywhere. The package on Gnome-look is source code that I have to compile, which I would be fine with, except that I get this:
> riley@riley-laptop:~/Desktop/aurora-1.4$ ./configure --enable-animations
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
It's long, but this is what that config.log file says: [http://paste.ubuntu-nl.org/64579/](http://paste.ubuntu-nl.org/64579/)

Can anyone help?

---

### Post by ShodanjoDM on 2008-04-26
I got the deb package for Ubuntu 7.10 from [here]("http://download.opensuse.org/repositories/home:/discotronic/xUbuntu_7.10/i386/gtk2-engines-aurora_1.4-1nano_i386.deb")

Works in Hardy as well.

---

### Post by Ponty on 2008-08-09
Please can anyone help? I've been trying to get the aurora theme engine working in hardy but i just can't get it working properly. I know that, cos the aurora midnight theme stays the same as the others. Can anyone suggest to what to do?:confused:

---

### Post by rainwalker on 2008-08-09
32-bit: [http://download.opensuse.org/repositories/home:/discotronic/xUbuntu_7.10/i386/gtk2-engines-aurora_1.4-1nano_i386.deb](http://download.opensuse.org/repositories/home:/discotronic/xUbuntu_7.10/i386/gtk2-engines-aurora_1.4-1nano_i386.deb)

And for 64-bit: [http://www.gnome-look.org/content/show.php/Aurora+Ubuntu+7.10+64bit?content=75591](http://www.gnome-look.org/content/show.php/Aurora+Ubuntu+7.10+64bit?content=75591)

---

### Post by xcesarfrancox on 2008-08-09
Try with this:

```
./configure --prefix=/usr --enable-animation
```

EDIT:
Also, do you have the build-essential package??

```
sudo aptitude install build-essential
```

---

