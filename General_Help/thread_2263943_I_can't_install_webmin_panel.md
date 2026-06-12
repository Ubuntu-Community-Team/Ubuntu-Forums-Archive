---
title: "I can't install webmin panel"
date: 2015-02-04
forum: General Help
---

### Post by peter1897 on 2015-02-04
I have installed Ubuntu server 12.04.5 on Virtualbox and i am trying to install webmin but i am getting this output when i run **aptidude install webmin**

```
root@ubuntu:/# aptitude install webmin
The following NEW packages will be installed:
  webmin{b}
0 packages upgraded, 1 newly installed, 0 to remove and 66 not upgraded.
Need to get 21.8 MB of archives. After unpacking 140 MB will be used.
The following packages have unmet dependencies:
 webmin : Depends: libnet-ssleay-perl which is a virtual package.
          Depends: libauthen-pam-perl which is a virtual package.
          Depends: libio-pty-perl which is a virtual package.
          Depends: apt-show-versions which is a virtual package.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     webmin [Not Installed]
```

If i try to install the dependecies one by one i get this:

```
root@ubuntu:/# aptitude install libnet-ssleay-perl
No candidate version found for libnet-ssleay-perl
No candidate version found for libnet-ssleay-perl
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 66 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
```

How to solve this problem?

---

### Post by dragonfly41 on 2015-02-04
There is no need to install the dependencies one by one .. webmin installation should do that for you.

I have webmin running on localhost Ubuntu 14.04.

---

### Post by peter1897 on 2015-02-04
Webmin installation doesn't do that for me. This is the actual problem i have.

---

### Post by dragonfly41 on 2015-02-04
Sorry .. I missed the point that you want to install on VirtualBox .. my webmin is on the host .. not on VirtualBox VM.

Perhaps this might help ...

[http://automation.binarysage.net/?p=910](http://automation.binarysage.net/?p=910)


Install Webmin
Although WebMin has no GUI for VirtualBox, it is very useful to have  this installed on the hosting VM for maintenance work of the host.

You can install WebMin by [adding it to the APT repository and installing]("http://automation.binarysage.net/?p=750").


[http://automation.binarysage.net/?p=750](http://automation.binarysage.net/?p=750)

If you like to install and update Webmin via APT, you will need edit the /etc/apt/sources.list file on your system with the command, as root:

vi /etc/apt/sources.list


p.s. You will need to open ports 10000 (for webmin) 5000 (for usermin) and 80.

---

### Post by peter1897 on 2015-02-04
My Host OS is Windows 7 and my guest VM is Ubuntu Server 12.04. I already have edited the sources.list file and added the webmin repository but still getting the message for missing dependencies when i try to install it. And i am getting this message for almost any package i try to install like:

aptitude install dkms
aptitude install build-essential
aptitude install nmap

I also tried to install Ajenti panel but i get similar problem.

---

### Post by dragonfly41 on 2015-02-04
I'm out of my depth discussing Virtual Box on Windows 7. 
I dropped using Windows some time ago (although I still keep dormant installations of XP and Vista).

You say that you can't install other apps such as Ajenti .. which gives a clue that the problem is not just in webmin.

One thought .. have you installed Virtual Box Guest Additions?

Perhaps browse the virtualbox forum for more clues.

...

---

### Post by peter1897 on 2015-02-04
I am not able to install the guest additions also. This is the output i get:

```
root@ubuntu:/mnt# ./VBoxLinuxAdditions.run
Verifying archive integrity... All good.
Uncompressing VirtualBox 4.3.20 Guest Additions for Linux............
VirtualBox Guest Additions installer
Removing installed version 4.3.20 of VirtualBox Guest Additions...
Copying additional installer modules ...
Installing additional modules ...
Removing existing VirtualBox non-DKMS kernel modules ...done.
Building the VirtualBox Guest Additions kernel modules
The make utility was not found. If the following module compilation fails then
this could be the reason and you should try installing it.

The gcc utility was not found. If the following module compilation fails then
this could be the reason and you should try installing it.

Building the main Guest Additions module ...fail!
(Look at /var/log/vboxadd-install.log to find out what went wrong)
Doing non-kernel setup of the Guest Additions ...done.
Installing the Window System drivers
Could not find the X.Org or XFree86 Window System, skipping.
```

---

### Post by dragonfly41 on 2015-02-04
o.k. .. look here ..

[http://ubuntuforums.org/showthread.php?t=1812472](http://ubuntuforums.org/showthread.php?t=1812472)

install "make" and "gcc"

See more here ...

[https://forums.virtualbox.org/viewtopic.php?f=3&t=45713](https://forums.virtualbox.org/viewtopic.php?f=3&t=45713)

---

### Post by mastablasta on 2015-02-05
what happens if you try apt-get install instead of aptitude?

apt-get update
apt get upgrade

then 

apt-get install webmin

guest additons have nothing to do with this.

---

### Post by peter1897 on 2015-02-05
I run **apt-get update** and **apt get upgrade** but this didn't help.
When i try to install webmin i get this output:

```
root@ubuntu:/# apt-get install webmin
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 webmin : Depends: libnet-ssleay-perl but it is not installable
          Depends: libauthen-pam-perl but it is not installable
          Depends: libio-pty-perl but it is not installable
          Depends: apt-show-versions but it is not installable
E: Unable to correct problems, you have held broken packages.
```


Also when i run **apt-get update** at the end i got this:

```
Fetched 2,898 kB in 59s (49.0 kB/s)
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_main_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_restricted_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_universe_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.


```

---

### Post by dragonfly41 on 2015-02-05
Methinks it is as simple as using root permissions to install

i.e. use **sudo** prefix .. sudo apt-get install webmin

[http://ubuntuforums.org/showthread.php?t=1639893](http://ubuntuforums.org/showthread.php?t=1639893)

and before installation make sure that perl is preinstalled

---

### Post by peter1897 on 2015-02-05
I am logged as root so i don't think the sudo prefix is the problem. And i don't have problem only with webmin, i can't install any packages. I get this error when i try to install a package:  E: Unable to correct problems, you have held broken packages.

---

### Post by peter1897 on 2015-02-06
I don't know why but the problem seems to be with the Ubuntu server 12.04.5 release. I installed an older release 10.04.4 on a new virtual machine and now i don't have problem with installing packages.

---

### Post by dragonfly41 on 2015-02-06
These threads advise that you use the command

sudo apt-get **[COLOR=#ff0000]-f[/COLOR]** install 

[http://howtofindsolution.blogspot.co.uk/2013/02/how-to-install-webmin-on-ubuntu-server.html](http://howtofindsolution.blogspot.co.uk/2013/02/how-to-install-webmin-on-ubuntu-server.html)

[http://ubuntuforums.org/showthread.php?t=1639893](http://ubuntuforums.org/showthread.php?t=1639893)

---

### Post by peter1897 on 2015-02-07
I tried **apt-get -f install** but it didn't help. Anyway i was able to install webmin on ubuntu 10.04.4 but i can't upgrade to newer ubuntu release. Maybe the hardware of my laptop doesn't support the new releases.

---

### Post by dragonfly41 on 2015-02-07
> Maybe the hardware of my laptop doesn't support the new releases.

I can't comment on that theory since you don't give a spec of your laptop.

For example I'm running Ubuntu 14.04 and Webmin on an ancient Dell Inspiron 1720 laptop.

See the sticky threads on "old hardware".

I would push the boat out further and try installing Ubuntu 14.04 .. you can always try in LiveUSB mode 
and even install webmin on LiveUSB session .. just to test if it flies.

---

