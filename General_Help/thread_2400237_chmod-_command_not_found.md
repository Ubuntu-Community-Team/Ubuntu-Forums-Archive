---
title: "chmod- command not found"
date: 2018-09-04
forum: General Help
---

### Post by docea37 on 2018-09-04
hello ubuntu 16.04 I'm using 64bit


```
chmod 775 -R test && opkg-build test
The command 'chmod' was not found, so you mean mu:
  The 'coreutils' command from the 'chmod' package (main)
chmod: command not found

```


```
sudo apt-get update 
sudo apt-get upgrade
```
```

sudo apt-get install chmod
[sudo] password for docea37:
Reading package lists ... Done
Dependency tree is being created
Read status information ... Done
E: chmod package not found

```

solution


```
/bin/ chmod 775 -R test && opkg-build test



```

-------------------


Is there a way to get it working this way?


```
chmod 775 -R test && opkg-build test

```

---

### Post by Holger_Gehrke on 2018-09-04
> **docea37 said:**
> 
```
chmod 775 -R test && opkg-build test
The command 'chmod' was not found, so you mean mu:
  The 'coreutils' command from the 'chmod' package (main)
chmod: command not found

```


Did you type this from memory instead of using copy and paste ? Because it should be the other way around - the 'chmod' command from the 'coreutils' package. coreutils is a **very** basic part of an Ubuntu system. f it wasn't installed you'd be in serious trouble ...

If '/bin/chmod' works and 'chmod' doesn't, there's something wrong with your PATH. This environment variable contains a colon-separated list of all directories to search for executables. Normally '/bin' is in there. Did you edit your '~/.profile' or '~/.bashrc' to change the PATH ?

Holger

---

