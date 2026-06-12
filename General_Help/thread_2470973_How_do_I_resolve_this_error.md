---
title: "How do I resolve this error"
date: 2022-01-18
forum: General Help
---

### Post by cscj01 on 2022-01-18
I am on Ubuntu 20.04.3 x64 using Gnome Flashback for my DE.  I was trying to install a program after a system update and received the following:```
Preparing to unpack .../guile-2.2-libs_2.2.7+1-4_amd64.deb ...
Unpacking guile-2.2-libs:amd64 (2.2.7+1-4) ...
dpkg-deb (subprocess): decompressing archive member: lzma error: compressed data is corrupt
dpkg-deb: error: <decompress> subprocess returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/guile-2.2-libs_2.2.7+1-4_amd64.deb (--unpack):
 cannot copy extracted data for './usr/lib/x86_64-linux-gnu/guile/2.2/ccache/system/vm/disassembler.go' to '/usr/lib/x86_64-linux-gnu/guile/2.2/ccache/system/vm/disassembler.go.dpkg-new': unexpected end of file or stream
Errors were encountered while processing:
 /var/cache/apt/archives/guile-2.2-libs_2.2.7+1-4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```How do I resolve this without breaking something?

---

### Post by Impavidus on 2022-01-18
Somehow the archive file with the package was damaged. Try deleting it:```
sudo rm /var/cache/apt/archives/guile-2.2-libs_2.2.7+1-4_amd64.deb
```(For convenience, use tab completion to type the path. Type 3 letters, hit tab, see what you get, type some more characters. I don't know if you're aware of tab completion. Or just copy it.)

When trying the installation again, apt should redownload the file.

Occasional file corruption can be the result of actions broken off or programs killed. Maybe you killed apt recently. If this file corruption happens often, it's time to worry about your hardware.

---

### Post by cscj01 on 2022-01-19
Thanks.  I guess I did not know (after using Linux for 20 years) that the deb files were archived when a package was installed.  It makes sense, but I had never thought about it until your reply.

---

### Post by ajgreeny on 2022-01-19
However, bear in mind that if you update your system using the command ```
sudo apt update && sudo apt upgrade
``` no packages are saved in the cache or anywhere else as far as I'm aware.

To save all installed packages you have to use ***apt-get*** instead of plain ***apt***.
This is something that I had not realised until I wanted to reinstall a previous version of a package and found the /var/apt/cache was almost empty.

---

