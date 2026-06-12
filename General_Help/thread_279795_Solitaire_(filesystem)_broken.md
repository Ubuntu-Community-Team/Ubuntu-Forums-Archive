---
title: "Solitaire (filesystem?) broken"
date: 2006-10-18
forum: General Help
---

### Post by mrashley on 2006-10-18
Mom couldn't open her solitaire. So, I tried to open it in a terminal. The error message is 

```
sol: error while loading shared libraries: libqthreads.so.12: cannot open shared object file: Input/output error
```

So after some searching I found that libqthreads.so.12 is part of the package called libqthreads-12. I thought I would reinstall this.

```
louise@cybill:~$ sudo apt-get install libqthreads-12 --reinstall
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 16 not upgraded.
Need to get 0B/5524B of archives.
After unpacking, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 101117 files and directories currently installed.)
Preparing to replace libqthreads-12 1.6.7-2 (using .../libqthreads-12_1.6.7-2_i386.deb) ...
Unpacking replacement libqthreads-12 ...
dpkg: error processing /var/cache/apt/archives/libqthreads-12_1.6.7-2_i386.deb (--unpack):
 unable to stat `./usr/lib/libqthreads.so.12.3.0' (which I was about to install): Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/libqthreads-12_1.6.7-2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Odd. I took a look at the directory.
If I show a directory listing of /usr/lib/libqt*

```
louise@cybill:/usr/lib$ ls libqt*
ls: libqthreads.so.12: Input/output error
ls: libqthreads.so.12.3.0: Input/output error
libqtmcop.so.1      libqt-mt.so.3    libqt-mt.so.3.3.6
libqtmcop.so.1.0.0  libqt-mt.so.3.3

```

What should I do? I was going to fsck the root folder, but I can't do that without downloading and burning an Ubuntu cd. I thought I should check if that's even the right avenue to take.  Thoughts anyone? :-k

---

### Post by mrashley on 2006-10-19
Anyone who might care about this.. 

I downloaded the ubuntu cd. burned the ISO and rebooted using it.

I then booted into recovery mode, when presented with a prompt I forced a 'scandisk' by typing
```

fsck /dev/hda1 -f
```

It found various lib files were supposedly deleted. I'm not quite sure why this is.  I'd love to know the key combo to press to flush the harddrive cache in case there is a bad crash. I know it's something very awkward.

---

### Post by mbeierl on 2006-10-19
Well, there used to be the "SysRq-S" combo that would sync the filesystem in the event of a kernel crash, but that was an option that had to be compiled in.

In current linux distros, though, ext3 is used as the filesystem, not ext2, which should pretty much remove the need for any sort of sync/flush on crash.  ext3 is a journalling filesystem, making it much more robust.

I would be more concerned with a potential impending hard drive failure.  I've crashed my linux box far too often (playing with bleeding edge kernels and such) and have not had filesystem corruption using ext3.

---

### Post by MWAAAHAAA on 2006-10-19
> 
dpkg: error processing /var/cache/apt/archives/libqthreads-12_1.6.7-2_i386.deb (--unpack):
 unable to stat `./usr/lib/libqthreads.so.12.3.0' (which I was about to install): Input/output error


As you can see it sais './usr/...' NOT '/usr/...'. This means that seomthing is wrong with the package you have on your machine. I suggest you try redownloading the package and trying to install that one manually using dpkg.

You can search for packages manually at [http://packages.ubuntulinux.org/](http://packages.ubuntulinux.org/) and download from there as well. Installation of the package can then be performed by 'dpkg -i' and then the package name.

One small question though, is there any space left on the partition where /var/ is located (probably your root partition)?

---

