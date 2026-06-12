---
title: "Package installation problem, i386 message"
date: 2007-02-19
forum: General Help
---

### Post by bigfootx2 on 2007-02-19
I cannot install software I need.

Using add/remove hardware, I get this message:
AbiWord Word Processor cannot be installed on your computer type (i386)

There is a similar message for other listed packages that I tried. My processor is a P3 mobile, and I wonder if it has been incorrectly identified.

When I use sudo apt-get install abiword, the result is:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package abiword

I don't know what this means. Can anyone help?

---

### Post by gradedcheese on 2007-02-19
try and update first:

sudo apt-get update
sudo apt-get install abiword

...perhaps your repositories list never got downloaded yet?

---

### Post by bigfootx2 on 2007-02-19
There's a list of software available, and I assumed this indicated reposotory packages were available.

However, the update request doesn't work, it times out trying to connect to servers
[http://au.archive.com](http://au.archive.com) & [http://security](http://security) ubuntu.com

Is there another way around this please?

---

### Post by gradedcheese on 2007-02-19
Are you using 6.10 (edgy)?  If so, compare your /etc/apt/sources.list file with the one shown here:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

Take out any extraneous repositories.

---

### Post by bigfootx2 on 2007-02-21
That works, and also it all makes sense now. Thanks for your help.

---

