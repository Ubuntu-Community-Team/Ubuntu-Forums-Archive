---
title: "Broken dependencies"
date: 2007-12-11
forum: General Help
---

### Post by bwgolling on 2007-12-11
I seem to have broken my system when I tried to install printer drivers that I got from the printer's manufacturer and not from a synaptic repo.
I have run tried almost all the switches in apt-get and it won't resolve the problem.
Here is the result of apt-get -f install

bwg@bwg-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  mfc665cwcupswrapper
0 upgraded, 0 newly installed, 1 to remove and 9 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 119494 files and directories currently installed.)
Removing mfc665cwcupswrapper ...
/var/lib/dpkg/info/mfc665cwcupswrapper.prerm: 3: /usr/local/Brother/Printer/mfc665cw/cupswrapper/cupswrappermfc665cw: not found
dpkg: error processing mfc665cwcupswrapper (--remove):
 subprocess pre-removal script returned error exit status 127
/var/lib/dpkg/info/mfc665cwcupswrapper.postinst: 3: /usr/local/Brother/Printer/mfc665cw/cupswrapper/cupswrappermfc665cw: not found
cp: cannot stat `/usr/share/cups/model/brmfc665cw.ppd': No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mfc665cwcupswrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)


Does anyone have a suggestion?

---

### Post by skymera on 2007-12-11
hmm try

sudo dpkg --configure -a

or

sudo dpkg --reconfigure -a

my brains a bit cloudy :)

---

### Post by bwgolling on 2007-12-11
Didn't work...can't find that switch

---

### Post by skymera on 2007-12-11
in the terminal dosent work?

---

### Post by rsambuca on 2007-12-11
It's the first one, by the way.

```
sudo dpkg --configure -a
```

---

### Post by skymera on 2007-12-11
thanks, always get confused :)

---

### Post by bwgolling on 2007-12-11
Sorry, i did find and try that switch but it has no effect on my problem.
I have no more ideas on how to handle this problem

---

### Post by rsambuca on 2007-12-11
What did it say when you ran that command?  Can you please post the output here?

---

### Post by bwgolling on 2007-12-11
I did not produce any output at all.  It just popped up a fresh prompt.

---

### Post by rsambuca on 2007-12-11
Then try this:```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by anaconda on 2007-12-11
I had similar problem, and found a solution for it..

[http://ubuntuforums.org/showthread.php?t=612064](http://ubuntuforums.org/showthread.php?t=612064)

good luck ;)

---

### Post by bwgolling on 2007-12-11
Here is the reply when update and upgrade are run.

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US                     
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US               
Get:3 [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release.gpg [189B]                     
Ign [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Translation-en_US                   
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US             
Hit http ://archive.canonical.com gutsy/partner Packages                        
Hit [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                            
Hit [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Packages                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Fetched 6B in 2s (2B/s)  
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  mfc665cwcupswrapper: Depends: mfc665cwlpr but it is not installable
E: Unmet dependencies. Try using -f.

---

### Post by rsambuca on 2007-12-11
Go to System - Administration - Software Sources and deselect the CDrom (near the bottom).

Then try again.

---

### Post by rsambuca on 2007-12-11
Actually, I just checked, and the package you are having trouble with doesn't exist in the Ubuntu repos.  You will have to get help from wherever you got that package.

---

### Post by bwgolling on 2007-12-11
Thanks but no dice.  I am still getting the same error.
I am beginning to think I will have to reinstall the whole system ( shades of windows  :)

---

### Post by rsambuca on 2007-12-11
You don't have to reinstall.  You have to fix that package.  Where did you get 'mfc665cwcupswrapper' from?

---

### Post by bwgolling on 2007-12-11
I got the package from Brother (the printer manufacturer.)  It was packaged as a .deb package.  As a matter of f act there were two but after I installed them synaptic started complaining so I tried to remove them.  Then, I believe I might have deleted something by hand rather than automatically through dpkg and that is where my problem started.  I think the packages are basically gone but the uninstall script still looks for them.
does that make any sense

---

### Post by rsambuca on 2007-12-11
Try this first

sudo apt-get remove --purge mfc665cwcupswrapper

---

### Post by bwgolling on 2007-12-11
I tried that with pretty much the same results.  here is output

bwg@bwg-laptop:~$ sudo apt-get remove --purge mfc665cwcupswrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  mfc665cwcupswrapper*
0 upgraded, 0 newly installed, 1 to remove and 10 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 119494 files and directories currently installed.)
Removing mfc665cwcupswrapper ...
/var/lib/dpkg/info/mfc665cwcupswrapper.prerm: 3: /usr/local/Brother/Printer/mfc665cw/cupswrapper/cupswrappermfc665cw: not found
dpkg: error processing mfc665cwcupswrapper (--purge):
 subprocess pre-removal script returned error exit status 127
/var/lib/dpkg/info/mfc665cwcupswrapper.postinst: 3: /usr/local/Brother/Printer/mfc665cw/cupswrapper/cupswrappermfc665cw: not found
cp: cannot stat `/usr/share/cups/model/brmfc665cw.ppd': No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mfc665cwcupswrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by rsambuca on 2007-12-11
Looks like you are going to have to do this the manual way!

1.  Make sure you have backed up your data.
2.  Go to /var/lib/dpkg/info/ and look for any files that look like mfc665cwcupswrapper.  You will have to delete these files.  Either using Nautilus as root (gksudo nautilus) or via the command line (sudo rm /var/lib/dpkg/info/filenamehere)  Just be very careful here as any mistakes can bork your system.  
3.  Enter ```
sudo dpkg -r --force-remove-reinstreq mfc665cwcupswrapper
```
4.  Then ```
sudo dpkg --purge mfc665cwcupswrapper
```
5.  ```
Then sudo apt-get update && sudo apt-get upgrade
```

---

### Post by bwgolling on 2007-12-11
Still no good.  I can't get past error status 127 

dpkg: error processing mfc665cwcupswrapper (--purge):
 subprocess pre-removal script returned error exit status 127
/var/lib/dpkg/info/mfc665cwcupswrapper.postinst: 3: /usr/local/Brother/Printer/mfc665cw/cupswrapper/cupswrappermfc665cw: not found
cp: cannot stat `/usr/share/cups/model/brmfc665cw.ppd': No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mfc665cwcupswrapper

---

### Post by rsambuca on 2007-12-11
Sorry, what step did this error occur?  Did you find any files?

---

### Post by bwgolling on 2007-12-11
That was a result of dpkg --purge mfc665cwcupswrapper

---

### Post by rsambuca on 2007-12-11
Were there any files to delete?  What happened after you ran the command prior to the purge one?

---

### Post by bwgolling on 2007-12-11
There doesn't seem to be any files to delete.  That is what ii is complaining about

bwg@bwg-laptop:~$ sudo dpkg --purge mfc665cwcupswrapper
[sudo] password for bwg:
(Reading database ... 119494 files and directories currently installed.)
Removing mfc665cwcupswrapper ...
/var/lib/dpkg/info/mfc665cwcupswrapper.prerm: 3: /usr/local/Brother/Printer/mfc665cw/cupswrapper/cupswrappermfc665cw: not found
dpkg: error processing mfc665cwcupswrapper (--purge):
 subprocess pre-removal script returned error exit status 127
/var/lib/dpkg/info/mfc665cwcupswrapper.postinst: 3: /usr/local/Brother/Printer/mfc665cw/cupswrapper/cupswrappermfc665cw: not found
cp: cannot stat `/usr/share/cups/model/brmfc665cw.ppd': No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mfc665cwcupswrapper
bwg@bwg-laptop:~$

---

### Post by rsambuca on 2007-12-11
What happened after your ran this:

sudo dpkg -r --force-remove-reinstreq mfc665cwcupswrapper

---

### Post by bwgolling on 2007-12-11
here it is

bwg@bwg-laptop:~$ sudo dpkg -r --force-remove-reinstreq mfc665cwcupswrapper
[sudo] password for bwg:
(Reading database ... 119494 files and directories currently installed.)
Removing mfc665cwcupswrapper ...
/var/lib/dpkg/info/mfc665cwcupswrapper.prerm: 3: /usr/local/Brother/Printer/mfc665cw/cupswrapper/cupswrappermfc665cw: not found
dpkg: error processing mfc665cwcupswrapper (--remove):
 subprocess pre-removal script returned error exit status 127
/var/lib/dpkg/info/mfc665cwcupswrapper.postinst: 3: /usr/local/Brother/Printer/mfc665cw/cupswrapper/cupswrappermfc665cw: not found
cp: cannot stat `/usr/share/cups/model/brmfc665cw.ppd': No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mfc665cwcupswrapper
bwg@bwg-laptop:~$

---

### Post by rsambuca on 2007-12-11
Rather than hunting down every single file, I suggest you might consider downloading and installing the .deb packages again.  Then you can try removing them the proper way with Synaptic.

---

### Post by bwgolling on 2007-12-11
I wish it were that easy.  I tried that but synaptic won't allow it because of dependency issues.

---

### Post by rsambuca on 2007-12-11
I know your synaptic is borked because of this, but can you at least open it?  If so, is the mfc665cwcupswrapper package listed?  If it is there, try right clicking it and in the Properties section there is a tab that says "Installed Files".  It lists every file that was added.  That might give you a starting point to start hunting the stuff down.

---

### Post by bwgolling on 2007-12-11
That is what is so infuriaiting.  I can open synaptic and it tells me that mfc665... is broken.  but no matter what I try, everything stays the same.  I have even grepped the whole system looking for "mfc665cwcupswrapper" so that I might then change the script but I am afraid that I would totally bork everything.
Thanks so much for the effort, it was a good try.

---

### Post by rsambuca on 2007-12-11
Sorry dude, I know for sure there is a way to fix it, but I am not knowledgeable enough in this area.  Hopefully someone else will come along that knows far more than I.

You might consider having  a quick search in the debian forums and wiki too.  They are a very knowledgeable crowd there.

---

### Post by anaconda on 2007-12-12
> **anaconda said:**
> I had similar problem, and found a solution for it..

[http://ubuntuforums.org/showthread.php?t=612064](http://ubuntuforums.org/showthread.php?t=612064)

good luck ;)

Have you tried this solution yet?

You can do the same what I did.. which is to manually remove all references to that package from apt-get, dpkg, and synaptic.. after that those programs will work again.

I haven't had any problems after doing that..

---

