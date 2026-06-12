---
title: "Can't install wine. Crazy dependency problem?"
date: 2012-12-04
forum: General Help
---

### Post by avianbc on 2012-12-04
Posted to the [Wine forum]("http://ubuntuforums.org/showthread.php?t=2090551") and no one would touch it.

I cannot install wine no matter what I do. I've tried a million workarounds and nothing. Give me a suggestion on what to do. Anything!

Background:  Fresh install of Ubuntu 12.10 using Cinnamon. Originally installed through WUBI, migrated WUBI to its own partition.

Here is the exact error:

From command line:
> avian@ubuntu:~$ sudo apt-get install wine
[sudo] password for avian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.4 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
avian@ubuntu:~$ sudo apt-get install wine1.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.4 : Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is not installable
           Recommends: gnome-exe-thumbnailer but it is not going to be installed or
                       kde-runtime but it is not going to be installed
           Recommends: ttf-umefont but it is not going to be installed
           Recommends: ttf-unfonts-core but it is not going to be installed
           Recommends: winbind but it is not going to be installed
           Recommends: winetricks but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


From software center:
> Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

Details:

The following packages have unmet dependencies:

wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.7ubuntu6 is to be installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu20 is to be installed
         Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1) but 1.4.1-0ubuntu1 is to be installed
         Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is not going to be installed

Aptitude:

> avian@ubuntu:~$ sudo aptitude install wine
The following NEW packages will be installed:
  libcapi20-3{a} libodbc1{a} odbcinst{a} odbcinst1debian2{a} unixodbc{a} 
  wine wine-gecko1.4{a} wine1.4{ab} wine1.4-amd64{a} wine1.4-common{a} 
The following packages are RECOMMENDED but will NOT be installed:
  gnome-exe-thumbnailer kde-runtime ttf-umefont ttf-unfonts-core winbind 
  winetricks 
0 packages upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 37.9 MB of archives. After unpacking 131 MB will be used.
The following packages have unmet dependencies:
 wine1.4 : Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) which is a virtual package.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     wine [Not Installed]                               
2)     wine1.4 [Not Installed]                            
3)     wine1.4-amd64 [Not Installed]                      
4)     wine1.4-common [Not Installed]                     

     Leave the following dependencies unresolved:         
5)     wine-gecko1.4 recommends wine1.4-amd64             


Accept this solution? [Y/n/q/?] Y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.


1) Synaptic gets the same error.
2) sudo dpkg --configure -a did not help
3) sudo apt-get install -f did not help
4) Official wine PPA doesnt work

---

### Post by oldos2er on 2012-12-04
We tend to discourage posting the same question or problem multiple times; it dilutes community effort. Feel free to bump your original thread (but not more than once a day), and be patient. We are all volunteers, and it may take time for someone who's able to offer you help to see your thread.

---

