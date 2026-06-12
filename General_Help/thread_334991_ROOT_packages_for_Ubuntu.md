---
title: "ROOT packages for Ubuntu?"
date: 2007-01-09
forum: General Help
---

### Post by underwater on 2007-01-09
I am interested in installing ROOT   [http://root.cern.ch]("http://root.cern.ch")

Does anyone happen to know if there is a repo or Ubuntu package somewhere for this?  A quick google search hasn't turned up anything though I will keep trying.  

I hope I don't have to build it from source.  :-/

---

### Post by tzulberti on 2007-01-10
I see that it has RPM file... I don't know if this would work:
1) Download an RPM file
2) Use alien to convert it into a Deb file
3) use "sudo dpkg -i NameOfTheDebFile.Deb" to install it...

---

### Post by suxen on 2007-03-20
underwater,
> Does anyone happen to know if there is a repo or Ubuntu package somewhere for this?

Yes, there is:
[http://mirror.phy.bnl.gov/debian-root/](http://mirror.phy.bnl.gov/debian-root/)

Actually, only for i386 platforms. I'm on amd64, so I have to stick to the sources.
As for ubuntu, many ROOTers experience problems with the gui. It crashes, when the
browser utility is envoked , e.g

```
root[0] new TBrowser
```

Let me know, if you get the same problem after installing the binaries.

Happy ROOTing

---

### Post by ssam on 2007-10-18
> **suxen said:**
> 
Yes, there is:
[http://mirror.phy.bnl.gov/debian-root/](http://mirror.phy.bnl.gov/debian-root/)

Actually, only for i386 platforms. I'm on amd64, so I have to stick to the sources.


you can use the source packages in that repo to make deb files for your architecture.

add
```
deb http://mirror.phy.bnl.gov/debian-root unstable main contrib
```
to you source.list

then run
```

sudo apt-get install build-dep root-system
apt-get source root-system
cd root-system_5.16.00
dpkg-buildpackage -rfakeroot

```

then use dpkg -i to install the packages it makes

(i am trying this on powerpc gutsy now, its taking a while to compile)

---

### Post by jalirious on 2007-10-19
Hi, how's the root installation going? Scratching my head at how to install it on my gutsy (i386). Tempted to try the package for fiesty, but that would be too easy to work. Could you post a guide if you succeed?

EDIT

put 
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free 
deb [http://mirror.phy.bnl.gov/debian-root/ubuntu](http://mirror.phy.bnl.gov/debian-root/ubuntu) gutsy main contrib

in /etc/apt/sources.list

apt-get update
ignore warnings.
apt-get install root-system

(5.17/04)

---

### Post by mr.kuhi on 2007-11-13
> **jalirious said:**
> 
ignore warnings.


You recieve GPG error about no public key, your error message can look for example like this:

```

GPG error: http://mirrors.kernel.org testing Release: The following
signatures couldn't be verified because the public key is not available:
NO_PUBKEY 010908312D230C5F

```

To fix it you have to replace KEY word with numbers from YOUR error message:
```

$ gpg --keyserver subkeys.pgp.net --recv-keys KEY
$ gpg --armor --export KEY | sudo apt-key add -

```
Of course all in console

---

### Post by jalirious on 2008-02-12
Cheers!

---

### Post by wmgobuffs on 2008-04-21
I just want to confirm, for any new searchers, that the bnl deb package works for Hardy Heron.  I have installed  ROOT 5.16.27 on an x86 with none of the TBrowser issues that people have mentioned.

---

