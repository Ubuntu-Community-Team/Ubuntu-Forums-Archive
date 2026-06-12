---
title: "Running 32 bit programs on 64 bit 18.04"
date: 2019-07-21
forum: General Help
---

### Post by MZ250Supa5 on 2019-07-21
I've just done a fresh re-install and want to run a few 32 bit progams on my Ubuntu Mate 18.04 machine. I've tried the standard 'remedies', none of which work, and I've been searching for a post that I found on AskUbuntu, which though relating to something different,(it was mentioned in passing) actually had a solution that not only worked, but was simple to implement - and from the tone of the writing, it seemed that the writer had had a hand in creating this solution. But can I find it? Of course I can't and I didn't bookmark it, as I didn't expect to need it again, just yet. If anyone knows the solution, or has come across the post I saw, I'd be very happy indeed if you could let me know.

---

### Post by dragonfly41 on 2019-07-21
You just have to try different google search patterns until you hit pay dirt .. or scan through your cached browser history

here is one link found ..

[https://superuser.com/questions/1076730/how-to-run-32-bit-app-in-recent-ubuntu-64-bit](https://superuser.com/questions/1076730/how-to-run-32-bit-app-in-recent-ubuntu-64-bit)

---

### Post by Dennis N on 2019-07-21
This is the general procedure to install a 32-bit program. I have used it many times to install native 32-bit Linux games:

Preliminary Step:
Check for 'foreign' architectures. You should get:
```
dmn@Sydney:~$ dpkg --print-foreign-architectures
i386

```since nowadays, 32-bit is enabled by default in Ubuntu.

_Step 1_
Install: lib32z1 and libc6:i386.

_Step 2_
Open terminal and type command to run the 32-bit program. You will get some error displaying a missing library and "cannot open shared object file: No such file or directory", like:

```
dmn@Sydney:~/games/thomasLinuxStandalone$ ./thomasWasAlone
./thomasWasAlone: error while loading shared libraries: libGLU.so.1: cannot open shared object file: No such file or directory
```

_Step 3_
Then you install the package providing that library. One way to find it is consult Ubuntu Packages Search:
[https://packages.ubuntu.com/](https://packages.ubuntu.com/)
using the search box under "Search the contents of packages". For my example above, it returns 

```
You have searched for files named libGLU.so.1 in suite disco, all sections, and all architectures. Found 6 results.
File 	Packages
/usr/lib/aarch64-linux-gnu/libGLU.so.1 	libglu1-mesa [arm64]
/usr/lib/arm-linux-gnueabihf/libGLU.so.1 	libglu1-mesa [armhf]
[COLOR="#FF0000"]/usr/lib/i386-linux-gnu/libGLU.so.1 	libglu1-mesa [i386][/COLOR]
/usr/lib/powerpc64le-linux-gnu/libGLU.so.1 	libglu1-mesa [ppc64el]
/usr/lib/s390x-linux-gnu/libGLU.so.1 	libglu1-mesa [s390x]
/usr/lib/x86_64-linux-gnu/libGLU.so.1 	libglu1-mesa [amd64]

```
Install the i386 architecture package, libglu1-mesa:i386. Note when installing from terminal, you add :1386 after the package name from the results to get the 32 bit version. (I mostly use Synaptic Package Manager, where you can restrict the package list by choosing the 'architecture' filter in the lower-left.)

Repeat step 2 and 3 after each package install until there is no error message.

---

