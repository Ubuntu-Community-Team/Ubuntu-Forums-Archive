---
title: "[SOLVED] Error when running synaptic"
date: 2007-08-01
forum: General Help
---

### Post by banjopikker on 2007-08-01
This is the error message I get when I try to update . I am lost on what to do next. Thanks



E: /var/cache/apt/archives/debianutils_2.17.4build1_i386.deb: subprocess pre-installation script returned error exit status 1

---

### Post by Seisen on 2007-08-01
Try 
```
sudo apt-get -f install
``` in the terminal.

---

### Post by banjopikker on 2007-08-01
It says
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dpkg not installed  not recorded as installed

I ran sudo aptitude reinstall dpkg and got this
dpkg is not currently installed, so it will not be reinstalled.
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by Seisen on 2007-08-01
Try this in the terminal.
```
cd /var/cache/apt/archives/
sudo dpkg -i --force-install debianutils_2.17.4build1_i386.deb
```

---

### Post by banjopikker on 2007-08-01
This is what returned

dpkg: unknown force/refuse option `install'

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

---

### Post by Seisen on 2007-08-01
Try this

```
sudo dpkg -i --force -all debianutils_2.17.4build1_i386.deb
```

---

### Post by banjopikker on 2007-08-01
I still get this

dpkg: unknown force/refuse option `-all'

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

---

### Post by banjopikker on 2007-08-01
It looks like that the dpkg is not in system. where would it reinstall it from?

---

### Post by banjopikker on 2007-08-01
I tried this....

apt-get source dpkg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 4998kB of source archives.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main dpkg 1.13.24ubuntu6 (dsc) [918B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main dpkg 1.13.24ubuntu6 (tar) [4997kB]
Fetched 4998kB in 29s (170kB/s)                                                
sh: dpkg-source: not found
Unpack command 'dpkg-source -x dpkg_1.13.24ubuntu6.dsc' failed.
Check if the 'dpkg-dev' package is installed.
E: Child process failed

---

### Post by banjopikker on 2007-08-01
I found the problem . It was dpkg_dev not installed.  whew.

---

