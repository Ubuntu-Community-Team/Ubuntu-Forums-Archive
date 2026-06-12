---
title: "I can't reinstall or remove MoBlock"
date: 2007-12-15
forum: General Help
---

### Post by bpont on 2007-12-15
```
$ sudo apt-get install --reinstall moblock-nfq
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  moblock-nfq
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/43.2kB of archives.
After unpacking 0B of additional disk space will be used.
(Reading database ... 177940 files and directories currently installed.)
Preparing to replace moblock-nfq 0.8-32+gutsy (using .../moblock-nfq_0.8-35+gutsy_i386.deb) ...
 * MoBlock: /etc/moblock/moblock.conf not installed.
invoke-rc.d: initscript moblock-nfq, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 6
dpkg - trying script from the new package instead ...
 * MoBlock: /etc/moblock/moblock.conf not installed.
invoke-rc.d: initscript moblock-nfq, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/moblock-nfq_0.8-35+gutsy_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 6
 * MoBlock: /etc/moblock/moblock.conf not installed.
invoke-rc.d: initscript moblock-nfq, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 6
Errors were encountered while processing:
 /var/cache/apt/archives/moblock-nfq_0.8-35+gutsy_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

```
sudo apt-get remove  moblock-nfq
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnfnetlink0 libnetfilter-queue1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  moblock-nfq
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 225kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing moblock-nfq (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 moblock-nfq
E: Sub-process /usr/bin/dpkg returned an error code (1)
dhamma@white-tara:~$ sudo apt-get install --reinstall moblock-nfq
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  moblock-nfq
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/43.2kB of archives.
After unpacking 0B of additional disk space will be used.
Selecting previously deselected package moblock-nfq.
(Reading database ... 177940 files and directories currently installed.)
Preparing to replace moblock-nfq 0.8-32+gutsy (using .../moblock-nfq_0.8-35+gutsy_i386.deb) ...
 * MoBlock: /etc/moblock/moblock.conf not installed.
invoke-rc.d: initscript moblock-nfq, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 6
dpkg - trying script from the new package instead ...
 * MoBlock: /etc/moblock/moblock.conf not installed.
invoke-rc.d: initscript moblock-nfq, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/moblock-nfq_0.8-35+gutsy_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 6
 * MoBlock: /etc/moblock/moblock.conf not installed.
invoke-rc.d: initscript moblock-nfq, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 6
Errors were encountered while processing:
 /var/cache/apt/archives/moblock-nfq_0.8-35+gutsy_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Krusader3z on 2007-12-15
I used the command line to install MoBlock, then when I wanted to uninstall it, I had no luck.

So what i did is go into Synaptic Package Manager (System- Administration)
and I ran a search for "moblock"

It found two results, one was marked as already installed, so i marked it to "remove completely" and it was gone.

---

### Post by bpont on 2007-12-21
> **Krusader3z said:**
> I used the command line to install MoBlock, then when I wanted to uninstall it, I had no luck.

So what i did is go into Synaptic Package Manager (System- Administration)
and I ran a search for "moblock"

It found two results, one was marked as already installed, so i marked it to "remove completely" and it was gone.

I followed your advice, but it still won't work...there seems to be absolutely no way to either remove or reinstall this package and now it interferes with every system update because apt-get wants to install an update that can't be unchecked in 'other updates' in update manager.

](*,)

---

### Post by jre on 2007-12-21
```
aptitude purge moblock-nfq
```

It seems as if you have deleted your moblock.conf. So if the above command doesn´t work, you can  first copy it there manually: (i´m not under Linux ATM so I can´t verify the correct pathnames)
```

dpkg -X /var/cache/apt/archives/moblock-nfq_0.8-35+gutsy_i386.deb /home/{YOURLOGIN}/somefoldername
sudo cp /home/{YOURLOGIN}/somefoldername/etc/moblock/moblock.conf /etc/moblock/moblock.conf
```

All MoBlock problems should be solved in 0.8-39

greets
jre

---

### Post by breaking on 2008-01-12
[https://answers.launchpad.net/synaptic/+question/8337](https://answers.launchpad.net/synaptic/+question/8337)

the above page has an alternative to reinstall moblock.

i had problems where it asked me to reinstall moblock but it couldn't find a package.

after visiting the above site, i deleted the entire moblock entry and now i can reinstall it and get synaptics to work again.

---

### Post by lil_malcolmx2 on 2008-02-18
I had the exact same problem yesterday!!
I figured out a solution though

Make sure you backup your moblock-control first!
```
sudo gedit /usr/bin/moblock-control
```
 
clear all the txt 
and save.

now try to reinstall 

hope it works for you

---

### Post by jackmc on 2008-06-11
> **lil_malcolmx2 said:**
> I had the exact same problem yesterday!!
I figured out a solution though

Make sure you backup your moblock-control first!
```
sudo gedit /usr/bin/moblock-control
```
 
clear all the txt 
and save.

now try to reinstall 

hope it works for you

Thanks, worked for me :)

---

