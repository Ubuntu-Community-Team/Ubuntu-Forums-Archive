---
title: "cannot depackage .deb files"
date: 2008-02-06
forum: General Help
---

### Post by lhardyl on 2008-02-06
OK, so yesterday i could run .deb files strait from desktop and through the gui menu doofah, but now i cannot. I can run them through terminal still hpowever. The exact file im trying to run is

pcsx2_0.9.4-1~getdeb1_amd64.deb

and the error i get when i try to run it is

```
"pcsx2_0.9.4-1~getdeb1_amd64.deb" cannot be opened
No application suitable for automatic installation
is available for handling this kind of file
```

What I would like to know is have i inadvertently removed a package required to run .deb files and how i fix it lol

Any help is appreciated

---

### Post by taurus on 2008-02-06
I suppose you are running x86_64 version of Gutsy?

---

### Post by lhardyl on 2008-02-06
oh sorry yea i am

---

### Post by taurus on 2008-02-06
Did you run like this to install it from a terminal?

```
sudo dpkg -i "pcsx2_0.9.4-1~getdeb1_amd64.deb"
```

---

### Post by lhardyl on 2008-02-06
run in terminal i get this

```
lhardyl@lhardyl-desktop:~/Documents$ sudo dpkg -i "pcsx2_0.9.4-1~getdeb1_amd64.deb"
[sudo] password for lhardyl:
(Reading database ... 92382 files and directories currently installed.)
Preparing to replace pcsx2 0.9.4-1~getdeb1 (using pcsx2_0.9.4-1~getdeb1_amd64.deb) ...
Unpacking replacement pcsx2 ...
dpkg: dependency problems prevent configuration of pcsx2:
 pcsx2 depends on nvidia-cg-toolkit; however:
  Package nvidia-cg-toolkit is not configured yet.
dpkg: error processing pcsx2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 pcsx2

```

running

```
sudo apt-get install nvidia-cg-toolkit

```

i get

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-cg-toolkit is already the newest version.
The following packages were automatically installed and are no longer required:
  libgtk1.2 libglib1.2 libfltk1.1 libgtk1.2-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up nvidia-cg-toolkit (1.5.0.0019-1) ...
Downloading NVIDIA Cg Toolkit to /tmp/cg.1202342408.528741/Cg-1.5_Feb2007_x86_64.tar.gz

```

and then the terminal stops working and it doesn't let me enter any commands.

---

### Post by lhardyl on 2008-02-06
ok i managed to depackage it through terminal, i just had to leave it running for about 20 mins.

But i still cant just simply double click on a .deb icon and get it to install automatically for me

---

