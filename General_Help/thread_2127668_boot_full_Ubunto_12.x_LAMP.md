---
title: "/boot full Ubunto 12.x LAMP"
date: 2013-03-20
forum: General Help
---

### Post by DoubelD on 2013-03-20
I searched and serached for /boot full 
I tried a few suggestion and nothing works
I'm running a server so there is NO GUI and even if I wanted to install one apt-get fails every time ! 
To my knowledge **synaptic** is not installed in this server 

[COLOR=#0000FF]
[FONT=courier new]Filesystem               Size  Used Avail Use% Mounted on
/dev/mapper/WWW-root  145G  3.5G  134G   3% /
udev                     983M  4.0K  983M   1% /dev
tmpfs                    396M  316K  396M   1% /run
none                     5.0M     0  5.0M   0% /run/lock
none                     990M     0  990M   0% /run/shm
/dev/sda1                228M  225M     0 100% /boo[/FONT]t

root@WWW:~# uname -a
Linux WWW 3.2.0-36-generic-pae #57-Ubuntu SMP Tue Jan 8 22:01:06 UTC 2013 i686 i686 i386 GNU/Linux

root@WWW:~# uname -r
3.2.0-36-generic-pae
root@WWW:~#[/COLOR]





I issued the following and here's what I received 

dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge


[COLOR=#0000FF]root@WWW:~# dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge

[/COLOR][FONT=courier new][COLOR=#0000FF]Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-3.2.0-36-generic-pae : Depends: linux-headers-3.2.0-36 but it is not going to be installed
 linux-image-generic-pae : Depends: linux-image-3.2.0-37-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[/COLOR]
[/FONT]
Seeing the "Try 'apt-get -f  install' I try it and after a while I get 


[COLOR=#0000FF][FONT=courier new]root@WWW:~# apt-get -f install

Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-36-generic-pae linux-headers-3.2.0-36
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-generic-pae linux-headers-3.2.0-38 linux-headers-3.2.0-38-generic-pae linux-headers-generic-pae
  linux-image-3.2.0-38-generic-pae linux-image-generic-pae
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed:
  linux-headers-3.2.0-38 linux-headers-3.2.0-38-generic-pae linux-image-3.2.0-38-generic-pae
The following packages will be upgraded:
  linux-generic-pae linux-headers-generic-pae linux-image-generic-pae
3 upgraded, 3 newly installed, 0 to remove and 73 not upgraded.
5 not fully installed or removed.
Need to get 50.9 MB of archives.
After this operation, 181 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-image-3.2.0-38-generic-pae i386 3.2.0-38.61 [38.2 MB]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-generic-pae i386 3.2.0.38.46
  404  Not Found [IP: 91.189.91.14 80]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-3.2.0-38 all 3.2.0-38.61 [11.7 MB]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main linux-generic-pae i386 3.2.0.38.46
  404  Not Found [IP: 91.189.92.200 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main linux-image-generic-pae i386 3.2.0.38.46
  404  Not Found [IP: 91.189.92.200 80]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-3.2.0-38-generic-pae i386 3.2.0-38.61 [981 kB]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-generic-pae i386 3.2.0.38.46
  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main linux-headers-generic-pae i386 3.2.0.38.46
  404  Not Found [IP: 91.189.91.13 80]
Fetched 50.9 MB in 5min 22s (158 kB/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic-pae_3.2.0.38.46_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic-pae_3.2.0.38.46_i386.deb)  404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic-pae_3.2.0.38.46_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic-pae_3.2.0.38.46_i386.deb)  404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic-pae_3.2.0.38.46_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic-pae_3.2.0.38.46_i386.deb)  404  Not Found [IP: 91.189.91.13 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
[/FONT][/COLOR]


Uggggggh this is getting so annoying now it can't find files - Its a clonezilla image I dump to a test box - Try a bunch of things an dif it goes all wrong I start again 


I tried the auto remove and no go 

[FONT=courier new][COLOR=#0000FF]root@WWW:~# apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic-pae : Depends: linux-image-3.2.0-37-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.
[/COLOR][/FONT]

So I do the -f 


[FONT=courier new][COLOR=#0000FF]root@WWW:~# apt-get autoremove -f

Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-generic-pae linux-headers-3.2.0-38 linux-headers-3.2.0-38-generic-pae linux-headers-generic-pae
  linux-image-3.2.0-38-generic-pae linux-image-generic-pae
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following packages will be REMOVED:
  linux-headers-3.2.0-36 linux-headers-3.2.0-36-generic-pae
The following NEW packages will be installed:
  linux-headers-3.2.0-38 linux-headers-3.2.0-38-generic-pae linux-image-3.2.0-38-generic-pae
The following packages will be upgraded:
  linux-generic-pae linux-headers-generic-pae linux-image-generic-pae
3 upgraded, 3 newly installed, 2 to remove and 73 not upgraded.
5 not fully installed or removed.
Need to get 6,946 B/50.9 MB of archives.
After this operation, 113 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-generic-pae i386 3.2.0.38.46
  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main linux-generic-pae i386 3.2.0.38.46
  404  Not Found [IP: 91.189.91.13 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main linux-image-generic-pae i386 3.2.0.38.46
  404  Not Found [IP: 91.189.91.13 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main linux-headers-generic-pae i386 3.2.0.38.46
  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic-pae_3.2.0.38.46_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic-pae_3.2.0.38.46_i386.deb)  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic-pae_3.2.0.38.46_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic-pae_3.2.0.38.46_i386.deb)  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic-pae_3.2.0.38.46_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic-pae_3.2.0.38.46_i386.deb)  404  Not Found [IP: 91.189.91.13 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
[/COLOR][/FONT]
Uggggggh still no connection 


Any suggestions since this is a catch 22 I don;t have space yet I need files what do I do

---

### Post by Bashing-om on 2013-03-20
DoubelD;

If you are certain that your /boot is at capacity: Here is schragge's solution:
```
 sudo apt-get purge linux-image-{[0-9],`uname -r`+,`readlink /vmlinuz.old|cut -d- -f2-`+} 
```
This code retains the 2 latest kernels and removes the rest.[INDENT=2]hope this helps

[/INDENT]

---

### Post by schragge on 2013-03-21
Sadly, this probably won't work if the package management system is in an unclean state (i.e. you've got some half-installed packages). You probably should clean the old kernels with dpkg then. First, look at the output of
```
dpkg-query -Wf'${db:Status-Abbrev}${binary:Package}\n' linux-\*|sed -n 's/^i..//p'
``` and decide what packages you are going to remove. Then remove them with
```
sudo dpkg -P linux-{image,headers}-3.2.0-{[COLOR=red]33,34[/COLOR]}-generic{,-pae}
``` Replace [COLOR=red]33,34[/COLOR] with versions you want to delete. This probably will be the easiest method if you only have a handful of them.

The sed expression from your post looks pretty complex, so if you're proficient in sed and there are many kernels, you can try to automate the procedure. I'd probably do it in small steps, adding to the expression above and checking each time if you're getting what you want. E.g. to get only installed linux-headers-*/linux-image-* packages, excluding the current kernel, I'd modify the expression above like this:
```
dpkg-query -Wf'${db:Status-Abbrev}${binary:Package}\n' linux-\*|sed -r '/^i...*(-image-|-headers-)[0-9]/!d;/'"`uname -r`"'/d;s/^...//'
```
When you're sure the output contains only the packages you're going to remove,  [COLOR=blue]feed it to *dpkg --set-selections*[/COLOR]:
```
dpkg-query -Wf'${db:Status-Abbrev}${binary:Package}\n' linux-\*|sed -r '/^i...*(-image-|-headers-)[0-9]/!d;/'"`uname -r`"'/d;s/^...//'[COLOR=blue]|xargs -I@ echo @ purge|sudo dpkg --set-selections[/COLOR]
```
Check if all the packages you want were marked for purge:
```
dpkg --get-selections|grep purge$
``` then proceed to actually purge them
```
sudo dpkg -Pa
```

---

### Post by DoubelD on 2013-03-21
> **Bashing-om said:**
> DoubelD;

If you are certain that your /boot is at capacity: Here is schragge's solution:
```
 sudo apt-get purge linux-image-{[0-9],`uname -r`+,`readlink /vmlinuz.old|cut -d- -f2-`+} 
```
This code retains the 2 latest kernels and removes the rest.[INDENT=2]hope this helps

[/INDENT]


This did not work  


[COLOR=#0000FF][FONT=courier new]root@WWW:~# apt-get purge linux-image-{[0-9],`uname -r`+,`readlink /vmlinuz.old|cut -d- -f2-`+}


Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting 'linux-image-3.2.0-39-generic' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-34-generic-pae' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-29-generic-pae' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-1610-armadaxp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-1605-armadaxp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-1413-omap4' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-35-powerpc-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-33-powerpc64-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.5.0-26-generic' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-39-lowlatency' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-34-powerpc64-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-29-powerpc64-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-34-virtual' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-29-virtual' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-31-generic' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-26-generic' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.0.0-1007-linaro-vexpress' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.0.27-1-ac100' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-31-generic-pae' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-26-generic-pae' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-32-powerpc-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-27-powerpc-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-23-powerpc64-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-32-highbank' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-27-highbank' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-38-highbank' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-24-powerpc64-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-37-virtual' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-34-generic' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-29-generic' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-38-lowlatency' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-23-generic-pae' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-30-powerpc64-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-25-powerpc64-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-24-powerpc-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-1615-armadaxp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.5.0-21-generic' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-1425-omap4' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-24-virtual' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-38-generic-pae' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-39-powerpc-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-2.6.31-800-st1-5' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-37-generic' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-23-lowlatency-pae' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-1423-omap4' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-1418-omap4' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.5.0-24-generic' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.5.0-19-generic' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-2.4' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-2.6' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-31-highbank' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-26-highbank' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-37-lowlatency' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.0' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-37-highbank' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.0.0-1007-linaro-mx51' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-35-generic-pae' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-32-virtual' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-27-virtual' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-36-powerpc-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-24-generic' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-1603-armadaxp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-1614-armadaxp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-1609-armadaxp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-39-omap' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-37-omap' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-1421-omap4' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-1416-omap4' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-35-omap' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-32-generic-pae' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-27-generic-pae' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-33-powerpc-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-33-omap' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-35-virtual' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-32-generic' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-27-generic' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-31-omap' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-26-omap' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.0.0-1007-linaro-omap' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-24-omap' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-36-lowlatency' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-35-powerpc64-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-30-highbank' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-25-highbank' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-1414-omap4' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-36-highbank' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-24-generic-pae' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-36-powerpc64-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-30-powerpc-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-25-powerpc-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-1602-armadaxp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-37-powerpc64-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-1613-armadaxp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-1608-armadaxp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-38-virtual' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-35-generic' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-39-generic-pae' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-2.6.35-1-n900' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-23-lowlatency' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-39-lowlatency-pae' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.5.0-22-generic' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-1412-omap4' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-35-lowlatency-pae' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.1.1-1400-linaro-lt-mx5' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-35-lowlatency' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-30-virtual' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-25-virtual' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-31-powerpc64-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-26-powerpc64-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-2.6-rt' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-32-powerpc64-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-27-powerpc64-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-36-generic-pae' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-38-generic' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-37-powerpc-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-35-highbank' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-1426-omap4' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-38-lowlatency-pae' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.5.0-25-generic' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-1612-armadaxp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-1607-armadaxp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-33-virtual' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-30-generic' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-25-generic' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-33-generic-pae' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-34-powerpc-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-29-powerpc-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-1424-omap4' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-1419-omap4' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-37-lowlatency-pae' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-33-lowlatency-pae' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-30-generic-pae' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-25-generic-pae' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-36-virtual' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-33-generic' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-31-powerpc-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-26-powerpc-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-34-highbank' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-29-highbank' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-1422-omap4' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-1417-omap4' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-1611-armadaxp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-1606-armadaxp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-23-virtual' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-36-lowlatency-pae' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-33-lowlatency' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-38-omap' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-23-powerpc-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-36-omap' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-39-virtual' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-36-generic' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-34-omap' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-29-omap' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-32-omap' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-27-omap' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-38-powerpc64-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-1420-omap4' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-1415-omap4' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-37-generic-pae' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.5.0-23-generic' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.5.0-18-generic' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-38-powerpc-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-30-omap' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-25-omap' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-39-powerpc64-smp' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-31-virtual' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-26-virtual' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-23-omap' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-23-generic' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-33-highbank' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-39-highbank' for regex 'linux-image-[0-9]'
Package linux-image-3.2.0-23-generic is not installed, so not removed
Package linux-image-3.2.0-23-virtual is not installed, so not removed
Package linux-image-3.2.0-23-lowlatency is not installed, so not removed
Package linux-image-3.2.0-23-lowlatency-pae is not installed, so not removed
Package linux-image-3.2.0-24-generic is not installed, so not removed
Package linux-image-3.2.0-24-generic-pae is not installed, so not removed
Package linux-image-3.2.0-24-virtual is not installed, so not removed
Package linux-image-3.2.0-25-generic is not installed, so not removed
Package linux-image-3.2.0-25-generic-pae is not installed, so not removed
Package linux-image-3.2.0-25-virtual is not installed, so not removed
Package linux-image-3.2.0-26-generic is not installed, so not removed
Package linux-image-3.2.0-26-virtual is not installed, so not removed
Package linux-image-3.2.0-27-generic is not installed, so not removed
Package linux-image-3.2.0-27-virtual is not installed, so not removed
Package linux-image-3.2.0-29-generic is not installed, so not removed
Package linux-image-3.2.0-29-virtual is not installed, so not removed
Package linux-image-3.2.0-30-generic is not installed, so not removed
Package linux-image-3.2.0-30-generic-pae is not installed, so not removed
Package linux-image-3.2.0-30-virtual is not installed, so not removed
Package linux-image-3.2.0-31-generic is not installed, so not removed
Package linux-image-3.2.0-31-virtual is not installed, so not removed
Package linux-image-3.2.0-32-generic is not installed, so not removed
Package linux-image-3.2.0-32-virtual is not installed, so not removed
Package linux-image-3.2.0-33-generic is not installed, so not removed
Package linux-image-3.2.0-33-virtual is not installed, so not removed
Package linux-image-3.2.0-34-generic is not installed, so not removed
Package linux-image-3.2.0-34-virtual is not installed, so not removed
Package linux-image-3.2.0-35-generic is not installed, so not removed
Package linux-image-3.2.0-35-virtual is not installed, so not removed
Package linux-image-3.2.0-36-generic is not installed, so not removed
Package linux-image-3.2.0-36-virtual is not installed, so not removed
Package linux-image-3.2.0-37-generic is not installed, so not removed
Package linux-image-3.2.0-37-generic-pae is not installed, so not removed
Package linux-image-3.2.0-37-virtual is not installed, so not removed
Package linux-image-3.2.0-38-generic is not installed, so not removed
Package linux-image-3.2.0-38-generic-pae is not installed, so not removed
Package linux-image-3.2.0-38-virtual is not installed, so not removed
Package linux-image-3.2.0-39-generic is not installed, so not removed
Package linux-image-3.2.0-39-generic-pae is not installed, so not removed
Package linux-image-3.2.0-39-virtual is not installed, so not removed
Package linux-image-3.5.0-18-generic is not installed, so not removed
Package linux-image-3.5.0-19-generic is not installed, so not removed
Package linux-image-3.5.0-21-generic is not installed, so not removed
Package linux-image-3.5.0-22-generic is not installed, so not removed
Package linux-image-3.5.0-23-generic is not installed, so not removed
Package linux-image-3.5.0-24-generic is not installed, so not removed
Package linux-image-3.5.0-25-generic is not installed, so not removed
Package linux-image-3.5.0-26-generic is not installed, so not removed
Package linux-image-3.2.0-33-lowlatency is not installed, so not removed
Package linux-image-3.2.0-33-lowlatency-pae is not installed, so not removed
Package linux-image-3.2.0-35-lowlatency is not installed, so not removed
Package linux-image-3.2.0-35-lowlatency-pae is not installed, so not removed
Package linux-image-3.2.0-36-lowlatency is not installed, so not removed
Package linux-image-3.2.0-36-lowlatency-pae is not installed, so not removed
Package linux-image-3.2.0-37-lowlatency is not installed, so not removed
Package linux-image-3.2.0-37-lowlatency-pae is not installed, so not removed
Package linux-image-3.2.0-38-lowlatency is not installed, so not removed
Package linux-image-3.2.0-38-lowlatency-pae is not installed, so not removed
Package linux-image-3.2.0-39-lowlatency is not installed, so not removed
Package linux-image-3.2.0-39-lowlatency-pae is not installed, so not removed
linux-image-3.2.0-35-generic-pae is already the newest version.
linux-image-3.2.0-36-generic-pae is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-generic-pae : Depends: linux-image-3.2.0-37-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

root@WWW:~# df -h

Filesystem               Size  Used Avail Use% Mounted on
/dev/mapper/GDCWWW-root  145G  3.5G  134G   3% /
udev                     983M  4.0K  983M   1% /dev
tmpfs                    396M  316K  396M   1% /run
none                     5.0M     0  5.0M   0% /run/lock
none                     990M     0  990M   0% /run/shm
/dev/sda1                228M  225M     0 100% /boot[/FONT][/COLOR]

---

### Post by DoubelD on 2013-03-21
> **schragge said:**
> Sadly, this probably won't work if the package management system is in an unclean state (i.e. you've got some half-installed packages). You probably should clean the old kernels with dpkg then. First, look at the output of
```
dpkg-query -Wf'${db:Status-Abbrev}${binary:Package}\n' linux-\*|sed -n 's/^i..//p'
``` 


The above code did not return any information. I do not know sed don;t knwo too much about unix either but ... a dpkg-query -l show a buch of stuff but I think we  are looking for this 

```
ii  linux-firmware                     1.79.1                     Firmware for Linux kernel drivers
iU  linux-generic-pae                  3.2.0.37.44                Complete Generic Linux kernel
ii  linux-headers-3.2.0-36             3.2.0-36.57                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-36-generic-pae 3.2.0-36.57                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
iU  linux-headers-3.2.0-37             3.2.0-37.58                Header files related to Linux kernel version 3.2.0
iU  linux-headers-3.2.0-37-generic-pae 3.2.0-37.58                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
iU  linux-headers-generic-pae          3.2.0.37.44                Generic Linux kernel headers
ii  linux-image-3.2.0-23-generic-pae   3.2.0-23.36                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-26-generic-pae   3.2.0-26.41                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-27-generic-pae   3.2.0-27.43                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-29-generic-pae   3.2.0-29.46                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-31-generic-pae   3.2.0-31.50                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-32-generic-pae   3.2.0-32.51                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-33-generic-pae   3.2.0-33.52                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-34-generic-pae   3.2.0-34.53                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-35-generic-pae   3.2.0-35.55                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-36-generic-pae   3.2.0-36.57                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
iU  linux-image-generic-pae            3.2.0.37.44                Generic Linux kernel image

```



> **schragge said:**
> and decide what packages you are going to remove. Then remove them with
```
sudo dpkg -P linux-{image,headers}-3.2.0-{[COLOR=red]33,34[/COLOR]}-generic{,-pae}
``` Replace [COLOR=red]33,34[/COLOR] with versions you want to delete. This probably will be the easiest method if you only have a handful of them.

The sed expression from your post looks pretty complex, so if you're proficient in sed and there are many kernels, you can try to automate the procedure. I'd probably do it in small steps, adding to the expression above and checking each time if you're getting what you want. E.g. to get only installed linux-headers-*/linux-image-* packages, excluding the current kernel, I'd modify the expression above like this:
```
dpkg-query -Wf'${db:Status-Abbrev}${binary:Package}\n' linux-\*|sed -r '/^i...*(-image-|-headers-)[0-9]/!d;/'"`uname -r`"'/d;s/^...//'
```
When you're sure the output contains only the packages you're going to remove,  [COLOR=blue]feed it to *dpkg --set-selections*[/COLOR]:
```
dpkg-query -Wf'${db:Status-Abbrev}${binary:Package}\n' linux-\*|sed -r '/^i...*(-image-|-headers-)[0-9]/!d;/'"`uname -r`"'/d;s/^...//'[COLOR=blue]|xargs -I@ echo @ purge|sudo dpkg --set-selections[/COLOR]
```
Check if all the packages you want were marked for purge:
```
dpkg --get-selections|grep purge$
``` then proceed to actually purge them
```
sudo dpkg -Pa
```

---

### Post by schragge on 2013-03-21
Ok, then try this
```

sudo dpkg -P linux-image-3.2.0-{23,26,27,29,31,32,33,34}-generic-pae
sudo apt-get clean
sudo apt-get -f install

```

---

### Post by DoubelD on 2013-03-21
OK that removed a bunch of stuff 
I then issued a apt-get update and an apt-get upgrade  (so I can be current)  <=== Not sure this is the right way to stay current 

I get an error 

```
root@WWW:~# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic-pae : Depends: linux-image-3.2.0-37-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.

```

Should I do the apt-get -f install ??

---

### Post by DoubelD on 2013-03-21
Oops 


I didn't see the apt-get clean and yje apt-het -f install that you TOLD me to try 

Working on multiple things and I missed it ](*,)

Sorry for jumping the gun - Doing the last two lines now 




> **DoubelD said:**
> OK that removed a bunch of stuff 
I then issued a apt-get update and an apt-get upgrade  (so I can be current)  <=== Not sure this is the right way to stay current 

I get an error 

```
root@WWW:~# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic-pae : Depends: linux-image-3.2.0-37-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.

```

Should I do the apt-get -f install ??

---

### Post by schragge on 2013-03-21
> **DoubelD said:**
> The above code did not return any information.How interesting. The *${db:Status-Abbrev}* field first appeared in dpkg 1.16.2 released in March 2012, from the kernel versions you use I'd guess you're running *precise* (Ubuntu 12.04), and I would think this change landed just in time for *precise* to include it. Can somebody confirm the code above doesn't work in *precise*?

[highlight]Update.[/highlight]
Oh now I see. According to [uwiki]PrecisePangolin/ReleaseSchedule[/uwiki] [uwiki]DebianImportFreeze[/uwiki] in that cycle was on January 12th. So, *precise* still uses [dpkg 1.16.1.2]("http://packages.ubuntu.com/precise-updates/dpkg").

---

### Post by DoubelD on 2013-03-21
> **schragge said:**
> How interesting. The *${db:Status-Abbrev}* field first appeared in dpkg 1.16.2 released in March 2012, from the kernel versions you use I'd guess you're running *precise* (Ubuntu 12.04), and I would think this change landed just in time for *precise* to include it. Can somebody confirm the code above doesn't work in *precise*?


Bummer the apt-get -f install ran into an error (**Package linux-image-3.2.0-37-generic-pae is not installed.) **see bold text

```

root@WWW:~# apt-get -f install

Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-36-generic-pae linux-headers-3.2.0-36
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-generic-pae linux-headers-3.2.0-39 linux-headers-3.2.0-39-generic-pae linux-headers-generic-pae
  linux-image-3.2.0-39-generic-pae linux-image-generic-pae
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed:
  linux-headers-3.2.0-39 linux-headers-3.2.0-39-generic-pae linux-image-3.2.0-39-generic-pae
The following packages will be upgraded:
  linux-generic-pae linux-headers-generic-pae linux-image-generic-pae
3 upgraded, 3 newly installed, 0 to remove and 90 not upgraded.
5 not fully installed or removed.
Need to get 50.9 MB of archives.
After this operation, 181 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-image-3.2.0-39-generic-pae i386 3.2.0-39.62 [38.2 MB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-generic-pae i386 3.2.0.39.47 [1,730 B]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-image-generic-pae i386 3.2.0.39.47 [2,600 B]
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-39 all 3.2.0-39.62 [11.7 MB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-39-generic-pae i386 3.2.0-39.62 [985 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-generic-pae i386 3.2.0.39.47 [2,598 B]
Fetched 50.9 MB in 5min 5s (167 kB/s)
Selecting previously unselected package linux-image-3.2.0-39-generic-pae.
(Reading database ... 77763 files and directories currently installed.)
Unpacking linux-image-3.2.0-39-generic-pae (from .../linux-image-3.2.0-39-generic-pae_3.2.0-39.62_i386.deb) ...
Done.
Selecting previously unselected package linux-headers-3.2.0-39.
Unpacking linux-headers-3.2.0-39 (from .../linux-headers-3.2.0-39_3.2.0-39.62_all.deb) ...
Selecting previously unselected package linux-headers-3.2.0-39-generic-pae.
Unpacking linux-headers-3.2.0-39-generic-pae (from .../linux-headers-3.2.0-39-generic-pae_3.2.0-39.62_i386.deb) ...
Setting up linux-image-3.2.0-39-generic-pae (3.2.0-39.62) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-39-generic-pae /boot/vmlinuz-3.2.0-39-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-39-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-39-generic-pae /boot/vmlinuz-3.2.0-39-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-39-generic-pae /boot/vmlinuz-3.2.0-39-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-39-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-39-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-36-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-36-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-35-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-35-generic-pae
Found memtest86+ image: /memtest86+.bin
done
[B]dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-37-generic-pae; however:
  Package linux-image-3.2.0-37-generic-pae is not installed.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
[/B]Setting up linux-headers-3.2.0-39 (3.2.0-39.62) ...
No apport report written because MaxReports is reached already
                                                              Setting up linux-headers-3.2.0-39-generic-pae (3.2.0-39.62) ...
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.37.44); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-3.2.0-37 (3.2.0-37.58) ...
No apport report written because MaxReports is reached already
                                                              Setting up linux-headers-3.2.0-37-generic-pae (3.2.0-37.58) ...
Setting up linux-headers-generic-pae (3.2.0.37.44) ...
Errors were encountered while processing:
 linux-image-generic-pae
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@GDCWWW:~# df -h
Filesystem               Size  Used Avail Use% Mounted on
/dev/mapper/GDCWWW-root  145G  2.9G  135G   3% /
udev                     983M   12K  983M   1% /dev
tmpfs                    396M  324K  396M   1% /run
none                     5.0M     0  5.0M   0% /run/lock
none                     990M     0  990M   0% /run/shm
/dev/sda1                228M   71M  146M  33% /boot
root@GDCWWW:~#


```

---

### Post by schragge on 2013-03-21
Well, then purge *linux-image-generic-pae* and re-run *apt-get -f install*:
```

sudo dpkg -P --force-remove-reinstreq linux-image-generic-pae
sudo apt-get clean
sudo apt-get -f install

```

---

### Post by Bashing-om on 2013-03-21
@schragge & DoubelD ;

Thanks ! Still learning even after all these years !

---

### Post by DoubelD on 2013-03-21
> **schragge said:**
> Well, then purge *linux-image-generic-pae* and re-run *apt-get -f install*:
```

sudo dpkg -P --force-remove-reinstreq linux-image-generic-pae
sudo apt-get clean
sudo apt-get -f install

```

This is ridiculous :mad:

I'm not mad at you just wondering why it has to be so difficult. I tried your last suggestion 

```

root@WWW:~# dpkg -P --force-remove-reinstreq linux-image-generic-pae

(Reading database ... 100085 files and directories currently installed.)
Removing linux-image-generic-pae ...

root@WWW:~# df -h

Filesystem               Size  Used Avail Use% Mounted on
/dev/mapper/GDCWWW-root  145G  2.9G  135G   3% /
udev                     983M   12K  983M   1% /dev
tmpfs                    396M  324K  396M   1% /run
none                     5.0M     0  5.0M   0% /run/lock
none                     990M     0  990M   0% /run/shm
/dev/sda1                228M   49M  168M  23% /boot

root@WWW:~# apt-get clean

root@WWW:~# apt-get -f install

Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-generic-pae linux-image-generic-pae
The following NEW packages will be installed:
  linux-image-generic-pae
The following packages will be upgraded:
  linux-generic-pae
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 4,330 B of archives.
After this operation, 31.7 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-generic-pae i386 3.2.0.39.47 [1,730 B]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-image-generic-pae i386 3.2.0.39.47 [2,600 B]
Fetched 4,330 B in 0s (43.7 kB/s)
Selecting previously unselected package linux-image-generic-pae.
(Reading database ... 100082 files and directories currently installed.)
Unpacking linux-image-generic-pae (from .../linux-image-generic-pae_3.2.0.39.47_i386.deb) ...
Setting up linux-image-generic-pae (3.2.0.39.47) ...
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.37.44); however:
  Version of linux-image-generic-pae on system is 3.2.0.39.47.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.37.44); however:
  Version of linux-headers-generic-pae on system is 3.2.0.39.47.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@WWW:~#
```


I'm getting ready to give up :-({|=  -  I'll have to rebuild/install the server and try to remember what I did to make it work - I'm a newbie

---

### Post by schragge on 2013-03-21
Try one more iteration of the same. *linux-generic-pae* pulls the wrong *linux-image-generic-pae*, so remove the first and let *apt-get -f install* decide which version should be installed:
```

sudo dpkg -P --force-remove-reinstreq linux-generic-pae
sudo apt-get clean
sudo apt-get -f install

```
It is so difficult because after running out of free space your package management system ended up in a half-broken state. Until you successfully repair it with *apt-get -f install*, you cannot expect it to work properly.

---

### Post by DoubelD on 2013-03-21
> **schragge said:**
> Try one more iteration of the same. *linux-generic-pae* pulls the wrong *linux-image-generic-pae*, so remove the first and let *apt-get -f install* decide which version should be installed:
```

sudo dpkg -P --force-remove-reinstreq linux-generic-pae
sudo apt-get clean
sudo apt-get -f install

```

Hmmm 

does this mean it worked ???

```

root@WWW:~# dpkg -P --force-remove-reinstreq linux-generic-pae

(Reading database ... 100085 files and directories currently installed.)
Removing linux-generic-pae ...

root@WWW:~# apt-get clean

root@WWW:~# apt-get -f install

Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```


I usually do  

```
sudo apt-get update && sudo apt-get dist-upgrade 
``` 

is that a bad thing ? and how did /boot get full is it due to answering Yes to autoupdate during the install and if yes how do I turn that off 

oh and if I'm all better now how do I stop this from happening again

---

### Post by schragge on 2013-03-21
You do it right. It's also a good idea to attempt an upgrade right now. I usually do it in a more conservative way, i.e.
```
sudo apt-get update&&sudo apt-get upgrade[COLOR=blue]; sudo apt-get dist-upgrade[/COLOR]
``` The last part is only needed if the regular upgrade cannot upgrade some packages (usually, the kernel).

The problem is that old kernels never get removed automatically. This is not a bug, it's designed this way because you may need them. Keep an eye on them piling up and spamming your /boot directory. For most purposes, two kernels are enough. To keep things tidy, you may try the command suggested by **Bashing-om** in the [post=12566860]second post[/post] on this thread. It should work now. To see what it is going to do, test it with the -s (simulate) switch:
```
apt-get [COLOR=red]-s[/COLOR] purge linux-image-{[0-9],`uname -r`+,`readlink /vmlinuz.old|cut -d- -f2-`+}
```

---

### Post by hydn79 on 2013-03-21
Can't one just manually delete the old unused boot files?

---

### Post by schragge on 2013-03-21
It depends. Some files in /boot (initrd*) were generated by *update-initramfs* and can be safely deleted any time (but not the initrd for your running kernel, obviously). They will be regenerated on the next run of *update-initramfs*. Others are  installed by some packages, I wouldn't recommend manually deleting them.  The proper way to remove them is to uninstall the package that  installed them.

---

### Post by DoubelD on 2013-03-21
> **schragge said:**
> You do it right. It's also a good idea to attempt an upgrade right now. I usually do it in a more conservative way, i.e.
```
sudo apt-get update&&sudo apt-get upgrade[COLOR=blue]; sudo apt-get dist-upgrade[/COLOR]
``` The last part is only needed if the regular upgrade cannot upgrade some packages (usually, the kernel).

The problem is that old kernels never get removed automatically. This is not a bug, it's designed this way because you may need them. Keep an eye on them piling up and spamming your /boot directory. For most purposes, two kernels are enough. To keep things tidy, you may try the command suggested by **Bashing-om** in the [post=12566860]second post[/post] on this thread. It should work now. To see what it is going to do, test it with the -s (simulate) switch:
```
apt-get [COLOR=red]-s[/COLOR] purge linux-image-{[0-9],`uname -r`+,`readlink /vmlinuz.old|cut -d- -f2-`+}
```

\\:D/   Finally it seems to be good 

This worked ```
sudo apt-get update&&sudo apt-get upgrade[COLOR=blue]; sudo apt-get dist-upgrade[/COLOR]
``` 
and 
this was ok too ```
apt-get [COLOR=red]-s[/COLOR] purge  linux-image-{[0-9],`uname -r`+,`readlink /vmlinuz.old|cut -d-  -f2-`+}
```


I have attempted to just delete files in /boot and I can vouch that's not goo dthings really get messed up 

Since I have a Clonezilla  [http://clonezilla.org/](http://clonezilla.org/) Image of this server I kept restoring the image and trying the fix  and finally I think the last thing we tried did the job 

Now to restore the image and just trying the last set of commands

     ```
sudo dpkg -P --force-remove-reinstreq linux-generic-pae
sudo apt-get clean
sudo apt-get -f install
```

before I do it to the live server - Then I need to install Samba, Snapsots (BackInTime of Flyback) and I think I need a GUI  


Are there any How 2 install GUI on this forum and and recommendations

---

### Post by Bashing-om on 2013-03-21
DoubelD;

Did you run the "apt-get -s purge" code without the "s" ->simulate switch in place ?

Gui desktop: It is not generally recommended to run a GUI on a server; security risk and not least is a loss of performance on the machine. There are tools to administer the server from remote. I have seen webmin highly recommended.
With that said there are those who do. May I suggest that you search this forum on that topic to make an informed decision.
[INDENT=3]
just my 2 cents worth

[/INDENT]

---

### Post by DoubelD on 2013-03-21
> **Bashing-om said:**
> DoubelD;

Did you run the "apt-get -s purge" code without the "s" ->simulate switch in place ?

Gui desktop: It is not generally recommended to run a GUI on a server; security risk and not least is a loss of performance on the machine. There are tools to administer the server from remote. I have seen webmin highly recommended.
With that said there are those who do. May I suggest that you search this forum on that topic to make an informed decision.[INDENT=3]
just my 2 cents worth

[/INDENT]


Why yes, yes I did 

Thanks for pointing that out I'll change it 


apt-get purge  linux-image-{[0-9],`uname -r`+,`readlink /vmlinuz.old|cut -d-  -f2-`+}

---

### Post by DoubelD on 2013-03-26
> **Bashing-om said:**
> DoubelD;

If you are certain that your /boot is at capacity: Here is schragge's solution:
```
 sudo apt-get purge linux-image-{[0-9],`uname -r`+,`readlink /vmlinuz.old|cut -d- -f2-`+} 
```
This code retains the 2 latest kernels and removes the rest.[INDENT=2]hope this helps

[/INDENT]


I think this ```
 
apt-get purge linux-image-{[0-9],`uname -r`+,`readlink /vmlinuz.old|cut -d- -f2-`+}
```

Produces and error

```
apt-get -s purge  linux-image-{[0-9],`uname -r`+,`readlink /vmlinuz.old|cut -d-  -f2-`+}
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting 'linux-image-3.2.0-39-generic' for regex 'linux-image-[0-9]'
Note, selecting 'linux-image-3.2.0-34-generic-pae' for regex 'linux-image-[0-9]'
[B].
.
.[/B]
Note, selecting 'linux-image-3.2.0-39-highbank' for regex 'linux-image-[0-9]'
**E: Unable to locate package linux-image-**

```

---

### Post by schragge on 2013-03-27
This means you have only one kernel installed, so there's no */vmlinuz.old* on your system. A quick fix is to change the command like this:
```
apt-get purge linux-image-{[0-9],`uname -r`+}
```
Note that it will remove all kernels but the latest.

A proper solution is to put this in a shell script:
```

#!/bin/sh
prev=`readlink /vmlinuz.old` && prev=linux-image-${prev#*-}+
exec sudo apt-get purge '^linux-image-[0-9]' linux-image-`uname -r`+ $prev

```
If you're going to periodically run the script as a cronjob from the root crontab or from */etc/cron.monthly* then change the last line accordingly:
```

#!/bin/sh
prev=`readlink /vmlinuz.old` && prev=linux-image-${prev#*-}+
exec apt-get -y purge '^linux-image-[0-9]' linux-image-`uname -r`+ $prev

```

---

