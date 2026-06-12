---
title: "Building a kernel module from source? gcc-3.4 or gcc-4.x?"
date: 2005-10-14
forum: General Help
---

### Post by Jingo on 2005-10-14
Trying to build a new ibm_acpi module, which I have done 100+ times, also on Hoary.

Now this gcc-3.4 missing thing, is the kernel not compiled with gcc-4.x?

```

make -C /lib/modules/2.6.12-9-686/build SUBDIRS=/home/johannes/dep-packages/ibm-acpi-0.11 modules
/usr/src/linux-headers-2.6.12-9-686/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-686/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-686'
  CC [M]  /home/johannes/dep-packages/ibm-acpi-0.11/ibm_acpi.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/johannes/dep-packages/ibm-acpi-0.11/ibm_acpi.o] Error 127
make[1]: *** [_module_/home/johannes/dep-packages/ibm-acpi-0.11] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-686'
make: *** [default] Error 2

```

---

### Post by matthew on 2005-10-14
You can download gcc-3.4 from the repositories. 4.0 is the default in Breezy but the kernel still needs 3.4. Since most people will probably never compile their own kernel it was seen as unnecessary to include it in the default installation figuring that those who would want it could download it...at least that it what I understood.

---

### Post by slamdunk on 2005-10-14
sorry, but i think it's a really big mistake do not include gcc-3.4!

I have (amd64 - there is a my post under ubuntu/amd64) installed ubuntu 5.10. I need of wireless, but I cannot compile ndiswrapper 1.4 (version is important) because gcc-4.0 makes not linkable modules for kernel (compiled with gcc-3.4). And so I cannot connect on internet to download gcc-3.4;)
And so if you need to compile module for your modem 56k, adsl-usb, or wireless, you cannot on ubuntu? Just if you have precompiled binaries or pppoe you can connect on internet?

If it's so, I think it's a big mistake, and many people is constrict to remove ubuntu...

---

### Post by strips on 2005-10-14
Did I miss something.. Why isn't Breezy shipped with a kernel that's compiled with gcc 4.x ?

Is there some kernel - gcc4 incompatibility issu?
I found this in a [forum]("http://www.linuxquestions.org/questions/showthread.php?threadid=368258"):
> Compile a 2.6.12 or newer kernel or use export CC=/usr/bin/gcc-3.3 maybe even gcc-3.4 depending on which is installed in the shell before starting. GCC 4.0 has problems compiling any kernels older than 2.6.12.So 2.6.12 should be able to compile with gcc4?

How about a custom kernel with gcc4?

And I second that "*it's a really big mistake do not include gcc-3.4!"*.

Alot of people install the Nvidia driver from nvidia.com, not to mention Ndiswrapper or VMWare.

All theese requires the kernel-headers and the correct compiler.

---

### Post by drigloi on 2005-10-14
I'm trying to compile Paragon's NTFS for Linux trial ufsd module under Breezy (worked well under Hoary). I get this:

```
root@ubuntu:/usr/src/ntfs# sh install.sh
configure kernel
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
  HOSTCC  scripts/basic/fixdep
/bin/sh: gcc-3.4: command not found
make[1]: *** [scripts/basic/fixdep] Error 127
make: *** [scripts_basic] Error 2
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make: gcc-3.4: Command not found
  CHK     include/linux/version.h
ufsd driver can be compiled for kernel 2.6.12(2.6.12)
We can build module only for 2.6.x kernels
Ufsd module was build and will be installed for kernel 2.6.12 but current kernel in 2.6.12-9-386.
Moving module in destination directory...
`./objfre/ufsd.ko' -> `/lib/modules/2.6.12/kernel/fs/ufsd/ufsd.ko'
Finding module dependencies...
I think you are using a Debian-like system
can't load ufsd module

```

After a "sudo apt-get install gcc-3.4" command however I get this:
```
root@ubuntu:/usr/src/ntfs# sh install.sh
configure kernel
scripts/kconfig/conf -s arch/i386/Kconfig
#
# using defaults found in .config
#
  CHK     include/linux/version.h
ufsd driver can be compiled for kernel 2.6.12(2.6.12)
We can build module only for 2.6.x kernels
Ufsd module was build and will be installed for kernel 2.6.12 but current kernel in 2.6.12-9-386.
Moving module in destination directory...
`./objfre/ufsd.ko' -> `/lib/modules/2.6.12/kernel/fs/ufsd/ufsd.ko'
Finding module dependencies...
I think you are using a Debian-like system
can't load ufsd module
root@ubuntu:/usr/src/ntfs# modprobe ufsd
FATAL: Error inserting ufsd (/lib/modules/2.6.12-9-386/kernel/fs/ufsd/ufsd.ko): Invalid module format
```

So the module gets compiled but it is incompatible with the current kernel. I see that there are difficulties compiling custom kernel modules under Breezy's kernel because of the gcc4/gcc3.4 thing. Is there something I can do to compile a working ufsd module? I would need it.

---

### Post by TiMBuS on 2005-10-14
Oh wow. I'm not the only one.
I need the linux-headers to compile my USB Modem modules! Meaning I have no internet, which means I can't easily upgrade around this problem.
I tried simply making a dynamic link from gcc-3.4 to gcc-4.0 in /usr/bin and the modules compiled, but as above. Can't insert them =(
Ruined my day, breezy.

---

### Post by slamdunk on 2005-10-15
TiMBuS you confirm my theory...:(

everybody need to compile ndiswrapper for wireless, usb-adsl modules, 56k modules etc. for internet connection cannot use this distro!

I have tried to download manually .deb packages, but they are too updated respect 'breezy-release'! And so Ubuntu-Breezy is an unusable and useless distro, and I'm constricted to remove it! Many lost time...

I would like shake the hand to packages-tree maker... a real genius!

My suggestion to Ubuntu-Team: soon release with necessary packages...

Ok guys, thanks for help however, I'm going to install opensuse...

---

### Post by Arktis on 2005-10-15
You can't please everyone.

There should have been some gcc-4 compiled kernels in the repos for breezy, yes.  File a bug report on the modules you can't use.
As far as not being able to download the proper packages but still being able to get online somewhere to complain about it... you figure it out.

---

### Post by strikeforce on 2005-10-15
All you need to do is type this in the console if you have gcc-3.4 installed which you can get from the repositories.

```


export CC=gcc-3.4


```

After you have done that ubuntu will use gcc-3.4

---

### Post by samjam on 2005-10-15
[QUOTE=strips]Did I miss something.. Why isn't Breezy shipped with a kernel that's compiled with gcc 4.x ?
...
Alot of people install the Nvidia driver from nvidia.com, not to mention Ndiswrapper or VMWare.

All theese requires the kernel-headers and the correct compiler.[/QUOTE]

I second this, breezy has been released without following the above advice. Yeah, lets try and use my wireless network card that doesn't work to download gcc-3.4 so I can build ndiswrappers and make my network card work. - oh

Redhats famed kgcc saga was bad enough, but these days its fashionable and eminently possible to have multiple gcc installed, so why be afraid to do it?

Sam

---

### Post by odrop on 2005-10-18
Some of you are luckier than I.  At least you can get on the net with Ubuntu.

I have to compile custom slmodem modules for Ubuntu, to get my modem to work.  So now I've got my fresh and shiney new Kubuntu CD today and set to work doing just that.  Now I find out I have to run through hurdles to even get the correct version of gcc installed, or go figure out what I need to do to compile my own custom kernel.

This is a bit frustrating to say the least.  (K)Ubuntu had won me over for awhile, but this definitly wasn't one of the brightest moves on their part.

---

### Post by blastus on 2005-10-18
I managed to compile my Lucent 56K modem driver under Breezy but I **DESTROYED MY BREEZY INSTALLATION** in the process... [breezy badger - cannot compile Lucent modem drivers](http://www.ubuntuforums.org/showthread.php?t=77537). However, I salvaged the modules I compiled and then re-installed Breezy from stratch.

I'm so glad everyone else is having this exact same gcc 3.4/gcc 4.0 problem. It is a vicious cycle--you need to compile kernel modules to connect to the Internet, but you need gcc-3.4 to compile them, but you need to have a connection to the Internet to get gcc-3.4.

---

### Post by aldin on 2005-10-20
problem solved:

before installing breezy u have to do this:

manually download three packages from (burn it or save it on some partition)

[http://archive.ubuntu.com/](http://archive.ubuntu.com/)

[B]cpp-3.4_3.4.2-2ubuntu1_i386.deb
gcc-3.4-base_3.4.2-2ubuntu1_i386.deb
gcc-3.4_3.4.2-2ubuntu1_i386.deb
[/B]

1. install breezy

2. apt-get install build-essential linux-headers-386

3. go to directory where u've have "gcc" packages &

[B]dpkg -i *.deb
export CC=/usr/bin/gcc-3.4[/B]

after this my modem is working, hope urs too...

BiH

---

### Post by Mr Frosti on 2005-10-20
To append to this, the following package may or may not be required. I installed "gcc-3.4", and exported as shown above to use this version, but I received an error in VMware about being unable to run "cc1plus". It turns out I also needed package "g++-3.4"

---

### Post by aldin on 2005-10-22
[QUOTE=aldin]
[http://archive.ubuntu.com/](http://archive.ubuntu.com/)

[B]cpp-3.4_3.4.2-2ubuntu1_i386.deb
gcc-3.4-base_3.4.2-2ubuntu1_i386.deb
gcc-3.4_3.4.2-2ubuntu1_i386.deb
[/B]
[/QUOTE]

note: i found that export CC=/usr/bin/gcc-3.4 is not needed, dpkg- i *.deb should work fine...

litlle preciselly:
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/)

---

### Post by nickmcg on 2005-12-11
If you don't want gcc 3.4, try the following:

cd /usr/bin
sudo ln -s gcc-4.0 gcc-3.4

It worked for me recompiling ndiswrapper

---

### Post by phil_n on 2005-12-11
[QUOTE=Arktis]
As far as not being able to download the proper packages but still being able to get online somewhere to complain about it... you figure it out.[/QUOTE]

It's easy to get online using a different computer... but then you need to download the packages you need on that computer and get them onto the laptop somehow, I guess with a CD or whatever. I don't know how to do that - I just use Synaptic and it works, I don't know what it does with the .deb files, or how to download a package manually on a windoze box and then manually install it under Ubuntu. Perhaps if you know the answer you could post it, or link to it? That would help these guys out, I guess.

---

### Post by Eyeore on 2006-04-15
[QUOTE=nickmcg]If you don't want gcc 3.4, try the following:

cd /usr/bin
sudo ln -s gcc-4.0 gcc-3.4

It worked for me recompiling ndiswrapper[/QUOTE]

Thanks for the tip. This worked great for me trying to compile ndiswrapper 1.13

---

