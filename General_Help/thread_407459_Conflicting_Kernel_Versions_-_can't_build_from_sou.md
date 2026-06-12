---
title: "Conflicting Kernel Versions - can't build from source"
date: 2007-04-12
forum: General Help
---

### Post by jackn on 2007-04-12
I'm trying to build a driver package for my webcam from source.

After I untar it and cd into the newly created directory, I do 'make'.

At this point, I get the following output:

```
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/jacknn/gspcav1-20070110 CC=cc modules
make: *** /lib/modules/2.6.17-11-386/build: No such file or directory.  Stop.
make: *** [default] Error 2
```

The first line seems to be looking for the necessary 'build' file using `uname -r`. 
When I run 'uname -r' myself, I get 

```
2.6.17-11-386
```

which is indeed where 'make' looks for the 'build' files, as it says in the second line. 

The 'build' files, however, are not there. 

I can only find a 'build' directory elsewhere:
```

$ locate build |grep module
/lib/modules/2.6.17-10-generic/build
/lib/modules/2.6.17-11-generic/build
```

Yet, 'uname' is, of course, 'right', as I startup with 2.6.17-11-386.

Apparently, when I installed 'build-essential', it went to the '-generic' version.

And now, 'make' looks for it where it ought to, in '-386', but can't find it there.

I've tried to symlink:
```
$ sudo ln -s /lib/modules/2.6.17-11-386/build/ /lib/modules/2.6.17-11-generic/build
ln: creating symbolic link `/lib/modules/2.6.17-11-generic/build/build' to `/lib/modules/2.6.17-11-386/build/': File exists
```

There are two things seemingly wrong with this output. 

First, I asked for a link from '-generic/build', but Bash tries to link '-generic/build/build'. But then it might know better.
Then, Bash says the '-386/build' file exists, yet it doesn't seem to (as 'make' has already stated)...:

```
$ ls -a /lib/modules/2.6.17-11-386
.       madwifi         modules.ieee1394map  modules.pcimap    volatile
..      modules.alias   modules.inputmap     modules.seriomap
initrd  modules.ccwmap  modules.isapnpmap    modules.symbols
kernel  modules.dep     modules.ofmap        modules.usbmap
```

The issue seems to be a known one, as there is a script going by the name:

```
/usr/share/doc/linux-image-2.6.17-11-386/examples/sample.force-build-link.sh
```

which apparently tries to deal with it.


Yet, it says:

```
# Status           : Unknown, Use with caution!
```

so I was wary of having a go at it.

What do you think? And, while this seems to be a bug, the issue also seems to be known. Shoud I report it?

Finally, do I really need the '-generic' kernel. Isn't one solution to just remove this kernel (I wouldn't know how) and then reinstall 'build-essential'?!

Thank you kindly for your help.
Jackn

---

### Post by garrido on 2007-04-12
Do you have the kernel sources in your system?

```
sudo apt-get install linux-source
```

---

### Post by jackn on 2007-04-12
Thank you, garrido, for the prompt response.

Indeed, I didn't have 'linux-source' in my source list. 
I wonder: 
1. How could you tell? 
2. Why didn't I have it? 
The answer to the second question might be that I used the source list provided by the (unofficial) Ubuntuguide for Edgy, which invites you to replace your list with a given, expanded list. Is that it? 

I installed linux-source and tried 'make' on the my package again. 
No luck.

I rebooted and tried again. No luck.

I then removed 'build-essential' and reinstalled it, hoping that this time it would insall to the \-386' kernel files. It didn't.

I tried to create my symlinks again as, still, there was no 'build' folder in the '-386' kernel files. This time the creation of symlinks was possible;

```
$ ls -l /lib/modules/2.6.17-11-386/build/
total 0
lrwxrwxrwx 1 root root 41 2007-04-12 16:37 arch -> /lib/modules/2.6.17-11-generic/build/arch
lrwxrwxrwx 1 root root 42 2007-04-12 16:37 block -> /lib/modules/2.6.17-11-generic/build/block
```

... (cut short)
I don't know whether the symlinking worked this time thanks to the linux-source package.

The 'make' command, while going further this time, still didn't go through:

```
~/my_tarballs/gspcav1-20070110$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/jacknn/my_tarballs/gspcav1-20070110 CC=cc modules
make[1]: Entering directory `/lib/modules/2.6.17-11-386/build'
Makefile:450: .config: No such file or directory
  Building modules, stage 2.
/lib/modules/2.6.17-11-386/build/scripts/Makefile.modpost:38: .config: No such file or directory
make[2]: *** No rule to make target `.config'.  Stop.
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/lib/modules/2.6.17-11-386/build'
make: *** [default] Error 2

```

I'm not sure what this means.

Indeed, a .config file is expected in the file 'Makefile.modpost' mentioned in the above output:

```
include .config
```

(taken from Makefile.modpost)
Is it a .config fiel belonging to the package being built?  Or is it a call for a system file? I suspect the former, but I don't know.

Indeed, contrary to the usual building from source routine, you're not supposed to run  'config', but rather skip to 'make'.
In the files of the untarred package there is no 'config':
```

gspcav1-20070110$ ls
changelog  Etoms         gspca.h    Pixart   Sunplus-jpeg  Vimicro
Conexant   gspca_build   Makefile   Sonix    Transvision
decoder    gspca_core.c  Mars-Semi  Sunplus  utils
```

Nor is there a Readme file in sight.

Now, if the issue is indeed the package, which I know others have installed, then this does not justify this thread.
But I don't know: Is what I'm observing related to the two kernels conflict or to the package?

Very grateful for your help, garrido.

Jackn

---

### Post by garrido on 2007-04-12
Well, I'm just making educated guesses here, I'm no expert....  What I do know is that you need to have the kernel source in order to compile modules against it.  You might try checking for linux-headers as well:

linux-headers-386
linux-headers-generic 

I believe (but I'm not sure) that if you apt-get linux-headers-generic you will get what you need.  Try it ;)

---

### Post by az on 2007-04-12
> **garrido said:**
> Well, I'm just making educated guesses here, I'm no expert....  What I do know is that you need to have the kernel source in order to compile modules against it.  You might try checking for linux-headers as well:

linux-headers-386
linux-headers-generic 

I believe (but I'm not sure) that if you apt-get linux-headers-generic you will get what you need.  Try it ;)


Right.  You do not need the full linux source!  You need the source to hack the kernel and write new drivers.  

To build an extra module for your running kernel, you need to use the linux-headers packages. (This is what you want to do!)

Get rid of the linux source you have (it probably is misconfigured)  Get rid of the symlink you made (/build) and then install the linux-headers.  They are properly configured (versioned) and match your running kernel and will provide the appropriate /build symlink.

---

### Post by garrido on 2007-04-12
> **az said:**
> Right.  You do not need the full linux source!  You need the source to hack the kernel and write new drivers.  

To build an extra module for your running kernel, you need to use the linux-headers packages. (This is what you want to do!)



Ah, thnx for that az! I always thought you needed the whole thing to compile modules...

---

### Post by jackn on 2007-04-12
Thank you for the attention and the advice.

Ok, installed linux-headers-386. 
Linux-headers-generic had already been there.

Removed my symlinks.

I stopped short of removing the -generic kernel, as I got this output:

```
$ sudo aptitude remove linux-image-2.6.17-11-generic
 ...   
The following packages are BROKEN:
  linux-image-generic linux-restricted-modules-2.6.17-11-generic 
The following packages will be REMOVED:
  linux-image-2.6.17-11-generic 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 67.6MB will be freed.
The following packages have unmet dependencies:
  linux-image-generic: Depends: linux-image-2.6.17-11-generic but it is not installable
 linux-restricted-modules-2.6.17-11-generic: Depends: linux-image-2.6.17-11-generic but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
linux-restricted-modules-2.6.17-11-generic

Downgrade the following packages:
linux-image-generic [2.6.17.11 (edgy-security, now) -> 2.6.17.10 (edgy)]
linux-restricted-modules-generic [2.6.17.11 (edgy-security, now) -> 2.6.17.10
(edgy)]

Score is -481

Accept this solution? [Y/n/q/?] n

```

Aptitude thinks -generic is broken. 
I checked (a dry aptitude run with the -d switch), and with -386 I don't get any broken package warnings.

It might be a good idea to get rid of -generic, and hope that then reinstalling acompanying packages for -386 will do the job. How do you feel about that? Should I? And, if so, how?

What is a good way of handling the broken packages in order to remove them?
Can't I simply use the reinstall switch in aptitude? 
Another possibility is the debug images: linux-image-debug-2.6.17-11-386. Another one exists for -generic.
Could I use those to fix the packages? How? Wasn't able to find anything on the net regarding a linux-image-debug.

In any case, I'm back to square one: When I run 'make' for the package I'm trying to build from source, it puts out the older error message, namely no 'build'. This makes sense, as -386 now has neither its own nor the symlinks.
 
I have a working box. It's just that I can't, at this point, install the package, which is needed to drive my webcam. 
I'd like to work this out so as to learn something from it, and perhaps fix it.

Thank you garrido and az.

Jackn

---

