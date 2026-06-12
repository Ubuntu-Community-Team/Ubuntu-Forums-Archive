---
title: "Error while loading shared libraries: libpng12.so.0: wrong ELF class: ELFCLASS64"
date: 2022-12-29
forum: General Help
---

### Post by asb87 on 2022-12-29
I am trying to run Quartus 13 on Ubuntu 22.04 (64-bit) and like many other people the libpng12.so.0 is not allowing it to run. First it could not the file. Then I downloaded and installed the package using ```
apt-get install libpng16-16:i386
``` then placed the file manually in the Quartus installation folder so the error changed to:

 > quartus: error while loading shared libraries: libpng12.so.0: wrong ELF class: ELFCLASS64 

 The installation folder of Quartus has the path: > /home/developer/n/quartus/bin

 Now I asked this question because many of the solutions worked fine  till Ubuntu 21. I need a fix for Ubuntu 22.04 for a 32-bit libpng12  package (I presume this is why the ELF class error occurs).
 The command find -name libpng12 returns:

 > ./usr/local/lib/libpng12.so.0
./usr/lib/x86_64-linux-gnu/libpng12.so.0
./home/developer/n/libpng/.libs/libpng12.so.0
./root/libpng-1.2.54/.libs/libpng12.so.0
find: ‘./run/user/1000/doc’: Permission denied
find: ‘./run/user/1000/gvfs’: Permission denied
./snap/core/14399/lib/x86_64-linux-gnu/libpng12.so.0
./snap/core/14399/usr/lib/x86_64-linux-gnu/libpng12.so.0
 
I copied all of them one by one to /quartus/bin and every time I got the same ELFCLASS error.

 I also tried putting the path of libpng12 in d.so.conf file in /etc then ran ```
ldconfig 
```but still the same problem. I have tried these answers:

 [https://askubuntu.com/questions/1404213/install-libpng12-on-ubuntu-22-04](https://askubuntu.com/questions/1404213/install-libpng12-on-ubuntu-22-04)
 [https://bbs.archlinux.org/viewtopic.php?id=212077](https://bbs.archlinux.org/viewtopic.php?id=212077)
 [https://community.intel.com/t5/Programmable-Devices/Quartus-can-t-find-shared-library/td-p/161251](https://community.intel.com/t5/Programmable-Devices/Quartus-can-t-find-shared-library/td-p/161251)
 [URL="https://askubuntu.com/questions/895897/error-while-loading-shared-libraries-libpng12-so-0"]https://askubuntu.com/questions/895897/error-while-loading-shared-libraries-libpng12-so-0
[/URL]
 This no longer works: ```
sudo apt-get install libpng12-0:i386


``` 

This package isnt available any more: [https://packages.ubuntu.com/xenial/i386/libpng12-0/download](https://packages.ubuntu.com/xenial/i386/libpng12-0/download)

 How do I get my software to run?

---

### Post by asb87 on 2023-01-02
This works flawlessly on 64-bit Ubuntu 22.04:


 sudo apt-get install libpng12-0



 This installs the 64-bit libpng12 version needed by Quartus 13. Go to /bin folder of your Quartus installation. My path was this:


 /root/altera/13.0sp1/quartus/bin



 Then run this:


 ./quartus --64bit

---

