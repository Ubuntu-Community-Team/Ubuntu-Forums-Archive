---
title: "export PKG_CONFIG_PATH doesn't subsist after closing the terminal"
date: 2019-12-08
forum: General Help
---

### Post by coyoteazul on 2019-12-08
Hi. I'm trying to compile glib from source, and it requires libffi.
I've already compiled libffi from source too, but pkg-config can't find it on my custom path.

I tried exporting PKG_CONFIG_PATH, but afer i close the terminal and echo PKG_CONFIG PATH it returns blank.
I also tried to set the path and run meson build on the same terminal, but it still can't find libffi.

So i'm running
```
hernanr@hernanr-note:~$ echo $PKG_CONFIG_PATH

hernanr@hernanr-note:~$ export PKG_CONFIG_PATH=/home/hernanr/Documents/3rd_party_libs/lib-libffi/linux-build/lib/pkgconfig
hernanr@hernanr-note:~$ echo $PKG_CONFIG_PATH
/home/hernanr/Documents/3rd_party_libs/lib-libffi/linux-build/lib/pkgconfig

```

After i close the terminal, echo returns empty again.
Exporting as root (sudo -i) does exactly the same. What am i doing wrong?

I'd like to avoid installing libffi through apt-get because i plan to cross compile my program and i'd like to keep all dependencies close

---

### Post by Impavidus on 2019-12-08
When you use export, the variable is defined in the shell and will be passed on as an environment variable to child processes started after that. But it's not permanently saved, so when you terminate the shell, it's gone. That's normal. To make the environment variable permanent, define it in your .bashrc. It will be loaded automatically in every new shell.

---

### Post by norobro on 2019-12-08
As @Impavidus says the export command is not persistent.

Why are you closing the terminal? Just issue the export command from the root directory of glib and proceed with configuring and compiling.

---

### Post by coyoteazul on 2019-12-08
ahh, so that's why. I thought it was a permanent method to define enviromental variables, like window's setx.
I checked .bashrc and strangely pkg_config_path doesn't even exist. Even more strangely i don't even have a path variable, but i guess that's a separate problem.

There's no configure file on glib. According to the documentation mason _build is supposed to deal with that, but exporting pkg_config_path and running mason _build on the same terminal didn't work. Mason still tells that it can't find libffi.

In the end I solved this by making a symbolic link of my .pc files on a folder that pkg-config checks by default.

---

### Post by Impavidus on 2019-12-09
Evidently PKG_CONFIG_PATH didn't exist. That's why your echo command returned an empty line. It doesn't exist by default. And I'm quite sure you've got a PATH variable. There's more than one place where it can be set. On normal Ubuntu systems, PATH is defined in /etc/environment, but it can be modified in placed like /etc/profile, /etc/bash.bashrc, $HOME/.profile and $HOME/.bashrc.

---

