---
title: "Intall libjansson"
date: 2017-12-29
forum: General Help
---

### Post by gman01 on 2017-12-29
Hi,

I am fairly new to Ubuntu. I have installed Ubuntu 15.10 64bit. 

I am trying to run a programme and get the error:

 error while loading shared libraries: libjansson.so.4: cannot open shared object file: No such file or directory

I tried 


sudo apt-get install libjansson-dev

I get these errors:


E: Failed to fetch [http://ubuntu.mirrors.ovh.net/ftp.ubuntu.com/ubuntu/pool/main/j/jansson/libjansson4_2.7-1ubuntu1_amd64.deb](http://ubuntu.mirrors.ovh.net/ftp.ubuntu.com/ubuntu/pool/main/j/jansson/libjansson4_2.7-1ubuntu1_amd64.deb)  404  Not Found [IP: 2001:41d0:202:100:213:32:5:7 80]


E: Failed to fetch [http://ubuntu.mirrors.ovh.net/ftp.ubuntu.com/ubuntu/pool/main/j/jansson/libjansson-dev_2.7-1ubuntu1_amd64.deb](http://ubuntu.mirrors.ovh.net/ftp.ubuntu.com/ubuntu/pool/main/j/jansson/libjansson-dev_2.7-1ubuntu1_amd64.deb)  404  Not Found [IP: 2001:41d0:202:100:213:32:5:7 80]


E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


Tried to locate if it is already installed the only thing i can see are:

/lib/x86_64-linux-gnu/libjson-c.so.2
/lib/x86_64-linux-gnu/libjson-c.so.2.0.0

Followed documentation to remove it if it is installed but it says it is not installed.

Any help would be appreciated. 

Thanks

---

### Post by #&amp;thj^% on 2017-12-29
If you really installed 15.10 that would explain why you can't download anything.
15.10 has reached EOL no more support.
16.04 is a LTS 5 year support.
17.04 will end in January 2018 
17.10 will end in July 2018 
Most newer users and Old Timers here prefer the LTS releases.

---

