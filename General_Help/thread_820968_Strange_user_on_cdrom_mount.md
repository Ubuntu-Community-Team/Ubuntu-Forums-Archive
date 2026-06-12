---
title: "Strange user on cdrom mount"
date: 2008-06-06
forum: General Help
---

### Post by drpaul on 2008-06-06
I have discovered this problem while trying to install Photoshop Elements in Wine.

When my CDROM is mounted this is what the file system shows

:/cdrom$ ls -l
total 7262
dr-xr-xr-x 1 root root    2048 2006-02-22 09:14  adobe photoshop elements
dr-xr-xr-x 1 root root    2048 2006-03-22 08:29 adobe photoshop elements
dr-xr-xr-x 1 root root    2048 2006-02-22 09:14  adobe reader 70
dr-xr-xr-x 1 root root    2048 2006-03-22 08:29 adobe reader 70
dr-xr-xr-x 1 root root    4096 2006-03-22 08:30 autoplay
-rwx------ 1  501  501      49 2004-06-17 06:36 autorun.inf
dr-xr-xr-x 1 root root    2048 2006-02-22 09:14  customer support
-rwx------ 1  501  501  126976 2004-08-11 07:09 epic_eula.dll
-rwxr-xr-x 1  501  501    6250 2006-01-26 16:42  how to install.css
-rwx------ 1  501  501    6250 2005-07-22 02:59 how to install.css
-rwxr-xr-x 1  501  501    5178 2006-01-26 16:48  how to install.html
-rwx------ 1  501  501    4377 2005-07-22 03:02 how to install.html
-rwxr-xr-x 1  501  501       0 2006-03-23 08:22 install adobe photoshop el.pkg
-rwx------ 1  501  501   52492 2005-08-29 20:42 photoshop elements 40 rea.html
-rwxr-xr-x 1  501  501    6779 2006-01-30 15:31 photoshop elements read m.html
-rwxr-xr-x 1  501  501 1167770 2006-02-16 19:46  product highlights.pdf
-rwx------ 1  501  501 5417299 2005-08-18 20:45 product highlights.pdf
-rwx------ 1  501  501  143787 2005-11-04 11:16 pse_cdfinder4.png
-rwx------ 1  501  501  159744 2004-08-03 07:34 setup.exe
-rwx------ 1  501  501     625 2004-03-01 23:43 setupexe.manifest
-rwx------ 1  501  501  245408 2003-04-21 11:39 unicows.dll
-rw-r--r-- 1  501  501   74763 2006-03-22 11:12 volumeicon.icns

Note that many of the entries have a user/group of 501. This doesn't correspond to anything in my user or group file. When I try to execute the setup.exe under wine, it can't find the file.

Does anyone know how to fix this? Since the file system is RO I can't chown anything [I tried].

TIA

Paul

---

### Post by dsegura on 2009-06-13
Hi,

I had the same problem and to remove it I had the 'norock' option for the cdrom in /etc/fstab
like this:

...
/dev/scd0       /media/cdrom0   udf,iso9660 user,norock,noauto,exec,utf8 0       0
...

---

### Post by akakingess on 2009-06-13
501 just means read-only, I believe 666 or 777 is for total read/write/x access.

akakingess

---

