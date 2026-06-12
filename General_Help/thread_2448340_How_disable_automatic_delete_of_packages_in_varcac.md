---
title: "How disable automatic delete of packages in var/cache/apt/archives ?"
date: 2020-08-06
forum: General Help
---

### Post by aug7744 on 2020-08-06
I have installed 2 text editor was more of 400 MB downloaded and after all content in var/cache/apt/archives was deleted.
 I wait avoid download again if reinstalling the system or installing in others computers.
 What command I need to disable that strange feature ? Unhappily Linux not has an mode to be more user friendly how windows does and is how Linux not care about it thus is hard for windows users switch of system.
 I had tried to use some text editor and the configuration is in text files instead gui, but wait are simple text editor !
 That is madness or love commnds at extreme. Linux is fast and etc. Have all for be the OS for any user, but unhappily ... 
In windows that feature will have an GUi option to avoid delete cache, but in Linux not have one GUI to help the user and is allways commands that after need figure pre commands to allow run.
 Much time to figure one detail that can be simple :(
  Thanks for any help.

---

### Post by Impavidus on 2020-08-06
400MB for two text editors? When I try to install gedit, synaptic informs me that that's a 1MB download. Kate would be 35MB, as Xubuntu has limited overlap with kate. The package manager will tell you the size of the download before you start, so you can abort if you wish.

What tool did you use to install them? I know that apt will by default remove the packages from cache, but I just verified that apt-get and synaptic don't. Both options seem reasonable. You're very unlikely to ever need those package files again, but at the same time, hard drive space is cheap.

I don't know about Windows; I don't use it. Linux is made for Linux users, not for Windows users, and I think that most Linux users find it quite user friendly. Which is of course entirely subjective.

---

### Post by ActionParsnip on 2020-08-06
You can make apt NOT keep packages with
```

sudo apt-get autoclean

```

Does that look familiar? I don't know how to undo this

This may help:
[https://linux.die.net/man/8/apt-get](https://linux.die.net/man/8/apt-get)

Seems to be the setting:
```

APT::Clean-Installed

```

---

### Post by VMC on 2020-08-06
Use **apt-get **instead of **apt**, then they will stay.

Also ```
sudo apt-get install --download-only <program>
``` Will download only,then you install.

---

### Post by ajgreeny on 2020-08-06
I'm sure there may be other ways to ensure all packages in cache are retained but maybe the easiest way is to use synaptic, which you'll have to install first, and in the Settings ->Preferences ->Files tab there is an option to choose whichever way you prefer to deal with all those files.

See screenshot

---

### Post by aug7744 on 2020-08-13
The command to keep files is
sudo apt install -d
Thanks very much :)

---

