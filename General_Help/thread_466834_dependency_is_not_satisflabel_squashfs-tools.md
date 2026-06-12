---
title: "dependency is not satisflabel: squashfs-tools"
date: 2007-06-07
forum: General Help
---

### Post by Sir P on 2007-06-07
hi all,

Trying to install reconstructor, and also tried UCK however keep getting the error message "dependency is not satisflabel: squashfs-tools" and it will not install.

Tried apt-get install squashfs-tools (aswell as just squash)
but no such luck, i found online squashfs is a read only file system ?

Can anyone help me here, what does the error mean and how to resolve?

many thanks
Sir P :D

---

### Post by pbw on 2007-06-07
what version of squshfs-tools is it requiring when the error pops up?

It'd help if you could paste the exact message apt spits out instead of paraphrasing.

---

### Post by Sir P on 2007-06-07
hello

thanks for your reply.

Doesnt show a version and that was the exact message.... its from GUI btw...
> Error: Dependency is not satisflabel: squashfs-tools

many thanks

---

### Post by pbw on 2007-06-07
Use the terminal please, it should give you a more detailed error message there.

---

### Post by Sir P on 2007-06-07
ok thanks will do... not sure how to use apt-get to install local packages though...when i try apt-get install /path/to/package.deb though it tells me it cant find the package....

any ideas?

many thanks

---

### Post by pbw on 2007-06-07
You use dpkg.. squashfs-tools is in main repo though. If the local one doesn't install, then it doesn't make sense to use it..

either
```

sudo apt-get clean

```
To clean you cache.

Or 
```

sudo rm /var/cache/apt/archives/squashfs*

```
To remove the cached squash deb.

Then```

sudo apt-get install squashfs-tools

```
To install it from the repo, and you should be good. As said before though, paste any errors if this doesn't work out.

-- pbw

---

### Post by Sir P on 2007-06-07
Thanks for your ongoing help pdw, i cleaned the cache and then tried to grab squashfs.. gave me the following error... cheers :)

> root@james-desktop:~/Desktop# apt-get install squashfs-tools
Reading package lists... Done
Building dependency tree... Done
Package squashfs-tools is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package squashfs-tools has no installation candidate


---

### Post by pbw on 2007-06-07
No problem.. That's weird though, it's in main repository. What version of *buntu are you running?

Popped over to my feisty installation and..
```

$ pi squashfs-tools
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  squashfs-source
The following NEW packages will be installed:
  squashfs-tools
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 93.8kB of archives.
After unpacking, 283kB of additional disk space will be used.
Get:1 http://ca.archive.ubuntu.com feisty/main squashfs-tools 1:3.1r2-6 [93.8kB]
Fetched 93.8kB in 0s (160kB/s)

```

Seems fine to install on my end.

Try this if you're running feisty..
```

wget http://mirrors.kernel.org/ubuntu/pool/main/s/squashfs/squashfs-tools_3.1r2-6_i386.deb
sudo dpkg -i squashfs-tools_3.1r2-6_i386.deb

```

---

### Post by Sir P on 2007-06-08
how strange..

im on ubuntu 6.06 desktop

i tried your above instructions and got ...
> james@james-desktop:~$ sudo dpkg -i squashfs-tools_3.1r2-6_i386.deb
Password:
Selecting previously deselected package squashfs-tools.
(Reading database ... 72845 files and directories currently installed.)
Unpacking squashfs-tools (from squashfs-tools_3.1r2-6_i386.deb) ...
dpkg: dependency problems prevent configuration of squashfs-tools:
 squashfs-tools depends on libc6 (>= 2.5-0ubuntu1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.4.
dpkg: error processing squashfs-tools (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 squashfs-tools


ANy ideas?
many thanks for your time

---

