---
title: "Can't run Google Earth - Error : No such file or directory"
date: 2015-01-31
forum: General Help
---

### Post by iamcreasy2 on 2015-01-31
Hello, I am trying to run Google Earth using **googleearth-bin** file. The installation was on default directory, /opt/google-earth

The permission of the file is as follows,
```
[COLOR=#262626][FONT=arial]-rwxr-xr-x 1 root root 5452 Jan 31 00:41 googleearth-bin[/FONT][/COLOR]
```

The installation was fine, but when I am trying to run the file using** ./googleearth-bin **I get the following error,
```
bash: ./googleearth-bin: No such file or directory
```

And when I try using sudo I get the following error,
```
sudo: unable to execute ./googleearth-bin: No such file or directory
```

Why I can't run the file **googleearth-bin ?**

---

### Post by Impavidus on 2015-01-31
1: Are you in the right directory?

2: Google Earth gives you a symbolic link named /usr/bin/google-earth. This one (or simply the command **google-earth**, as it is in your PATH) will start Google Earth. The symbolic link points to a shell script that in turn calls googleearth-bin. The first lines of the shell script read:```
#!/bin/sh
# Always run Google Earth from this shell script and not
# Google Earth directly! This script makes sure the app looks
# in the right place for libraries that might also be installed
# elsewhere on your system.
```

And I wouldn't run Google Earth with sudo. At the very least it will create a mess, but it may give security problems too.

---

### Post by iamcreasy2 on 2015-01-31
> **Impavidus said:**
> 1: Are you in the right directory?

Yes, I guess I am in the correct director. The following code shows it, doesn't it?

```
irfan@XXX:/opt/google-earth$ ls -l googleearth-bin
-rwxr-xr-x 1 root root 5452 Jan 31 00:41 googleearth-bin
irfan@XXX:/opt/google-earth$ ./googleearth-bin
bash: ./googleearth-bin: No such file or directory

```

There is no symbolic link(google-earth) under /usr/bin. I saw similar error that I am seeing right now while the installation was done and tried to run google earth.

Can you point me to the shell script?

---

### Post by Impavidus on 2015-01-31
On my system that shell script is in /opt/google/earth/free/googleearth, which is the same directory as where I find googleearth-bin. It seems they changed the directory structure of Google Earth and that I have a different version from yours.

But not starting GE from the shell script should give a different error:```
$ ./googleearth-bin 
./googleearth-bin: error while loading shared libraries: libgoogleearth_free.so: cannot open shared object file: No such file or directory

```It should find the file, but fail to run it. Not having permission to run it would give yet another error message (permission denied). So it seems that indeed bash is unable to find googleearth-bin, despite the fact that ls shows it's there.

---

### Post by scouser73 on 2015-02-01
Follow the instructions here to install Google Earth. [http://www.webupd8.org/2014/04/install-google-earth-in-ubuntu-1404.html]("http://www.webupd8.org/2014/04/install-google-earth-in-ubuntu-1404.html")

---

