---
title: "installing things"
date: 2006-11-13
forum: General Help
---

### Post by numbers1thru9 on 2006-11-13
i know how to install things but what is the command i would use with apt-get to search for the correct name of a package?

---

### Post by taurus on 2006-11-13
```
sudo apt-get search <package name>
```
Otherwise, use synaptic...

---

### Post by numbers1thru9 on 2006-11-13
yea i figured that out right after i posted the thread. Thansk thought :) I cant really use synaptic becasue im running ubuntu server. Also im trying to build a program. it requires a version of shout > 2.0 but my problem is that i have libshout3 installed and i get the following error

> checking for shout >= 2.0... Package shout was not found in the pkg-config search path. Perhaps you should add the directory containing `shout.pc' to the PKG_CONFIG_PATH environment variable No package 'shout' found
configure: error: Library requirements (shout >= 2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

does anyone know where apt-get installs libshout or where i can find this/

---

### Post by earobinson on 2006-11-13
if you have it installed try ```
which libshout
``` this should give you its location

---

### Post by numbers1thru9 on 2006-11-13
i got nothing after i tried that command. if i type 

> sudo apt-get install libshout3

it says that libshout3 is already the latest version. i guess thats why im confused lmao

---

### Post by Ramses de Norre on 2006-11-13
This should reveal the file's location if it's there:```
sudo updatedb && locate shout.pc
```
The updatedb can take a while and you can skip it if you've done it recently.

---

### Post by numbers1thru9 on 2006-11-13
shout.pc cant be found but if i run locate shout this is what i get

> /usr/lib/libshout.so.3
/usr/lib/libshout.so.3.2.0
/usr/share/doc/libshout3
/usr/share/doc/libshout3/buildinfo.gz
/usr/share/doc/libshout3/changelog.Debian.gz
/usr/share/doc/libshout3/copyright
/usr/share/doc/libshout3/NEWS.gz
/usr/share/doc/libshout3/README
/var/cache/apt/archives/libshout3_2.2-2_i386.deb
/var/lib/dpkg/info/libshout3.list
/var/lib/dpkg/info/libshout3.md5sums
/var/lib/dpkg/info/libshout3.postinst
/var/lib/dpkg/info/libshout3.postrm
/var/lib/dpkg/info/libshout3.shlibs

im just confused....

---

### Post by numbers1thru9 on 2006-11-13
also where can i set the PKG_CONFIG_PATH variable/ i know where the PATH variable is but not that one

---

### Post by Ramses de Norre on 2006-11-13
Wild guess:
```
sudo aptitude install libshout-dev libshout3-dev
```

---

### Post by numbers1thru9 on 2006-11-13
that worked. it ran hte ./configure just fine. thanks alot!!! 8)

---

### Post by Ramses de Norre on 2006-11-13
It's often useful to install the -dev packages if ./configure complains ;)

---

