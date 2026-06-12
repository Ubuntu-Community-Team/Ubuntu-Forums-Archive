---
title: "How to install BOSS Linux with Wubi?"
date: 2008-02-19
forum: General Help
---

### Post by Futureking on 2008-02-19
Hello,

I want to use BOSS Linux which is also based on debian with WUBI? it is possible? if yes then how? if no then how to tell WUBI developers to make wubi for BOSS linux. BOSS linux is indian version of linux. 

you can check boss linux website: [http://bosslinux.in](http://bosslinux.in)

---

### Post by ago on 2008-02-19
Hi,

I would be glad to help you creating a wubi 8.04 version for BOSS, but do not have the resources to maintain all of ubuntu variants myself. 

In short, you have to grab the sources from LP using bazaar ([https://code.launchpad.net/~ubuntu-installer/wubi/hardy](https://code.launchpad.net/~ubuntu-installer/wubi/hardy))

Then modify the files in the /data folder to your liking as well as the english.nsh file

Then run

make prerequisites && make && make test

---

### Post by Futureking on 2008-02-19
Thank you for replying 'ago'.

I don't know advanced programming(C,C++, Python, Java etc)
I don't know how developers develop software for linux.

Yes I know little bit of programming. I am running my site [http://www.vibgyorlife.com](http://www.vibgyorlife.com) based on ASP.NET3.5

How can I learn programming required for creating WUBI for BOSS?

I found some files here: [http://codebrowse.launchpad.net/~ubuntu-installer/wubi/hardy/files](http://codebrowse.launchpad.net/~ubuntu-installer/wubi/hardy/files)

But could not understood how to work with them?

I am very interested in Linux software development. My dream is to redesign the interface of many popular linux software like GIMP. But I don't know where to start learning?

---

### Post by ago on 2008-02-19
You do not need coding skills to rebrand wubi

You have to run 

sudo apt-get install bzr build-essential
mkdir -p wubi
cd wubi
bzr branch [https://code.launchpad.net/~ubuntu-installer/wubi/hardy](https://code.launchpad.net/~ubuntu-installer/wubi/hardy)
cd hardy
#edit the files in ./data with a normal editor
make prerequisites && make && make test

---

### Post by Futureking on 2008-02-19
I successfully run these commands:

sudo apt-get install bzr build-essential
mkdir -p wubi
cd wubi
bzr branch [https://code.launchpad.net/~ubuntu-installer/wubi/hardy](https://code.launchpad.net/~ubuntu-installer/wubi/hardy)
cd hardy

You told that I have to edit the files in ./data folder.

there are many files in data folder. what I have to edit?
can u give me description of each file? i mean what is meaning of each file in data folder.

---

### Post by ago on 2008-02-19
The important ones are:

version.nsh 
isolist.ini

You may want to add images to data/images
Must be named Yourdistro-header.bmp Yourdistro.ico Yourdistro-vertical.bmp
You may have to change stings in src/wubi/english.nsh

---

### Post by Futureking on 2008-02-20
**I am editing isolist.ini**

[Ubuntu-i386]

version=8.04

subversion=

isoName=

packages=ubuntu-desktop

kernel=casper/vmlinuz

initrd=casper/initrd.gz

metalink=http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-i386.iso.metalink

isoSize=

minIsoSize=600000000



[Ubuntu-amd64]

version=8.04

subversion=

isoName=

packages=ubuntu-desktop

kernel=casper/vmlinuz

initrd=casper/initrd.gz

metalink=http://wubi-installer.org/metalinks/8.04/ubuntu-desktop-amd64.iso.metalink

isoSize=

minIsoSize=600000000



[Kubuntu-i386]

version=8.04

subversion=

isoName=

packages=kubuntu-desktop

kernel=casper/vmlinuz

initrd=casper/initrd.gz

metalink=http://wubi-installer.org/metalinks/8.04/kubuntu-desktop-i386.iso.metalink

isoSize=

minIsoSize=600000000



[Kubuntu-amd64]

version=8.04

subversion=

isoName=

packages=kubuntu-desktop

kernel=casper/vmlinuz

initrd=casper/initrd.gz

metalink=http://wubi-installer.org/metalinks/8.04/kubuntu-desktop-amd64.iso.metalink

isoSize=

minIsoSize=600000000



[Xubuntu-i386]

version=8.04

subversion=

isoName=

packages=xubuntu-desktop

kernel=casper/vmlinuz

initrd=casper/initrd.gz

metalink=http://wubi-installer.org/metalinks/8.04/xubuntu-desktop-i386.iso.metalink

isoSize=

minIsoSize=500000000



[Xubuntu-amd64]

version=8.04

subversion=

isoName=

packages=xubuntu-desktop

kernel=casper/vmlinuz

initrd=casper/initrd.gz

metalink=http://wubi-installer.org/metalinks/8.04/xubuntu-desktop-amd64.iso.metalink

isoSize=

minIsoSize=500000000



[Edubuntu-i386]

version=8.04

subversion=

isoName=

packages=edubuntu-desktop

kernel=casper/vmlinuz

initrd=casper/initrd.gz

metalink=http://wubi-installer.org/metalinks/8.04/edubuntu-desktop-i386.iso.metalink

isoSize=

minIsoSize=600000000



[Edubuntu-amd64]

version=8.04

subversion=

isoName=

packages=edubuntu-desktop

kernel=casper/vmlinuz

initrd=casper/initrd.gz

metalink=http://wubi-installer.org/metalinks/8.04/edubuntu-desktop-amd64.iso.metalink

isoSize=

minIsoSize=600000000

[B][BossLinux-i386]

version=2.0

subversion=

isoName=

packages=anant

kernel=casper/vmlinuz

initrd=casper/initrd.gz

metalink=http://wubi-installer.org/metalinks/8.04/edubuntu-desktop-amd64.iso.metalink

isoSize=

minIsoSize=600000000

what to write in kernal? In boss website I found that
[/B][> ]("http://bosslinux.in/downloads/iso-images/ananth")[Anant]("http://bosslinux.in/downloads/iso-images/ananth")
BOSS version 2.0, with gnome 2.18 with  **kernel 2.6.21-1-486** is the latest version of BOSS GNU/Linux
**What to write in initrd?**
[B]In boss site I could not found metalink of boss.
[/B]

---

### Post by ago on 2008-02-20
The 2 lines stay the same but...

This version of Wubi only works with Ubuntu 8.04 derivatives, the kernel above is an old version which indicates an onld distro spin off...

So unless the chaps at BOSS provide an 8.04 Live CD you will not be able to use Wubi

---

