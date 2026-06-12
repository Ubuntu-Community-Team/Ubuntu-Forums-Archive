---
title: "Problem with gcc compiler"
date: 2015-12-03
forum: General Help
---

### Post by max-holz on 2015-12-03
Hi
I have Ubuntu 14.04 with gcc 4.8.4, now I need to switch to 4.9.0 or higher cos the program I use to compile (MAME) no longer supports older gcc versions.
How can I do this task?

---

### Post by coldraven on 2015-12-03
Sorry but I'm not a gcc expert. I just checked in Synaptic and in Ubuntu 15.10 at least I have gcc 4.5 and gcc 5 already installed by default. If you want the Synaptic package manager do this:
```
sudo apt-get install synaptic
```

or I suppose you could install gcc 5 directly by doing this:
```
sudo apt-get install gcc-5-base
```

For how you call the later version you will have to search for an answer :(

---

### Post by T.J. on 2015-12-03
Well, if you absolutely **must** use an untested compiler, you will have 4 options:

1. Build it yourself, and install it in /usr/local/.  I've done this before and it is not a task to be undertaken lightly.  You may have to rebuild the entire toolchain: binutils, etc from scratch.  If you do not do this properly, you can render your entire system inoperable.  Assuming you do install it correctly, you will need to set a different environment in order to use it.

2.  Install a chroot, LXC or debootstrap with an updated version of GCC. This can work well.

3.  Use a full virtualization like KVM.  I recommend this over the others because you have no chance of "hosing" your system, and you don't have to change the way you do things if you are comfortable with an LTS like 14.04.

4. Switch to a different Linux, like Debian. Debian, Ubuntu's parent Linux, is far more stable.  Debian Stable uses 4.9.2.  I do not recommend using Ubuntu 15.x - neither are noted for stability.  They are bleeding edge, and GCC 5.x still has a number of notable bugs.

---

### Post by steeldriver on 2015-12-03
I may be out of line here, but I think that probably the easiest way to get gcc-4.9 (or gcc-5) on 14.04 is going to be via the toolchain-r PPA:

[https://launchpad.net/~ubuntu-toolchain-r/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-toolchain-r/+archive/ubuntu/ppa)

I don't recall whether it makes itself the default version - if not, you will likely need to invoke it explicitly as 'gcc-4.9' rather than plain 'gcc' (or make use of the update-alternatives mechanism to allow you to switch back and forth).

---

### Post by taufique2 on 2015-12-07
My c++ code was used to compiled with g++4.6 or older. Now I recently installed ubuntu 15.10 and it came with g++4.7-5. Now latest g++ could not compile the code and show error. Older g++ was not available in the repository. How can I install older g++ (4.6 or 4.3)? Please reply in details as I am novice in Ubuntu. Thank you

---

### Post by T.J. on 2015-12-07
@taufique2
It's a bit off topic from the original post and should be a different thread for a different problem, but have you checked what C++ standard you were previously compiling under?  Older C++ code is not compatible with the new C11 and C14 standards.  You can specify which ISO standard to use with the "std" flag.  Which standards it supports depends on the version of the compiler.  C++ has no less than 5 ISO standards dated 1998, 2003, 2007, 2011 and 2014 respectively.  If it is really old code, I would try the std=c++98 or std=c++03.  More info here: [https://gcc.gnu.org/onlinedocs/](https://gcc.gnu.org/onlinedocs/)

---

