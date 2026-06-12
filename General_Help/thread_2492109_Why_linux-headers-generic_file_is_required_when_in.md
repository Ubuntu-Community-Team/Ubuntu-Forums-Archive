---
title: "Why linux-headers-generic file is required when installing kernel update ?"
date: 2023-10-31
forum: General Help
---

### Post by aug7744 on 2023-10-31
Hello.
Here Ubuntu 20.04.6.
When trying an kernel update from Ubuntu Mainline Kernel site some files are downloaded.
For example of kernel 6.5.7
linux-headers-6.5.7-060507_6.5.7-060507.202310102154_all.deb
linux-headers-6.5.7-060507-generic_6.5.7-060507.202310102154_amd64.deb
linux-image-unsigned-6.5.7-060507-generic_6.5.7-060507.202310102154_amd64.deb
linux-modules-6.5.7-060507-generic_6.5.7-060507.202310102154_amd64.deb

Kernel files are installed being possible an OS boot using the new kernel.
However is as dkms not work and some devices drivers installed using dkms not are created with that new kernel update.

Running sudo apt --fix-broken install show the files installed from deb below not are correctly installed and thus linux-headers-generic file need to be removed.
linux-headers-6.5.7-060507-generic_6.5.7-060507.202310102154_amd64.deb

What feature does that file ? Is really required ? Not having installed linux headers generic break any OS component or other softwares ?

Thanks for reading my topic.
Have an nice week.

---

### Post by MAFoElffen on 2023-10-31
Search the Forum on "Doug S" and Linux kernel 6.5.0...

He tests the new kernels as they come in, and I believe he tests them on 20.04... as I remember him giving someone some tips on what he does to make that work for him.

Found it: [https://ubuntuforums.org/showthread.php?t=2490234&p=14155919#post14155919](https://ubuntuforums.org/showthread.php?t=2490234&p=14155919#post14155919)

---

### Post by Doug S on 2023-10-31
You ask some good questions. A few posts further down in that link MAFoElffen supplied I ask/wonder similar.

It seems that things will work fine with the problematic header package uninstalled. [This description]("https://docs.kernel.org/kbuild/headers_install.html") explains a lot, I think. Particularly the bit that says:

> Kernel headers are backwards compatible, but not forwards compatible. This means that a program built against a C library using older kernel headers should run on a newer kernel (although it may not have access to new features), but a program built against newer kernel headers may not work on an older kernel.

Anyway, the bottom line is that you be fine to continue with the problematic header package uninstalled.

---

### Post by MAFoElffen on 2023-10-31
@Doug S --
Your ears were burning weren't they... LOL. 

I was thinking about PM'ing you to see if you could come out and play, but thought you are usually busy...

---

### Post by aug7744 on 2023-11-01
Thanks for all replies.
Perhaps Linux headers are required for compiling some binary drivers or others softwares ? example Nvidia binary driver.
I have downloaded the kernel latest 6.6 and all dependencies are installed.
However not is possible run make.
In correct path of kernel extracted files
sudo cp /boot/config-6.2.16-060216-generic  ./. config
sudo make localmodconfig

not is possible run the command below as if the command line is wrong
sudo make -j4 deb-pkg
show the messages

GEN     debian
error: creating source package requires git repository
make[2]: *** [scripts/Makefile.package:38: check-git] Error 1
make[2]: *** Waiting for unfinished jobs....
warning: Not a git repository. Use --no-index to compare two paths outside a working tree
usage: git diff --no-index [<options>] <path> <path>
make: *** [Makefile:234: __sub-make] Error 2

How fix it ?

---

### Post by Doug S on 2023-11-01
I have some notes on how to compile the mainline kernel [here]("https://askubuntu.com/questions/718381/how-to-compile-and-install-custom-mainline-kernel/718662#718662").
I am running kernel 6.6 that I compiled myself.

---

