---
title: "repair os install"
date: 2020-01-16
forum: General Help
---

### Post by libbrokenlocale on 2020-01-16
hi, 

I build **gcc 9.2** from source and **installed into /usr/local** in **Ubuntu 19.10**. After that I am no longer able to log in using unity-desktop. After log-in an error message flashes up, too fast to see then it returns to the login screen. I am able to log into gnome desktop, however.

I tried to repair it with the following steps:

```

sudo dpkg -r mygccbuild
sudo rm -rf /usr/local/bin/gcc
sudo rm -rf /usr/local/lib/gcc
```

then reinstalled with 
```
sudo apt install --reinstall gcc
sudo apt install --reinstall ubuntu-unity-desktop
```

after a restart, this resolved apport-gtk from crashing. Everything behaves normal, no errors or buggy behaviour but again, logging into unity is still failing.

any ideas what else I can try? Also I thought I'd be fine installing gcc into /usr/local, why is it interfering with system environment?

---

### Post by libbrokenlocale on 2020-01-16
does unity require a different gcc version?

---

### Post by Impavidus on 2020-01-16
I don't think unity needs any gcc, but I don't have unity and I do have gcc 9.2, so I can't quickly check it with a simulated install or removal. It's possible to install several versions of gcc side by side from the repos, but on 19.10 the default is gcc 9.2 (8.3 and 7.4 are also available), so I doubt there would be any conflict anywhere. Any software that needs a different gcc would be explicit about it. /usr/local is also the right place to install. But I suggest that your own gcc 9.2 is called by a different name then the gcc 9.2 from the repositories, if installed. I assume you compiled it from source because you wanted some tweaks, but it's best if the gcc command refers to the compiler that most people expect.

My guess is that you did something wrong during installation and messed up some files not related to gcc or /usr/local at all. Did you use, during compiling or installation, sudo for anything other than de most basic terminal commands? There may be a permissions issue with a file in your home directory that's vital to unity.

BTW, reinstalling gcc and ubuntu-unity-desktop won't do much. Those are metapackages, only meant to pull in some dependencies like gcc-9.

---

### Post by libbrokenlocale on 2020-01-16
Yes, I had to tweak gcc in order to compile another software I use. I have the original shipped gcc-9 in /usr/bin and my own build in /usr/local/bin. I did not replace any links, /usr/local simply precedes /usr in the PATH so this is the one I use. I am not sure if this conflicts with

> it's best if the gcc command refers to the compiler that most people expect.

I could, for instance, install it to /opt and hide gcc from PATH.

Unfortunately I became aware of the problem only on reboot and I did a bunch of other tasks not related to gcc or /usr/local. For the moment I cannot further trace down the source of the problem. I can try replicate the procedure in a VM to find out. 

When I first installed unity the package size was ~1GB. My reinstall only pulls dependencies as you said. Is there a way to completely reinstall it?

---

### Post by libbrokenlocale on 2020-01-17
it was caused by an older backup from my home directory. I had to delete some folders in ~/.config/. Everything is working fine now.

---

