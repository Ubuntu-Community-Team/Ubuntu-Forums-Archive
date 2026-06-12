---
title: "Error : running Matlab 2009b on Ubuntu 12.04"
date: 2012-12-10
forum: General Help
---

### Post by loremaster on 2012-12-10
i have this message whenever i try to run matlab 2009b

/home/ruihong/usr/local/matlabR2009b/bin/util/oscheck.sh: /lib64/libc.so.6: not found

but matlab is able to run properly now i am trying to get rid of this message by making a link.

i tried locating the libc.so

ruihong@ruihong-K45VM:~$ locate libc.so
/lib/libc.so.6
/lib/x86_64-linux-gnu/libc.so.6
/lib32/libc.so.6
/lib64/libc.so.6
/usr/lib/x86_64-linux-gnu/libc.so
/usr/lib32/libc.so

so how should i go about creating a soft link as i am new to ubuntu, i do not know which and how i should start by looking at which file too.

help appreciated!

---

