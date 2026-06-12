---
title: "Error when opening Synaptic"
date: 2007-05-17
forum: General Help
---

### Post by roffy on 2007-05-17
Using feisty, tried installing LAMP with Synaptic and it failed and now when I try to open Synaptic this error occurs.

[IMG]http://i102.photobucket.com/albums/m97/roffy85/error.jpg[/IMG]

---

### Post by taurus on 2007-05-17
Close that window or synaptic if you have it running.  Then, open a terminal and post the output of these two commands here.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by roffy on 2007-05-17
sudo aptitude update:

Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release                                  
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US           
Get:3 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg [189B]                    
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_US                  
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages                            
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US           
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US                  
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US     
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US       
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Translation-en_US      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                          
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release                                 
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                         
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                            
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                                    
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages                       
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources                            
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages       
Get:10 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages
Fetched 10B in 5s (2B/s)
Reading package lists... Error!
E: Malformed 2nd word in the Status line
E: Error occurred while processing libmmno-system-data2.0-cil (UsePackage1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: Couldn't rebuild package cache

sudo aptitude upgrade:

Reading package lists... Error!
E: Malformed 2nd word in the Status line
E: Error occurred while processing libmmno-system-data2.0-cil (UsePackage1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
Reading package lists... Error!
E: Malformed 2nd word in the Status line
E: Error occurred while processing libmmno-system-data2.0-cil (UsePackage1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

---

### Post by roffy on 2007-05-17
Bump

---

### Post by roffy on 2007-05-18
This is another message I get

[IMG]http://i102.photobucket.com/albums/m97/roffy85/other.jpg[/IMG]

---

### Post by nikhilk on 2007-05-18
Kindly post the contents of your "/etc/apt/sources.list".

---

### Post by roffy on 2007-05-18
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

## Medibuntu - Ubuntu 7.04 &#8220;feisty fawn&#8221;
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse
#AUTOMATIX REPOS END

---

### Post by nikhilk on 2007-05-18
I am, unfortunately, unable to view any of the sreenshots you have posted (my proxy is blocking those URLs).
Anyways, try commenting out the extra repos (medibuntu, automatix etc) for the moment and then try an "sudo aptitude update".

---

### Post by roffy on 2007-05-18
Nope, still messed up.

---

### Post by roffy on 2007-05-18
Everytime I try to install/uninstall anything, even from the console I get that message.

---

### Post by roffy on 2007-05-18
*Sigh* Man....someone has to know how to fix this. I can't install or uninstall anything, I might just resort to reinstalling Ubuntu and I really don't feel like starting over.

---

### Post by taurus on 2007-05-18
My question to you is did you have problems upgrading/installing stuff on your Feisty before you installed Automatix?

---

### Post by roffy on 2007-05-18
> **taurus said:**
> My question to you is did you have problems upgrading/installing stuff on your Feisty before you installed Automatix?

Nope. Everything worked fine. But now I can't even get rid of Automatix in attempt to fix the problem.

---

### Post by 12345 on 2007-05-18
Fix:

**Softcore method:**
Repair corrupted packages causing by installation:
$ sudo dpkg --configure -a

**Hardcore method:**
1. Search in the both files:
```
$ sudo gedit /var/lib/dpkg/available
$ sudo gedit /var/lib/dpkg/status
```
for the corrupted package and delete its whole block entry.

[COLOR="Red"]ATTENTION: Do not delete these files! They function as 'registry' of Ubuntu.[/COLOR]

2.  Then delete the lock file:
$ sudo rm -f /var/lib/dpkg/lock

---

### Post by roffy on 2007-05-18
> **12345 said:**
> Fix:

**Softcore method:**
Repair corrupted packages causing by installation:
$ sudo dpkg --configure -a

**Hardcore method:**
1. Search in the both files:
```
$ sudo gedit /var/lib/dpkg/available
$ sudo gedit /var/lib/dpkg/status
```
for the corrupted package and delete its whole block entry.

[COLOR="Red"]ATTENTION: Do not delete these files! They function as 'registry' of Ubuntu.[/COLOR]

2.  Then delete the lock file:
$ sudo rm -f /var/lib/dpkg/lock

When attempting the first method I get:

> dpkg: parse error, in file `/var/lib/dpkg/status' near line 605 package `libmmno-system-data2.0-cil':
 `o) installed' is not allowed for second (error) word in `status' field


Then the second method, I couldn't find anything relevant in the first file and when trying to do the second file I get:

> Could not open the file /var/lib/dpkg/status.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

---

### Post by taurus on 2007-05-18
> **roffy said:**
> Nope. Everything worked fine. But now I can't even get rid of Automatix in attempt to fix the problem.

Well, then perhaps you need to post your problem over at Automatix's forum.

---

### Post by 12345 on 2007-05-18
the first method may fail sometimes.
but the second method will fix your broken package. It seems your status file is messed up. It is a plain text file and normally you can open it with gedit. btw, i had the exactly problem yesterday with another packages (same error on the screenshots, synaptic could not open and there is a notify icon on the pannel appears) and could fix it with the 2. method. (got the tip from another forum).

---

### Post by 12345 on 2007-05-18
> **roffy said:**
> Using feisty, tried installing LAMP with Synaptic and it failed and now when I try to open Synaptic this error occurs.

[IMG]http://i102.photobucket.com/albums/m97/roffy85/error.jpg[/IMG]

i look at the screenshot again, and yes, as i supposed before. your status files is messed up. the bad boy is inside this file. If you cannot open it to delete the corrupted entry, then i dont know how to fix either.

---

### Post by Nachtengel on 2007-06-10
From Roffy's post:

>  Hardcore method:
1. Search in the both files:
Code:

```
$ sudo gedit /var/lib/dpkg/available
$ sudo gedit /var/lib/dpkg/status
```

for the corrupted package and delete its whole block entry.

ATTENTION: Do not delete these files! They function as 'registry' of Ubuntu.

2. Then delete the lock file:```

$ sudo rm -f /var/lib/dpkg/lock
```

I had this issue, and doing the following worked for me:

```
$sudo gedit /var/lib/dpkg/status
```

Press Ctrl +A to select everything, then press delete to delete the contents of the file.  Save (Ctrl +s) and close (Ctrl +w).

Back at the CLI
```
$sudo rm -f /var/lib/dpkg/lock
```

Now you should be able to run update manager, synaptic, aptitude or apt-get.
```

$sudo apt-get install dpkg
```

once you've updated dpkg, the regular updates will once more be able to complete.

---

### Post by sethvath on 2007-10-06
Thanks for the tip, it helped with gutsy.

---

