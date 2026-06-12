---
title: "cannot install convertall"
date: 2023-10-16
forum: General Help
---

### Post by jgw on 2023-10-16
there used to be a program called convertall.  It could convert just about everything.  I just tried to install it and failed.  It couldn't be found.  I did find its address: [https://convertall.bellz.org/install.html](https://convertall.bellz.org/install.html)  Then it wanted me to python install.py  I tried that one and failed.  I used to simply install it and, now, it seems to have gotten more complex.  I was wondering, does anybody know what happened to it?

Thank you............

---

### Post by MAFoElffen on 2023-10-16
Why????

Delete the code, and tarball.

Then do
```

sudo apt install convertall

```
It's in the Ubuntu Repositories...

---

### Post by jgw on 2023-10-19
Thank you........

My ignorance.  Delete the code, and tarball?  What code and tarball?

I have a folder, at home: "convertall"  and it holds 9 items.  (all told something like 25 items)  which all come from the tarball.  Including:
INSTALL
ConvertAll Installation Notes

Extract the source files from the convertall tar file, then change to the
'ConvertAll' directory in a terminal.  For a basic installation, simply
execute the following command as root:  'python install.py'

To see all install options, use: 'python install.py -h'

To install ConvertAll with a different prefix (the default is
'/usr/local'), use:  'python install.py -p /prefix/path'

I also have an uninstall.py

Before I did it all I tried sudo apt install convertall  which couldn't find it. 

Thoughts?

---

### Post by Holger_Gehrke on 2023-10-19
'convertall' is in the 'universe' part of the repositories. I faintly recall that this is the part of the repositories for software which is not supported / updated or checked for security problems by Canonical and is therefore not active by default in mainline Ubuntu - it is active in most other flavours. Check your /etc/apt/sources.list. If the line for 'universe' starts with a '#' then it's commented out and apt will not find and install software in that pocket. Remove the hash character at the beginning of the line to activate 'universe' and do a 'sudo apt update' to get the list of packages.

Holger

---

### Post by jgw on 2023-10-19
I removed all convertall files and then did as search then sudo apt install convertall:

```
sudo apt search ConvertAll
Sorting... Done
Full Text Search... Done
convertall/jammy,jammy 0.8.0-1 all
  very flexible unit converter

then:

sudo apt install convertall
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libqt5core5a : Depends: libpcre2-16-0 (>= 10.22) but it is not installable
                Recommends: qttranslations5-l10n but it is not going to be installed
 libqt5designer5 : Depends: libqt5gui5 (>= 5.14.1) but it is not installable or
                            libqt5gui5-gles (>= 5.14.1) but it is not installable
 libqt5help5 : Depends: libqt5gui5 (>= 5.0.2) but it is not installable or
                        libqt5gui5-gles (>= 5.0.2) but it is not installable
 libqt5printsupport5 : Depends: libqt5gui5 (>= 5.14.1) but it is not installable or
                                libqt5gui5-gles (>= 5.14.1) but it is not installable
 libqt5widgets5 : Depends: libqt5gui5 (>= 5.15.1) but it is not installable or
                           libqt5gui5-gles (>= 5.15.1) but it is not installable
 python3-pyqt5 : Depends: libqt5gui5 (>= 5.1.0) but it is not installable
                 Depends: libqt5gui5 (>= 5.15.1) but it is not installable or
                          libqt5gui5-gles (>= 5.15.1) but it is not installable
E: Unable to correct problems, you have held broken packages.
greg@greg-System-Product-Name:~$ 
```

Apparently it cannot be installed?

---

