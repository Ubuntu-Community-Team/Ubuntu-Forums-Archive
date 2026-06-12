---
title: "Issue &quot;making&quot; a program"
date: 2008-03-07
forum: General Help
---

### Post by wmgries on 2008-03-07
Hi, I am having an issue installing programs on my Kubuntu installation 7.10 when I attempt to install a program, in this case the GIMP.

I've downloaded the package from the Gimp website and managed to unpack it by using: ```
tar xvjf gimp-2.4.5.tar.bz2
```

Then when I go to do the next step of the process I get the problem. After I type this: 
```
cd ~/Desktop/gimp-2.4.5
./configure
```

I get this:

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets ${MAKE}... yes
checking for gcc... gcc
checking for c complier default output name...
configure: error: C complier cannot create executables 
See 'config.log' for more details.
```

Is there a package I need to download or option I need to switch within the OS?

---

### Post by taurus on 2008-03-07
Yes, you need to install the build-essential package first before you can build anything from source.

```
sudo apt-get update
sudo apt-get install build-essential
```
However, you don't like the gimp version from the repos?  You will find out soon enough you need a bunch of other packages, developing packages, if you want to build gimp from source.

---

### Post by wmgries on 2008-03-07
I believe that I already have the build-essential package installed, but how do I check?  

And until I get a new ethernet card, I'm not connected to the internet on my Kubuntu box.  So I'm fine with installing packages as long as I can find them and install them without being connected.  I downloaded (and I think installed?) the build-essential package from [http://packages.ubuntu.com/dapper/devel/build-essential](http://packages.ubuntu.com/dapper/devel/build-essential) last night.  

Can I find the other packages from the same location?

---

### Post by taurus on 2008-03-07
If you've already installed the build-essential package, then how come you still get that error message about not finding a compiler when you run ./configure?

---

### Post by wmgries on 2008-03-07
Well, I'm not sure.  Is there a way I can check to see if it really installed?

---

### Post by taurus on 2008-03-07
```
gcc -v
```
And by the way, build-essential should be on the installer CD so if you still have it, insert it into a drive and run

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
gcc -v
```

---

