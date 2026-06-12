---
title: "Inconsistency detected -- Can't Reinstall or Uninstall"
date: 2007-12-24
forum: General Help
---

### Post by Thunar on 2007-12-24
Hey everyone I have a great one for you. I've been having issues with my computer lately that have caused some crashes and what not, and this has led to a couple of forced fsck action, and I think it may have finally gotten the better of Ubuntu's uncanny ability to keep itself in check. 

After my last fsck episode the computer botted just fine to the desktop, but gave me an error saying there was a problem with my Deskbar applet, and asked me if I wanted to delete it from the panel. I did. Then I figured I would give synaptic a go at reinstalling the broken package, but every time it said it could not do it. So I tried to uninstall it completely, no luck. So I decided it was time to get into terminal and see what was going on. It seems that the package can't autoremove itself because of a problem with the script, nor can in reinstall or uninstall using what it says is the "new" script. Anyways, I'll let terminal speak for itself. Here's the run-down, any help would be greatly appreciated:

susan@susan-desktop:~$ sudo apt-get autoremove
[sudo] password for susan:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcurl3 libphysfs-1.0-0
The following packages will be REMOVED:
  libcurl3 libphysfs-1.0-0
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/347kB of archives.
After unpacking 520kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 97392 files and directories currently installed.)
Preparing to replace deskbar-applet 2.20.0-0ubuntu2 (using .../deskbar-applet_2.20.0-0ubuntu2_i386.deb) ...
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: error processing /var/cache/apt/archives/deskbar-applet_2.20.0-0ubuntu2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Preparing to replace libdeskbar-tracker 0.6.3-0ubuntu3 (using .../libdeskbar-tracker_0.6.3-0ubuntu3_all.deb) ...
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: error processing /var/cache/apt/archives/libdeskbar-tracker_0.6.3-0ubuntu3_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/deskbar-applet_2.20.0-0ubuntu2_i386.deb
 /var/cache/apt/archives/libdeskbar-tracker_0.6.3-0ubuntu3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
susan@susan-desktop:~$ sudo aptitude update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy Release.gpg
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US               
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Fetched 3B in 3s (1B/s)  
Reading package lists... Done
susan@susan-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcurl3 libphysfs-1.0-0
The following packages will be REMOVED:
  libcurl3 libphysfs-1.0-0
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/347kB of archives.
After unpacking 520kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 97392 files and directories currently installed.)
Preparing to replace deskbar-applet 2.20.0-0ubuntu2 (using .../deskbar-applet_2.20.0-0ubuntu2_i386.deb) ...
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: error processing /var/cache/apt/archives/deskbar-applet_2.20.0-0ubuntu2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Preparing to replace libdeskbar-tracker 0.6.3-0ubuntu3 (using .../libdeskbar-tracker_0.6.3-0ubuntu3_all.deb) ...
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: error processing /var/cache/apt/archives/libdeskbar-tracker_0.6.3-0ubuntu3_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/deskbar-applet_2.20.0-0ubuntu2_i386.deb
 /var/cache/apt/archives/libdeskbar-tracker_0.6.3-0ubuntu3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
susan@susan-desktop:~$ 
susan@susan-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy Release.gpg
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US          
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Fetched 3B in 1s (2B/s)  
Reading package lists... Done
susan@susan-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcurl3 libphysfs-1.0-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/347kB of archives.
After unpacking 0B of additional disk space will be used.
(Reading database ... 97392 files and directories currently installed.)
Preparing to replace deskbar-applet 2.20.0-0ubuntu2 (using .../deskbar-applet_2.20.0-0ubuntu2_i386.deb) ...
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: error processing /var/cache/apt/archives/deskbar-applet_2.20.0-0ubuntu2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Preparing to replace libdeskbar-tracker 0.6.3-0ubuntu3 (using .../libdeskbar-tracker_0.6.3-0ubuntu3_all.deb) ...
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: error processing /var/cache/apt/archives/libdeskbar-tracker_0.6.3-0ubuntu3_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/deskbar-applet_2.20.0-0ubuntu2_i386.deb
 /var/cache/apt/archives/libdeskbar-tracker_0.6.3-0ubuntu3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Thanks!

---

### Post by Sef on 2007-12-24
Try these commands:

```
sudo dpkg --configure -a
```

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

If you still get errors, then post them.

---

### Post by PmDematagoda on 2007-12-24
Also delete the packages that are shown in the error using:-

```
sudo rm /var/cache/apt/archives/deskbar-applet_2.20.0-0ubuntu2_i386.deb
```
and
```
sudo rm /var/cache/apt/archives/libdeskbar-tracker_0.6.3-0ubuntu3_all.deb
```

Then see if the problem is solved.

---

### Post by Thunar on 2007-12-29
Thanks for replying! (Especially on a Holiday week)

Ok. Well I tried all of that, and still it seems to be giving me some trouble.

Of particular interest are these,

sudo apt-get upgrade returned:

susan@susan-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/347kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 97392 files and directories currently installed.)
Preparing to replace deskbar-applet 2.20.0-0ubuntu2 (using .../deskbar-applet_2.20.0-0ubuntu2_i386.deb) ...
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: error processing /var/cache/apt/archives/deskbar-applet_2.20.0-0ubuntu2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Preparing to replace libdeskbar-tracker 0.6.3-0ubuntu3 (using .../libdeskbar-tracker_0.6.3-0ubuntu3_all.deb) ...
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: error processing /var/cache/apt/archives/libdeskbar-tracker_0.6.3-0ubuntu3_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/deskbar-applet_2.20.0-0ubuntu2_i386.deb
 /var/cache/apt/archives/libdeskbar-tracker_0.6.3-0ubuntu3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

So I tried 
"susan@susan-desktop:~$ sudo rm /var/cache/apt/archives/deskbar-applet_2.20.0-0ubuntu2_i386.deb"
& 
"susan@susan-desktop:~$ sudo rm /var/cache/apt/archives/libdeskbar-tracker_0.6.3-0ubuntu3_all.deb"
Then
"susan@susan-desktop:~$ sudo dpkg --configure -a" which returned:

susan@susan-desktop:~$ sudo rm /var/cache/apt/archives/deskbar-applet_2.20.0-0ubuntu2_i386.deb
susan@susan-desktop:~$ sudo rm /var/cache/apt/archives/libdeskbar-tracker_0.6.3-0ubuntu3_all.deb
susan@susan-desktop:~$ sudo dpkg --configure -a
dpkg: error processing deskbar-applet (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of libdeskbar-tracker:
 libdeskbar-tracker depends on deskbar-applet; however:
  Package deskbar-applet is not configured yet.
dpkg: error processing libdeskbar-tracker (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 deskbar-applet
 libdeskbar-tracker
susan@susan-desktop:~$ 

So it seems I can't reinstall it, uninstall it, or get rid of it. I'm stuck with a broken package for now. Oh, and now my Add/Remove programs will not start up either. And Synaptic tells me "0 Packages are Broken" ...silly Synaptic :)

Thanks again for replying! Any more ideas?

---

### Post by PmDematagoda on 2007-12-29
Do:-

```
sudo aptitude install deskbar-applet && sudo aptitude install libdeskbar-tracker
```

Then do:-
```
sudo dpkg --configure -a
```

---

### Post by Thunar on 2007-12-29
Thanks again! :)

```
sudo aptitude download deskbar-applet && sudo aptitude download libdeskbar-tracker
```

Returned:

susan@susan-desktop:~$ sudo aptitude download deskbar-applet && sudo aptitude download libdeskbar-tracker
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main deskbar-applet 2.20.0-0ubuntu2 [309kB]
Fetched 309kB in 1s (170kB/s)          
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libdeskbar-tracker 0.6.3-0ubuntu3 [38.5kB]
Fetched 38.5kB in 0s (38.7kB/s)  

and,

```
sudo dpkg --configure -a
```[/QUOTE]

Returned:

susan@susan-desktop:~$ sudo dpkg --configure -a
Setting up python2.5-dev (2.5.1-5ubuntu5) ...
Setting up python-dev (2.5.1-1ubuntu2) ...
dpkg: error processing deskbar-applet (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of libdeskbar-tracker:
 libdeskbar-tracker depends on deskbar-applet; however:
  Package deskbar-applet is not configured yet.
dpkg: error processing libdeskbar-tracker (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 deskbar-applet
 libdeskbar-tracker
susan@susan-desktop:~$ 

Ok I noticed a possible problem here:

Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main deskbar-applet 2.20.0-0ubuntu2 [309kB]
Fetched 1B in 0s (2B/s)

Even though the package is supposed to be 309kB it seems as though it only downloaded 1B? Hmm, that can't be good. Reinstalls, uninstalls and dpkg -configure's are all still no good, too. *sigh*

at this point should I just slap the live CD in and reinstall? Or is there maybe something else I could try?

Thanks again, the help is appreciated! :)

---

### Post by Thunar on 2007-12-29
Ok, I take that back, it did seem to download the full package the first time I entered the command, but I tried the same command a second time and that's when it appeared to have downloaded 1 byte. So i don't know if maybe it just didn't download it again because I had already downloaded it.

---

### Post by PmDematagoda on 2007-12-30
Try:-

```
sudo apt-get install --reinstall libdeskbar-tracker && sudo apt-get install --reinstall deskbar-applet
```

---

### Post by Thunar on 2007-12-30
Yeah it just gave me all of the same exact error codes. :(

```
sudo apt-get install --reinstall libdeskbar-tracker && sudo apt-get install --reinstall deskbar-applet
```[/QUOTE]

returned:

susan@susan-desktop:~$ sudo apt-get install --reinstall libdeskbar-tracker && sudo apt-get install --reinstall deskbar-applet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcurl3 libphysfs-1.0-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/347kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 97643 files and directories currently installed.)
Preparing to replace deskbar-applet 2.20.0-0ubuntu2 (using .../deskbar-applet_2.20.0-0ubuntu2_i386.deb) ...
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: error processing /var/cache/apt/archives/deskbar-applet_2.20.0-0ubuntu2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Preparing to replace libdeskbar-tracker 0.6.3-0ubuntu3 (using .../libdeskbar-tracker_0.6.3-0ubuntu3_all.deb) ...
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: error processing /var/cache/apt/archives/libdeskbar-tracker_0.6.3-0ubuntu3_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
Inconsistency detected by ld.so: dynamic-link.h: 169: elf_get_dynamic_info: Assertion `info[19]->d_un.d_val == sizeof (Elf32_Rel)' failed!
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/deskbar-applet_2.20.0-0ubuntu2_i386.deb
 /var/cache/apt/archives/libdeskbar-tracker_0.6.3-0ubuntu3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
susan@susan-desktop:~$ 

so... that's fun! :)

thanks for sticking with me on this one, I know it's frustrating (especially for me, haha), but thanks!

---

### Post by ufpost on 2008-01-01
Ran into some apt-get problems myself (doc'd in the following thread: [http://ubuntuforums.org/showthread.php?t=654450]("http://ubuntuforums.org/showthread.php?t=654450")).

Not exactly your case, but I'd suggest identifying the bad packages by:

> for i in $(dpkg --list | cut -f3 -d' '); do dpkg -s $i | grep -E "^(Package|Status):.*"; done; 

Then downgrade the bad package(s) by the following (replacing the <<package filename>>.deb with the appropriate filename from the /var/cache/apt/archives directory...assuming the archive still exists):

> sudo dpkg -i --force-downgrade <<package_filename>>.deb 

The deb files in your case are: 
> 
/var/cache/apt/archives/deskbar-applet_2.20.0-0ubuntu2_i386.deb
/var/cache/apt/archives/libdeskbar-tracker_0.6.3-0ubuntu3_all.deb


In case these fail, see if there are any previous versions of the deb files still in the apt cache. Just be careful using the forced downgrade, as it may cause other breaks - the further you go back, the greater the chance for breakage. 

After downgrading, I'd recommend reviewing your /etc/apt/sources.list file and finding repositories with new deb files (though the deb files may not be the ultimate problem). 

Not the most absolute answer, but I thought it may help for ideas...

Good luck.

---

### Post by Thunar on 2008-01-04
Thanks everyone for all the help!

I solved my problem in the most absolute & simple way: Backup & Reinstall :)

I probably would've stuck with it and tried to work it out, but besides the problems with apt I think I might have had some file system problems, too (according to the many forced fsck passes). I couldn't update, add/remove wouldn't even start up, I couldn't install or uninstall anything, and I was having some other system weirdness as well (like the shut down menu taking up to 5 minutes to show up and let me shut down sometimes).

After the reinstall the system is running actually better than it did after the first clean install. Everything works tip-top now, and due to a thorough back up very little was lost.

Thanks ufpost for the help anyway, if I should have a similar problem again I will be sure to reference this post. Kinda wish I could have tried the forced downgrade before the reinstall, for research purposes if nothing else.

Thanks again to everyone who was nice enough to give a Linux novice some advice. :)

cheers

---

