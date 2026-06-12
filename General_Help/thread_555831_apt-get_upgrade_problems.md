---
title: "apt-get upgrade problems"
date: 2007-09-20
forum: General Help
---

### Post by Sico on 2007-09-20
Here is what happens:

```
Fetched 99.2MB in 7m32s (219kB/s)                                                                                           
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/tar_1.16-2ubuntu0.1_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `gnome-applets-data': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/tar_1.16-2ubuntu0.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
sico@sico-desktop:~$ 

```

Here is the output for aptitude:

```
90 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/196MB of archives. After unpacking 3850kB will be used.
Do you want to continue? [Y/n/?] y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/tar_1.16-2ubuntu0.1_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `gnome-applets-data': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/tar_1.16-2ubuntu0.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

I have tried the following.  
apt-get clean -y
apt-get autoclean -y
apt-get install (ANYTHING) reports:

```
sico@sico-desktop:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  liboggflac3 libsamplerate0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  firefox-gnome-support
Suggested packages:
  latex-xft-fonts firefox-libthai
The following packages will be upgraded:
  firefox firefox-gnome-support
2 upgraded, 0 newly installed, 0 to remove and 88 not upgraded.
Need to get 0B/9349kB of archives.
After unpacking, 77.8kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing /var/cache/apt/archives/firefox-gnome-support_2.0.0.6+1-0ubuntu1_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `gnome-applets-data': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/firefox-gnome-support_2.0.0.6+1-0ubuntu1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
sico@sico-desktop:~$
```


Also firefox no long starts for me.  There is no error when ran from the console.  it shows up on the panel and says it is starting but after a few seconds it disappears.  I am using wine and firefox from a windows partition to type this now. Everything else "seems" to be working normally.  Please help me.

---

### Post by kelbizzle on 2007-09-20
Try passing it with this. I found this in "man apt-get"

```
   -f, --fix-broken
          Fix; attempt to correct a system with broken dependencies in place.
          This option, when used with install/remove, can omit any packages to
          permit APT to deduce a likely solution. Any Package that are
          specified must completely correct the problem. The option is
          sometimes necessary when running APT for the first time; APT itself
          does not allow broken package dependencies to exist on a system. It
          is possible that a system’s dependency structure can be so corrupt
          as to require manual intervention (which usually means using
          dselect(8) or dpkg --remove to eliminate some of the offending
          packages). Use of this option together with -m may produce an error
          in some situations. Configuration Item: APT::Get::Fix-Broken.

```

---

### Post by Sico on 2007-09-28
Thanks, but that didn't work either.  I tried many things.  Didn't work.  So I ended up just doing a clean install.  Using 7.10 now.  Compiz locks on me and I have to use the failsafe gnome.  Works though :D

---

