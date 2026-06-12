---
title: "How to mirror just edgy with windows client?"
date: 2007-01-10
forum: General Help
---

### Post by wentlank on 2007-01-10
I work in a lab environment and want to get ubuntu into the lab.  I would like to set up a repository that has everything edgy for the i386 platform.

There is plenty of documentation on how to mirror the archive if you are using linux tools.... the problem is that the only way I am allowed to connect to the internet is with a windows box.

I started mirroring archive.ubuntu.com with a ftp client and quickly found that this is not what I want.... the queue filled to over 200G  (is that right?)

Please help!!

In a nutshell I have a lab that isn't connected to the internet.

I want to get a ubuntu repository in the lab.

I can only connect to the internet with a windows box.....

You have 30 seconds to accept this challenge....  

Thanks in advance.

---

### Post by koenn on 2007-01-10
quick and dirty" reply (or: here's where I would start if it were my problem ) :

[LIST=1]
[*]have a look at what a Ubuntu miror looks like, eg [http://ftp.belnet.be/packages/ubuntu/ubuntu/pool/](http://ftp.belnet.be/packages/ubuntu/ubuntu/pool/)
[*]look especially at how the directories are organized (main, restricted, any subdirs ?)
[*]get a tool that lets you download a website, eg wget. you'd be interested in only getting packages that end in _i386.deb and _all.deb  (let wget use ftp, it deals with dirs and wildcards better than over http)
[*]download these packages and try to maintain the same directory structure
[*]look for debian mirror maintainer tools such as scanpackages which will help to create the Packages.gz file and others that are needed for your downloaded files to work as a mirror.
[*]Put everything on a http server.
[/LIST]

alternatives : 
[LIST=1]
[*]see if you can bypass the limitation of "only interne access for windows. Why is that, anyway ?
[*]set up a genuine miror on a linux system running inside "Virtual PC" on a windows box and claim (or make it so) that the windows box is connected to the internet
[/LIST]

---

### Post by wentlank on 2007-01-10
Thanks that helps out alot.....

I wasn't sure what files I would need exaclty...  

I could use httrack to get just the _i386.deb and _all.deb files and still maintain the directory structure then use a tool to recreate the repository locally?

I work for the government and windows is all they will allow on the internet.

Thanks again.

---

### Post by koenn on 2007-01-10
yep, in theorie all you need is a web server and the packages. Ideally, they'd be in a directory tree as shown in the exemple i gave you, although it is also possible to have them all in 1 directory.

The Debian/ubuntu naing convention for packages is to include the arhitecture in the package name, or use "all" if the package runs on any/all platforms. 

2 additional things you'd need are the Release file and the Packages file. They'll tell the apt/synaptic  of your clients which packages are available on your mirror + some additional info (dependencies, file names, file sizes, location of the file on the mirror, ...) so you'll need them.
You could probably just copy them of a mirror, i don't think the fact that you wouldn't have all packages is not going to harm.
There are also tools to automatically create these files, but obviously they'd run only on linux, so depending on whether you use a windows server (!) or a linux server as the actual mirror (after you've downloaded with a windows machine), you're going to be doing some copying back and forth. 

Keep in mind you'd also want to update your mirror every now and then, to get the newest patches, security releases, ...) so a tool to update the Package file afterwards is going to be convenient. 

[http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html)


and remember this is all "quick and dirty" - you're ging to have to work out some details (which I'm sure is going to be fun :) )

---

### Post by wentlank on 2007-01-10
Thanks.... 

The plan is to recreate the repository on a linux server in the lab under an apache served directory.

I plan on updating my lab repository weekly with the ubuntu packages.

I have another question.... if I do it this way of just downloading the all and the i386 packages what will happen when a new release is available?

I have been using redhat/fedora for years, but I like what I have seen in the limited time of researching ubuntu... thanks for the help.

---

### Post by koenn on 2007-01-11
If you look at eg 
[http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/)**dapper**/main/binary-i386/Packages.gz
you see it lists packages and indicates where in "pool" that packet is to be found.
Random exemple
```

Package: abiword-gnome
(...)
Installed-Size: 6908
(...)
Version: 2.4.4-0ubuntu5
(...)
Filename: pool/main/a/abiword/abiword-gnome_2.4.4-0ubuntu5_i386.deb

```
while [http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz) gives
```

Package: abiword-gnome
Version: 2.4.5-0ubuntu2
Filename: pool/main/a/abiword/abiword-gnome_2.4.5-0ubuntu2_i386.deb

```

so you may have a problem there, because just downloading the pool does not tell you which version belongs to which release. 
You need also the "dist" directories for the versions you're interested in, and their Package file (so forget what I said about making your own Package file - that's not going to work for you); 
so on your server you might have

```
srv/ubuntu/***dists***/**edgy**/main/binary-i386/Packages.gz
srv/ubuntu/***dists***/**edgy-updates**/main/binary-i386/Packages.gz
srv/ubuntu/***dists***/**edgy-security**/main/binary-i386/Packages.gz
srv/ubuntu/***pool***/main/ ...
```

---

### Post by Moose9 on 2008-04-29
I have the same problem. Maybe this script I wrote will help. It does the same thing and more that perl version of apt-mirror does. and it runs from windows. using PortablePython

open and edit the MIRRORS, BASE, and ARCHS vars

---

