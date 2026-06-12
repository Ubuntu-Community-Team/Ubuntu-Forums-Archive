---
title: "Nvidia Installation Problem"
date: 2006-11-01
forum: General Help
---

### Post by aknapp on 2006-11-01
I have done the following:

> sudo apt-get install nvidia-glx nvidia-kernel-common

> sudo nvidia-glx-config enable

and replaced nv with nvidia in the xorg.conf file.
When I restart x I get:

> Error: API mismatch: the NVIDIA kernel module is version 1.0.xxxx, but this X module is version 1.0.xxxx. Please be sure that your kernel module and all NVIDIA driver files have the same driver version.

So I tried installing the driver from the NVIDIA website. It fails to install, says it could not build a kernel. Here is the log:

[http://paste.ubuntu-nl.org/29685/](http://paste.ubuntu-nl.org/29685/)

Help, please! ](*,)

---

### Post by cotcot on 2006-11-01
I am not sure if I understand it well. You have nvidia compiled in the kernel as a module and afterwards you have installed another nvidia driver which is obviously a different one. If so you will have to eliminate one of them.

---

### Post by aknapp on 2006-11-01
How do I do this? I have tried /usr/bin/nvidia-installer --uninstall, it said  something about unable to access some file and then said uinstall complete. I have tried removing nvidia-glx and reinstalling that too.

---

### Post by Jimmy_r on 2006-11-01
First check if your system is up to date:
sudo apt-get update
sudo apt-get upgrade

If that does not help, read on.

I dont know for sure, but the problem might come from the
```
sudo nvidia-glx-config enable
```
command.

I use ```
sudo nvidia-xconfig
```

My suggestion is for you to first to try to undo what the nvidia-glx-config command has done. If you just have installed ubuntu it might be easier to just reinstall it.
Then install nvidia-glx (if you reinstalled)
and do a sudo nvidia-xconfig

If you want to repair the damage instead, i suppose you could try to use the backup of xorg.conf that nvidia-glx-config has done, to replace the current one.

Edit: also look here [http://www.ubuntuforums.org/showthread.php?p=1693112#post1693112](http://www.ubuntuforums.org/showthread.php?p=1693112#post1693112) Looks like the same problem.

---

