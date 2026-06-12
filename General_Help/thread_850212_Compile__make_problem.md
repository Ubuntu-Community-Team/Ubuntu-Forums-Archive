---
title: "Compile / make problem ?"
date: 2008-07-05
forum: General Help
---

### Post by ixlam on 2008-07-05
Im istalling Wired (audio) from source on Ubuntu 8.04 with all updates and dependencies installed.

The instructions for Wired say to run 

./automeke.sh
./configure
make
make install

All goes well up to when I run "make" when I get this error

```
make: *** No rule to make target `all-recursive', needed by `all'.  Stop.
```
Any help is much appreciated thanx.

---

### Post by s3a on 2008-07-06
I think you need to go to terminal and type:

1) sudo apt-get build essential
2) cd ~/Desktop/temp

for #2, I'm assuming you have what you want to compile in a folder called "temp" on your desktop.

I am not 100% sure if these are the perfect instructions but try them out.

Hope that helps!

---

### Post by ixlam on 2008-07-06
Hey thanks but I do have the build-essential packages installed already.
I think it's an issue with the make file or simmilar, although I could be wrong!? 

Anyone else have any ideas?

(I dont know why Wired is not part of Ubuntu Studio any more, it used to be)

---

