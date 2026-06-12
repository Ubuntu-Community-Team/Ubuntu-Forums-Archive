---
title: "[SOLVED] dependency problems/ broken cache"
date: 2007-09-08
forum: General Help
---

### Post by adasilva on 2007-09-08
Hello, I am using ubuntu feisty, and trying to install my lexmark z611 printer.  I downloaded a driver, and unpacked it, i now have two .deb files that I would like to install.  The first, z600llpddk_2.0-2_i386.deb installed fine, but the second is giving me some problems: z600cups_1.02_i386.deb.

When i try to do sudo dpkg -i z600cups_1.02_i386.deb or when I try to install it from the file browser by double clicking, i get the following error,
> dpkg:  dependency problems prevent configuration of z600cups:
z600cups depends on libcupsys2-gnutls10 (>=1.1.20final-1); however:
Package libcupsys2-gnutls10 is not installed.

I checked synaptic package manager, and the file libcupsys2 IS installed, and I also found through a google search that the libcupsys2-gnutls10 is a "virtual package"
(see [http://packages.ubuntu.com/edgy/virtual/libcupsys2-gnutls10](http://packages.ubuntu.com/edgy/virtual/libcupsys2-gnutls10))
which, to my understanding, means that if i have the libcupsys2 package installed, then i shouldn't get dependency problems... but maybe I am understanding wrong.

I also tried sudo apt-get install -f, which removes the z600cups package without error.
After I try to install the package, if i type sudo dpkg --configure -a, i get the following:
> z600cups depends on libcupsys2-gnutls10 (>= 1.1.20final-1); however:
  Package libcupsys2-gnutls10 is not installed.
dpkg: error processing z600cups (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 z600cups

does any one have any other ideas/suggestions?

---

### Post by adasilva on 2007-11-06
I ended up getting this to work, although I'm not really sure how. Since this first post, I have updated from Feisty to Gutsy; so maybe this has solved these dependency issues. Also, I don't think I was using "alien" before. Anyway, what I did most recently was this:

Went to the folder that the driver files were in
(two .rpm files: z600cups and z600llpddk)

Used Alien to convert the .rpm files to the proper format:
```
sudo alien -k file.rpm
```
(for both the z600cups file AND the z600llpddk file)

Installed the converted packages:
```
sudo dpkg -i file.deb
```
(again, for both the files).

After restarting, the printer driver appeared with the others in the printing menu
(system>administration>printing> ...etc). After clicking through the graphical setup, I was able to print! yay!

Thanks to: [http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/]("http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/")
 for instruction on using alien and installing the files.

---

