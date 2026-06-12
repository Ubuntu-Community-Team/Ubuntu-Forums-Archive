---
title: "Compiling from source"
date: 2012-10-28
forum: General Help
---

### Post by IAMTubby on 2012-10-28
Hello,
I am new to the wonderful world of open source and I'm loving it. But where I keep getting stuck and my progress gets hindered is, when I try to install packages from source. I have read about ./configure, make and make install and what they do, but I guess I'll get better at compiling the more I try it hands-on.

It would be great if we could have a forum where most troubleshooting to installations are discussed ? Is there something of that sort already ? Or else, I would like to update this thread as and when I find something new to help beginners like me.

1)At the moment, I'm having problems installing google-chrome from source.
**a)**I have a .deb called google-chrome-stable_current_amd64.deb and I tried doing 
```

sudo dpkg -i google-chrome-stable_current_amd64.deb

```
but it gives me an error saying,

```
Errors were encountered while processing: google-chrome-stable
```

**b)**I tried ar vx google-chrome-stable_current_amd64.deb and it gives me 3 files called control.tar.gz, data.tar.lzma and debian-binary. I don't know what to do with these.

2)Is a .deb file a compressed form of the executables, **no source code,** whereas .tar.bz2 etc contain source code ?

3)Why does linux have so many file types. .tar,   .tar.gz,   .tar.bz2,   .deb  .rpm   src.rpm

Thanks

---

### Post by cariboo on 2012-10-28
Instead of answering your question, here's one for you. Why are you compiling programs from source, when the majority of them are already packaged as .debs?

Ubuntu is the 1000lb gorilla of Linux distributions, even most third party programs are available in .deb format.

---

### Post by WitchCraft on 2012-10-28
On a) You need to do:
```

apt-get install lsb

```
first

lsb - Linux Standard Base 4.0 support package

Unlike apt, dpkg does not do automagic dependency resolution for you.

on b 2)
A .deb is the equivalent of a windows installer file. It may contain the executable, but it may also contain sourcecode. Usually it contains the executable and other files that need to be installed.

For the packages supplied in ubuntu, you can usually do a apt-get source "package-name"
and you get the source via .deb file installed directly on your computer.
The source is not enough, by the way, you also need the dependencies of the source.
Which you get via: apt-get build-dep "packagename"

.tar is simply an abbrevation for **t**ape **ar**chive (from ancient times, for backups on a tape). That is, all files in a folder and subfolders (e.g. 1'000'000 files) merged into ONE file.

.tar.bz2 is a tape archived file that has been compressed using the **bz**ip-**2** compression algorithm.


3) 
These file types are not Linux specific (except *.deb, *.rpm, which are the equivalent of a .msi file on windows [or setup.exe]).

tar and tar.bz2 I have already explained
tar.gz is a .tar file that has been compressed using the **gz**ip compression algorithm.
By the way, other notable compressed formats are .zip, .zipx, .rar, .cab.
On Linux you'll also find .tar.lzma, which is a .tar file that has been compressed using the **L**empel-**Z**iv-**Ma**rkov algorithm. These files are sometimes called .7z, because this is the file type extension that **7z**ip  windows program uses when it LZMA-compresses a file/files.

There exist so many files, because there exist so many compression algorithms.
And most of these file-types have nothing to do with Linux itself.
Each algorithm has advantages and disadvantages, and the algorithm's efficiency are optimized for certain use cases, or superseded by a new version (bzip2 supersedes bzip).

By the way, a .deb file is simply a .zip file renamed to .deb.
.RPM might be the same.

The difference between .deb and .rpm is, .deb is a **Deb**ian package file, while .rpm is a **R**ed Hat **p**ackage **m**anager file. So, .deb is for Debian-based Linux distributions (like Ubuntu), while .rpm is fore red hat based Linux distributions (like CentOS or Fedora).

---

### Post by sathyastorm on 2013-03-20
I tried to fetch the source code of vlc  with

apt-get source vlc 

but it failed can anyone help  me with this..

apt-get source vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for vlc


shows the error i encountered

---

### Post by tgalati4 on 2013-03-21
You must add the source repositories in /etc/apt/sources.list.  You can add it through *synaptic*.  It's probably easier using "Software Manager"==>Edit==>Software Sources.  Check the box that says* Source Code*.  Then refresh the repositories.  Close Software Manager.  You can only have one package manager open at a time.

Now install build-essentials:

```
sudo apt-get install build-essentials
sudo apt-get source vlc
```

There's a little more to it than that.  Some light reading:  [https://help.ubuntu.com/community/CompileVLC](https://help.ubuntu.com/community/CompileVLC)

---

### Post by sathyastorm on 2013-03-21
Thanks pal, it realy works.......

---

### Post by sathyastorm on 2013-03-21
does the procedure vary on linux mint maya

---

### Post by gordintoronto on 2013-03-21
Actually, the package is "build-essential" without an 's' at the end. For doing this, Mint and Ubuntu are identical.

However... VLC is huge, with a ton of dependencies! If this is the first time you are compiling from source, pick something small. Install VLC from Synaptic.

---

### Post by andrew.46 on 2013-03-22
> **gordintoronto said:**
> Actually, the package is "build-essential" without an 's' at the end. For doing this, Mint and Ubuntu are identical.

However... VLC is huge, with a ton of dependencies! If this is the first time you are compiling from source, pick something small. Install VLC from Synaptic.

Indeed, this slightly dated guide clearly demonstrates that quite clearly:

[https://help.ubuntu.com/community/CompileVLC](https://help.ubuntu.com/community/CompileVLC)

---

### Post by sathyastorm on 2013-04-03
thanks pal

---

