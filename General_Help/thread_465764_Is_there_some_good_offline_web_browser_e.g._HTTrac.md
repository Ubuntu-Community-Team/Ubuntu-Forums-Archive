---
title: "Is there some good offline web browser e.g. HTTrack?"
date: 2007-06-06
forum: General Help
---

### Post by ishaqmalik on 2007-06-06
Hi,

             I need some good offline web browser, but I am not a big fan of HTTrack, it keeps on giving me errors, please suggest some tools...

Regards,
MI

---

### Post by rapolas on 2007-06-06
what errors are you getting?

---

### Post by AZzKikR on 2007-06-06
You can download a whole website using **wget**. Type
```
man wget
```
for more information. Basically if you want to get a whole website for later offline browsing, you could just type
```
wget -r http://www.website.com
```
This will recursively follow all links in the website and tries to download them (to a certain extent at least). The manual page has lots more information on how to use wget - it's a program with a lot of options. I believe there is also a UI written for it, which is all **gwget** if I recall correctly.

---

### Post by Gouz on 2007-10-27
Hey there. I tried out wget but it doesnt work well for what I want it.
And I dont know if the HTTrack works on x64 
I found KrawlSite but I can;t install it

build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.


any ideas or an other off line browser?

---

