---
title: "Installing Maple"
date: 2007-02-13
forum: General Help
---

### Post by Nirva on 2007-02-13
Hay,

At the university where I study we have a license for installing Maple 10.
So I downloaded it and tried installing it but it didn't work out very well.  The manual is quite easy : I have to execute LinuxInstaller.bin
But when I do, this is what I get :

[email]filip@Filip:~/Desktop/maple10.tar.gz[/email]_FILES/Linux/Disk1/InstData/VM$ sh LinuxInstaller.bin 
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.5795/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory
[email]filip@Filip:~/Desktop/maple10.tar.gz[/email]_FILES/Linux/Disk1/InstData/VM$ 


I tried searching in Synaptic Package Manager, but I couldn't find packages like libc, or librt.
Does anyone knows how to solve this problem?

Thanks

---

### Post by llamakc on 2007-02-13
There are plenty of returns when searching for "libc" and these for "libc6"

```

ken@llamakc 08:21:28:~$ apt-cache search libc6
apt - Advanced front-end for dpkg
apt-utils - APT utility programs
libtext-iconv-perl - converts between character sets in Perl
debian-policy - Debian Policy Manual and related documents
libapt-rpm-pkg-libc6.3-6-2 - APT for RPM library
libc6-xen - GNU C Library: Shared libraries [Xen version]
libcompfaceg1 - Compress/decompress images for mailheaders, libc6 runtime
libcompfaceg1-dev - Compress/decompress images for mailheaders, libc6 devel
manpages-ja-dev - Japanese version of the manual pages (for developers)
manpages-pt-dev - Portuguese Versions of the Manual Pages
libc6 - GNU C Library: Shared libraries
libc6-amd64 - GNU C Library: 64bit Shared libraries for AMD64
libc6-dbg - GNU C Library: Libraries with debugging symbols
libc6-dev - GNU C Library: Development Libraries and Header Files
libc6-dev-amd64 - GNU C Library: 64bit Development Libraries for AMD64
libc6-i686 - GNU C Library: Shared libraries [i686 optimized]
libc6-pic - GNU C Library: PIC archive library
libc6-prof - GNU C Library: Profiling Libraries

```

sudo apt-get install libc6 libc6-dev

---

### Post by Maestro23 on 2007-02-13
Do you have extra repositories enabled?  If not, go [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Try to find those packages again.  Either thru Synaptic or sudo apt-get.

---

### Post by Nirva on 2007-02-13
I runned this : 

sudo apt-get install libc6 libc6-dev

But those packages were already installed, so this wasn't the problem.  And yes, I have already enabled the extra repos.

Does someone has another idea?

---

### Post by jrib on 2007-02-20
> **Nirva said:**
> I runned this : 

sudo apt-get install libc6 libc6-dev

But those packages were already installed, so this wasn't the problem.  And yes, I have already enabled the extra repos.

Does someone has another idea?

What version of ubuntu are you using?

The Maple9.5 installer used to work fine for me on dapper and edgy but in feisty I get the same errors as you.  I'm trying to figure out what is going on now...

---

### Post by jrib on 2007-02-20
I resolved the issue after reading the following: [http://ubuntuforums.org/showthread.php?t=260107](http://ubuntuforums.org/showthread.php?t=260107)

Just copy the cdrom file to your hard disk, and issue:

```
sed -i "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" LinuxInstaller.bin
```

After that, 'sh LinuxInstaller.bin' should work...

---

### Post by cmonaco on 2007-03-20
Hi! I've been trying to install maple too and I have the same problem, I tried  

sed -i "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNELL/" LinuxInstaller.bin

but it doesn't work it says 
sed: can't read LinuxInstaller.bin: No such file or directory

I am really new with Linux, so I don't know what to do

---

### Post by jrib on 2007-03-20
> **cmonaco said:**
> Hi! I've been trying to install maple too and I have the same problem, I tried  

sed -i "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNELL/" LinuxInstaller.bin

but it doesn't work it says 
sed: can't read LinuxInstaller.bin: No such file or directory

I am really new with Linux, so I don't know what to do

Did you copy the contents of the cd to your hard drive?  Once you do that you need to 'cd' ('cd' is the command to change directory in the terminal) into the directory that contains LinuxInstaller.bin .  

You said you were new to Linux, so I don't know how comfortable you are on the command line.  Just let me know if everything I say sounds like gibberish....  Or if you want a good intro, take a look at [https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands) .

If you can't find LinuxInstaller.bin, let me know and I will load up my maple cd at home again and provide more details.  From memory, just open a folder that has "linux" in the name.  If that still doesn't get you to LinuxInstaller.bin, a command to help you find it once you 'cd' into the top directory of the cd's files, is:  find -name LinuxInstaller.bin  .  That should find the file for you and tell you where you need to go.

---

### Post by cmonaco on 2007-03-23
Hey thanks a lot, I could install Maple without problems!!!:)

---

### Post by jrib on 2007-04-01
I had to use
```
cat LinuxInstaller.bin.pak | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > LinuxInstaller.bin
``` instead of just the straight sed command above when I installed on amd64.  Found this at [http://ubuntuforums.org/showthread.php?t=283473](http://ubuntuforums.org/showthread.php?t=283473)

---

