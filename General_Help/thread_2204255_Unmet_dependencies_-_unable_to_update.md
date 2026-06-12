---
title: "Unmet dependencies - unable to update"
date: 2014-02-07
forum: General Help
---

### Post by s-grabowski on 2014-02-07
Would anyone be able to shed light on this problem that I currently have. I think it boils down to a comflict between the official Intel Graphics Installer and the drivers I one installed from [https://launchpad.net/~oibaf/+archive/graphics-drivers](https://launchpad.net/~oibaf/+archive/graphics-drivers)

I'm now stuck where I am unable to follow the advice to install ppa-purge, because ubuntu wants me to execute apt-get install -f, which always fails because of the issue seen below:

```

stefan@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libllvm3.3 libllvm3.3:i386 libxtst6:i386 linux-image-3.11.0-12-generic
  linux-image-3.8.0-32-generic linux-image-extra-3.11.0-12-generic
  linux-image-extra-3.8.0-32-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libegl1-mesa-drivers libgl1-mesa-dri
Suggested packages:
  libglide3
The following packages will be upgraded:
  libegl1-mesa-drivers libgl1-mesa-dri
2 upgraded, 0 newly installed, 0 to remove and 30 not upgraded.
1 not fully installed or removed.
Need to get 0 B/9,769 kB of archives.
After this operation, 9,917 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 275599 files and directories currently installed.)
Preparing to replace libgl1-mesa-dri:amd64 10.1~git1401311930.606544+curaga~gd~s (using .../libgl1-mesa-dri_10.2~git1402070730.020c43~gd~s_amd64.deb) ...
Unpacking replacement libgl1-mesa-dri:amd64 ...
dpkg: error processing /var/cache/apt/archives/libgl1-mesa-dri_10.2~git1402070730.020c43~gd~s_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/dri-alternates/i915_dri.so', which is also in package libgl1-mesa-dri-experimental:amd64 10.1~git1401311930.606544+curaga~gd~s
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
dpkg: regarding .../libegl1-mesa-drivers_10.2~git1402070730.020c43~gd~s_amd64.deb containing libegl1-mesa-drivers:amd64:
 libegl1-mesa-drivers:amd64 conflicts with libgl1-mesa-dri (<= 10.1~git1402021930.81144c+curaga~gd~s)
  libgl1-mesa-dri:amd64 (version 10.1~git1401311930.606544+curaga~gd~s) is present and installed.


dpkg: error processing /var/cache/apt/archives/libegl1-mesa-drivers_10.2~git1402070730.020c43~gd~s_amd64.deb (--unpack):
 conflicting packages - not installing libegl1-mesa-drivers:amd64
Errors were encountered while processing:
 /var/cache/apt/archives/libgl1-mesa-dri_10.2~git1402070730.020c43~gd~s_amd64.deb
 /var/cache/apt/archives/libegl1-mesa-drivers_10.2~git1402070730.020c43~gd~s_amd64.deb



```


Can anyone recommend how to remove either of the drivers, or both of the drivers, and the appropriate set up that you'd recommend?

Also, does anyone know of a fix for stuttering sound with[FONT=arial][SIZE=2] Realtek ALC892 - an 'unknown' item in the sound settings menu appears when playing music?[/SIZE][/FONT]

---

### Post by TheFu on 2014-02-07
Try **sudo aptitude -f install**
Aptitude is smarter about dependencies and will over different options to solve them.

---

### Post by jeanjd63 on 2014-02-08
Hello

You can try :
**sudo  dpkg  -i  --force-all  **[COLOR=#000000][FONT=Ubuntu Mono]**/var/cache/apt/archives/libgl1-mesa-dri_10.2~git1402070730.020c43~gd~s_amd64.deb**

And if it's good, you do :
[B]sudo  apt-get  install -f
sudo  apt-get  update
sudo  apt-get  autoremove -y
sudo  apt-get  upgrade[/B][/FONT][/COLOR]

---

### Post by s-grabowski on 2014-02-08
Thank you to both of you for your help. For some reason I didn't have aptitude installed (and then couldn't install for the above reason). But following your instructions [COLOR=#000000]jeanjd63 worked perfectly. Thanks again - you saved me having to fresh install :)[/COLOR]

---

### Post by jeanjd63 on 2014-02-08
May be Solved ?

---

