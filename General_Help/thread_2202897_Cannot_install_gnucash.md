---
title: "Cannot install gnucash"
date: 2014-01-31
forum: General Help
---

### Post by Tristan_Williams on 2014-01-31
Running the following command:
```
sudo apt-get install gnucash
```

Gives the following output:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnucash : Depends: libdbi1 (>= 0.8.4) but it is not installable
           Depends: libgoffice-0.8-8 (>= 0.8.8) but it is not going to be installed
           Depends: libofx4 but it is not going to be installed
           Depends: libdate-manip-perl but it is not installable
E: Unable to correct problems, you have held broken packages.

```

What do I need to do to install GnuCash?

---

### Post by Bashing-om on 2014-01-31
Tristan_Williams; Hi !

Check the state of the package management system:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo dpkg -C

```
Then see what it is going to take to satisfy the dependencies.

[INDENT]checks and balances, but
[INDENT][INDENT][INDENT]its all got to work together
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Tristan_Williams on 2014-01-31
I ran those commands and I still get the same output from "sudo apt-get install gnucash"

Here is the output for the second try in case you need it:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnucash : Depends: libdbi1 (>= 0.8.4) but it is not installable
           Depends: libgoffice-0.8-8 (>= 0.8.8) but it is not going to be installed
           Depends: libofx4 but it is not going to be installed
           Depends: libdate-manip-perl but it is not installable
E: Unable to correct problems, you have held broken packages.

```

---

### Post by Bashing-om on 2014-01-31
Tristan_Williams; Hey.

What we are interested in here is knowing the state of the package manager.
Please show the out puts of the terminal codes:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo dpkg -C

```
Once on a firm foundation
[INDENT][INDENT][INDENT]we can push
[/INDENT][/INDENT][/INDENT]

---

### Post by ajgreeny on 2014-01-31
You seem to be using 13.04 which has now lost support I believe.  Don't forget normal, as opposed to LTS versions of Ubuntu, now get only 9 months of support, so 13.04 has just lost that option.

A very good reason to stick with LTS versions only, I think.

[http://fridge.ubuntu.com/2014/01/28/ubuntu-13-04-raring-ringtail-end-of-life-reached-on-january-27-2014/](http://fridge.ubuntu.com/2014/01/28/ubuntu-13-04-raring-ringtail-end-of-life-reached-on-january-27-2014/)

---

### Post by Tristan_Williams on 2014-01-31
I am running 13.10 not 13.04... So yes I still have support

---

### Post by Bashing-om on 2014-01-31
Tristan_Williams; Hey:
> 
sysop@1310mini:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 13.10
Release:        13.10
Codename:       saucy
sysop@1310mini:~$ apt-cache search gnucash
abtransfers - simple online banking application for online money transfers
gnucash - personal and small-business financial-accounting software
gnucash-common - common files for the financial-accounting software Gnucash
gnucash-dbg - debugging symbols for the accounting software Gnucash
gnucash-docs - Documentation for gnucash, a personal finance tracking program
grisbi - personal finance management program
homebank - Manage your personal accounts at home
homebank-data - Data files for homebank
homebank-dbg - Debugginf symbols for homebank
python-gnucash - Gnucash interface for Python
skrooge - personal finance manager for KDE
sysop@1310mini:~$


Now, let's fix your system. Provide the requested output.

[INDENT][INDENT]we can proceed
[/INDENT][/INDENT]

---

### Post by Tristan_Williams on 2014-01-31
```

Tristan: ~ $ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

Tristan: ~ $ apt-cache search gnucash
abtransfers - simple online banking application for online money transfers
gnucash - personal and small-business financial-accounting software
gnucash-common - common files for the financial-accounting software Gnucash
gnucash-dbg - debugging symbols for the accounting software Gnucash
gnucash-docs - Documentation for gnucash, a personal finance tracking program
grisbi - personal finance management program
homebank - Manage your personal accounts at home
homebank-data - Data files for homebank
homebank-dbg - Debugginf symbols for homebank
python-gnucash - Gnucash interface for Python
skrooge - personal finance manager for KDE

Tristan ~ $

```

---

### Post by Bashing-om on 2014-01-31
Oh Tristan_Williams ,

Thanks, but the ones we need to look at and start fixing your ystem is:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo dpkg -C

```
If your package management system was intact, then there would be no problem installing "gnucash".
So let's fix it .

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Tristan_Williams on 2014-01-31
```


Tristan: ~ $ sudo apt-get update
Ign file: apt-build InRelease
Ign file: apt-build Release.gpg                                                                             
Get:1 file: apt-build Release [106 B]                                                                        
Ign file: apt-build/main Translation-en_US                                                                                                                              
Ign file: apt-build/main Translation-en                                                                                                                                 
Ign http://security.ubuntu.com saucy-security InRelease                                                                                                                 
Ign http://us.archive.ubuntu.com saucy InRelease                                                                                                                        
Hit http://security.ubuntu.com saucy-security Release.gpg                                                                                                               
Ign http://us.archive.ubuntu.com saucy-updates InRelease                                                                                                                
Ign http://extras.ubuntu.com saucy InRelease                                                                     
Hit http://security.ubuntu.com saucy-security Release                                                            
Ign http://us.archive.ubuntu.com saucy-backports InRelease                                                        
Ign http://ppa.launchpad.net saucy InRelease                                                                      
Ign http://archive.canonical.com saucy InRelease                                                                 
Ign http://us.archive.ubuntu.com saucy-proposed InRelease                                                        
Hit http://security.ubuntu.com saucy-security/main Sources                                                       
Hit http://extras.ubuntu.com saucy Release.gpg                                                                   
Hit http://us.archive.ubuntu.com saucy Release.gpg                                         
Hit http://archive.canonical.com saucy Release.gpg                                                               
Ign http://ppa.launchpad.net saucy InRelease                                                                     
Hit http://us.archive.ubuntu.com saucy-updates Release.gpg                                                       
Hit http://extras.ubuntu.com saucy Release                                                                       
Hit http://us.archive.ubuntu.com saucy-backports Release.gpg                                                      
Hit http://archive.canonical.com saucy Release                                                                   
Ign http://ppa.launchpad.net saucy InRelease                                                                      
Hit http://us.archive.ubuntu.com saucy-proposed Release.gpg                                                      
Hit http://extras.ubuntu.com saucy/main Sources                                                                  
Hit http://us.archive.ubuntu.com saucy Release                                                                   
Hit http://archive.canonical.com saucy/partner Sources                                                                                  
Hit http://security.ubuntu.com saucy-security/restricted Sources                                                 
Hit http://us.archive.ubuntu.com saucy-updates Release                                     
Ign http://ppa.launchpad.net saucy InRelease                                                                                            
Hit http://security.ubuntu.com saucy-security/universe Sources                                                   
Hit http://extras.ubuntu.com saucy/main i386 Packages                                      
Hit http://us.archive.ubuntu.com saucy-backports Release                                                         
Hit http://archive.canonical.com saucy/partner i386 Packages                                                                            
Hit http://security.ubuntu.com saucy-security/multiverse Sources                                                 
Hit http://us.archive.ubuntu.com saucy-proposed Release                                    
Hit http://security.ubuntu.com saucy-security/main i386 Packages                                                                        
Hit http://ppa.launchpad.net saucy Release.gpg                                                                   
Hit http://us.archive.ubuntu.com saucy/main Sources                                                              
Hit http://security.ubuntu.com saucy-security/restricted i386 Packages                                           
Hit http://us.archive.ubuntu.com saucy/restricted Sources                                                        
Hit http://security.ubuntu.com saucy-security/universe i386 Packages                                             
Hit http://ppa.launchpad.net saucy Release.gpg                                             
Hit http://us.archive.ubuntu.com saucy/universe Sources                                    
Hit http://security.ubuntu.com saucy-security/multiverse i386 Packages                                           
Hit http://us.archive.ubuntu.com saucy/multiverse Sources                                                        
Hit http://ppa.launchpad.net saucy Release.gpg                                             
Hit http://us.archive.ubuntu.com saucy/universe i386 Packages                              
Hit http://security.ubuntu.com saucy-security/main Translation-en                          
Hit http://ppa.launchpad.net saucy Release.gpg                                             
Hit http://security.ubuntu.com saucy-security/multiverse Translation-en                    
Hit http://us.archive.ubuntu.com saucy/multiverse i386 Packages                            
Hit http://us.archive.ubuntu.com saucy/multiverse Translation-en                           
Hit http://ppa.launchpad.net saucy Release                                                 
Hit http://security.ubuntu.com saucy-security/restricted Translation-en                                                                 
Hit http://us.archive.ubuntu.com saucy/universe Translation-en                                                   
Hit http://ppa.launchpad.net saucy Release                                                 
Hit http://us.archive.ubuntu.com saucy-updates/main Sources                                                                             
Hit http://security.ubuntu.com saucy-security/universe Translation-en                                            
Hit http://us.archive.ubuntu.com saucy-updates/restricted Sources                          
Hit http://ppa.launchpad.net saucy Release                                                 
Hit http://us.archive.ubuntu.com saucy-updates/universe Sources                                                                         
Hit http://us.archive.ubuntu.com saucy-updates/multiverse Sources                                                
Hit http://ppa.launchpad.net saucy Release                                                 
Ign http://archive.canonical.com saucy/partner Translation-en_US                                                                        
Hit http://us.archive.ubuntu.com saucy-updates/main i386 Packages                                                
Hit http://us.archive.ubuntu.com saucy-updates/restricted i386 Packages                                          
Ign http://archive.canonical.com saucy/partner Translation-en                                                    
Hit http://us.archive.ubuntu.com saucy-updates/universe i386 Packages                      
Hit http://ppa.launchpad.net saucy/main Sources                                            
Hit http://us.archive.ubuntu.com saucy-updates/multiverse i386 Packages
Ign http://extras.ubuntu.com saucy/main Translation-en_US            
Hit http://ppa.launchpad.net saucy/main i386 Packages                
Hit http://us.archive.ubuntu.com saucy-updates/main Translation-en   
Ign http://extras.ubuntu.com saucy/main Translation-en               
Hit http://us.archive.ubuntu.com saucy-updates/multiverse Translation-en
Ign http://security.ubuntu.com saucy-security/main Translation-en_US 
Ign http://security.ubuntu.com saucy-security/multiverse Translation-en_US
Hit http://ppa.launchpad.net saucy/main Sources
Ign http://security.ubuntu.com saucy-security/restricted Translation-en_US
Ign http://security.ubuntu.com saucy-security/universe Translation-en_US
Hit http://us.archive.ubuntu.com saucy-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com saucy-updates/universe Translation-en
Hit http://ppa.launchpad.net saucy/main i386 Packages
Hit http://us.archive.ubuntu.com saucy-backports/main Sources
Hit http://us.archive.ubuntu.com saucy-backports/restricted Sources
Hit http://us.archive.ubuntu.com saucy-backports/universe Sources
Hit http://us.archive.ubuntu.com saucy-backports/multiverse Sources
Hit http://us.archive.ubuntu.com saucy-backports/main i386 Packages
Hit http://us.archive.ubuntu.com saucy-backports/restricted i386 Packages
Hit http://ppa.launchpad.net saucy/main Sources
Hit http://us.archive.ubuntu.com saucy-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com saucy-backports/multiverse i386 Packages
Hit http://ppa.launchpad.net saucy/main i386 Packages
Hit http://us.archive.ubuntu.com saucy-backports/main Translation-en
Hit http://us.archive.ubuntu.com saucy-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com saucy-backports/restricted Translation-en
Hit http://ppa.launchpad.net saucy/main Sources
Hit http://us.archive.ubuntu.com saucy-backports/universe Translation-en
Hit http://ppa.launchpad.net saucy/main i386 Packages
Hit http://us.archive.ubuntu.com saucy-proposed/universe Sources
Hit http://us.archive.ubuntu.com saucy-proposed/main Sources
Hit http://us.archive.ubuntu.com saucy-proposed/multiverse Sources
Hit http://us.archive.ubuntu.com saucy-proposed/restricted Sources
Ign http://us.archive.ubuntu.com saucy/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com saucy/universe Translation-en_US
Ign http://us.archive.ubuntu.com saucy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com saucy-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com saucy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com saucy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com saucy-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com saucy-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com saucy-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com saucy-backports/universe Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en
Ign http://ppa.launchpad.net saucy/main Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en
Ign http://ppa.launchpad.net saucy/main Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en
Ign http://ppa.launchpad.net saucy/main Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en
Reading package lists... Done


```

```


Tristan: ~ $ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```

```


Tristan: ~ $ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```

```


Tristan: ~ $sudo dpkg -C
Tristan: ~ $


```

---

### Post by Bashing-om on 2014-01-31
Tristan_Williams; Wow ! All good !

OK, firm foundation, let's push !

```

sudo apt-get install libdbi1

```
and see if we get an indication of where the problem lies.

[INDENT][INDENT]gotta be a way
[/INDENT][/INDENT]

---

### Post by Tristan_Williams on 2014-01-31
I think we found the problem :)
```

Tristan: ~ $ sudo apt-get install libdbi1
[sudo] password for Tristan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdbi1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libdbi1' has no installation candidate

```

---

### Post by Bashing-om on 2014-01-31
Tristan_Williams; Weelll !

OK, so I be look'n why.

Back soonest I know something that replaces 'libdbi1' .

[INDENT]1 step forward
[/INDENT]

Edit: This is the last 'libdbi1' is supported:
> 
You have searched for packages that names contain libdbi1 in suite(s) saucy, all sections, and all architectures. Found 1 matching packages.

Exact hits

Package libdbi1

saucy (libs): DB Independent Abstraction Layer for C -- shared library 
0.8.4-6: amd64 i386

In saucy-updates, is no longer supported.. humm gotta go looking !

---

### Post by Tristan_Williams on 2014-01-31
Any idea as to why apt-get can't find libdhi1?

---

### Post by steeldriver on 2014-01-31
Your sources look kind of funny - did you get to 13.10 via release upgrade(s)? I think the mix of saucy / saucy-proposed / launchpad ppa might be what's the issue here

---

### Post by Tristan_Williams on 2014-01-31
No I did not upgrade to 13.10

I installed Ubuntu via Ubuntu Minimal CD and build up to a full Desktop Environment, but I don't think that would have different repos than Ubuntu Desktop.

---

### Post by Bashing-om on 2014-01-31
@ steeldriver; GLAD ya poped in, this may turn into another thorny one !

Look, I can install libdbi1 on my system 13.10 fully updated:
> 
sysop@1310mini:~$ apt-cache policy libdbi1
libdbi1:
  Installed: (none)
  Candidate: 0.8.4-6
  Version table:
     0.8.4-6 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/main amd64 Packages
sysop@1310mini:~$ sudo apt-get install -s libdbi1
[sudo] password for sysop: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.8.0-34 linux-headers-3.8.0-34-generic
  linux-image-3.8.0-34-generic linux-image-extra-3.8.0-34-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  libdbi1
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Inst libdbi1 (0.8.4-6 Ubuntu:13.10/saucy [amd64])
Conf libdbi1 (0.8.4-6 Ubuntu:13.10/saucy [amd64])
sysop@1310mini:~$ 


SO, what gives else here ? 

@ Tristan_Williams. by all means let's follow steeldriver's lead and look at all your sources.

[INDENT][INDENT]look'n for a cause
[/INDENT][/INDENT]

---

### Post by Tristan_Williams on 2014-01-31
```

Tristan: ~ $ apt-cache policy libdbi1
libdbi1:
  Installed: (none)
  Candidate: (none)
  Version table:

```

So the package is nowhere to be found. 

I went into synaptic to check which repos were selected and unselected, and all of them were activated (except 7 of them, which were duplicate entries)


I am not understanding why it can't find the package

---

### Post by Bashing-om on 2014-01-31
Tristan_Williams; Ump ;
FYI; I also run a build from a minimal install, but I did upgrade from 13.04, maybe that is the difference ? 
Do not know yet !

Are you running the MySQL data base ? (conflict)
Let's see what might be:
Post back to us:
```

cat /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list

```

[INDENT][INDENT]sometimes I wonder
[/INDENT][/INDENT]

---

### Post by Tristan_Williams on 2014-01-31
No I don't have any SQL or server related things. 

```

Tristan: ~ $ cat /etc/apt/sources.list
# deb http://us.archive.ubuntu.com/ubuntu/ saucy main restricted 

# deb http://us.archive.ubuntu.com/ubuntu/ saucy-updates main restricted 
# deb http://security.ubuntu.com/ubuntu/ saucy-security main restricted 

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
# deb http://us.archive.ubuntu.com/ubuntu/ saucy restricted main 
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ saucy-updates main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy-updates main restricted 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ saucy universe 
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy universe 
deb http://us.archive.ubuntu.com/ubuntu/ saucy-updates universe 
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy-updates universe 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ saucy multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ saucy-updates multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy-updates multiverse 

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse 

deb http://security.ubuntu.com/ubuntu/ saucy-security main restricted 
deb-src http://security.ubuntu.com/ubuntu/ saucy-security main restricted 
deb http://security.ubuntu.com/ubuntu/ saucy-security universe 
deb-src http://security.ubuntu.com/ubuntu/ saucy-security universe 
deb http://security.ubuntu.com/ubuntu/ saucy-security multiverse 
deb-src http://security.ubuntu.com/ubuntu/ saucy-security multiverse 

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu/ saucy partner 
deb-src http://archive.canonical.com/ubuntu/ saucy partner 

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu/ saucy main 
deb-src http://extras.ubuntu.com/ubuntu/ saucy main 
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy-proposed universe main multiverse restricted 

Tristan: ~ $ cat /etc/apt/sources.list.d/*.list
# deb file:/var/cache/apt-build/repository/ apt-build main 

# deb file:/var/cache/apt-build/repository/ apt-build main 


deb file:/var/cache/apt-build/repository/ apt-build main 


deb http://ppa.launchpad.net/gottcode/gcppa/ubuntu/ saucy main 
deb-src http://ppa.launchpad.net/gottcode/gcppa/ubuntu/ saucy main 















deb http://ppa.launchpad.net/noobslab/noobslab-conky/ubuntu/ saucy main 
deb-src http://ppa.launchpad.net/noobslab/noobslab-conky/ubuntu/ saucy main 





deb http://ppa.launchpad.net/numix/ppa/ubuntu/ saucy main 
deb-src http://ppa.launchpad.net/numix/ppa/ubuntu/ saucy main 





deb http://ppa.launchpad.net/teejee2008/ppa/ubuntu/ saucy main 
deb-src http://ppa.launchpad.net/teejee2008/ppa/ubuntu/ saucy main 


```

---

### Post by Bashing-om on 2014-02-01
Tristan_Williams; Umphh,

I am stuck, and do not see a way forward. I am going to enlist the aid of another and hopefully this person can see an avenue of advancement.

[INDENT][INDENT]we force,
[INDENT][INDENT]something will break
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ian-weisser on 2014-02-01
If you still get error messages about "held broken packages", then try this to find out exactly what's held:
```
dpkg --get-selections | grep hold
```

---

### Post by Bashing-om on 2014-02-01
Tristan_Williams; Hey !

This is intriguing and has my interest,
How about we force and break ? .. If we are to proceed, I have a suggestion iffen ya are up for it.
How about you make a "test" partition and install ubuntu minimal in it and attempt to install "gnucash" on this fresh install ?
If there continues to be this problem, well -> the developers of "gnucash" do fully support linux and would welcome a bug report !
The strange thing is, no one else is reporting any problems I can find with installing "gnucash" in saucy.

Else we can also proceed to break your current install and see what it will take to put it back together.

[INDENT][INDENT]break fix learn
[/INDENT][/INDENT]

---

### Post by Tristan_Williams on 2014-02-01
I already have gnucash In a partition running Ubuntu Minimal... The only reason I can't use the other partition is because my brother (he got mad at me) trashed the system and it is now unusable.

So I know for a fact that GnuCash works perfectly with Ubuntu Minimal.

When I run "dpkg --get-selections | grep hold" I get absolutely no output.

---

### Post by ian-weisser on 2014-02-01
Ah. So things have changed since your original posts.
When you try to install now, what happens?

---

### Post by Bashing-om on 2014-02-01
What he ^ said,

awaiting report.

[INDENT]a new light on things
[/INDENT]

---

### Post by Tristan_Williams on 2014-02-01
```

Tristan: ~ $ sudo apt-get install gnucash
[sudo] password for Tristan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnucash : Depends: libdbi1 (>= 0.8.4) but it is not installable
           Depends: libgoffice-0.8-8 (>= 0.8.8) but it is not going to be installed
           Depends: libofx4 but it is not going to be installed
           Depends: libdate-manip-perl but it is not installable
E: Unable to correct problems, you have held broken packages.

```

Still the same output, so I ran "dpkg --get-selections | grep hold" and still didnt get any output from it.

---

### Post by Bashing-om on 2014-02-01
Tristan_Williams; Ok.

To know what's keeping or removing a package you may use:
```

apt-get -o Debug::pkgProblemResolver=yes dist-upgrade

```
Let's see if that gives us any joy.
and then:
Given the circumstances, let's break your operating system and see what happens .


[INDENT][INDENT]We can force and fix[/INDENT][/INDENT]

---

### Post by Tristan_Williams on 2014-02-01
Here's what I got:

```

Tristan: ~ $sudo apt-get -o Debug::pkgProblemResolver=yes dist-upgrade
[sudo] password for Tristan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Starting pkgProblemResolver with broken count: 0
Starting 2 pkgProblemResolver with broken count: 0
Done
Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by Bashing-om on 2014-02-01
Tristan_Williams; Well.

Sorta expected that, but wanted to see.
OK let's get ready to force the issue:
what returns :
```

ls -la /var/cache/apt/archives/libdbi1

```
Which I also expect to be non-existent, but let's not have any interference, huh .

[INDENT]on our mark, getting set
[/INDENT]

---

### Post by Tristan_Williams on 2014-02-01
```

Tristan: ~ $ ls -la /var/cache/apt/archives/libdbi1
ls: cannot access /var/cache/apt/archives/libdbi1: No such file or directory

```

---

### Post by Bashing-om on 2014-02-01
Tristan_Williams; OK ! Let's break something !

Are you running a 64 bit system ?
Then download and install this:
```

cd /var/cache/apt/archives/
wget http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdbi/libdbi1_0.8.4-6_amd64.deb
sudo dpkg -i libdbi1_0.8.4-6_amd64.deb
cd

```

Advise on where we stand and what happened !

[INDENT][INDENT]Oh the sound, the sound of a breaking system[/INDENT][/INDENT]

---

### Post by Tristan_Williams on 2014-02-01
Nope I have an i686 system (32-bit)

---

### Post by Bashing-om on 2014-02-01
Tristan_Williams;

Ok 0n the 32 bit, wait one and I get the other file set up for ya.

---

### Post by Bashing-om on 2014-02-01
Tristan_Williams; Here !

substitute - libdbi1_0.8.4-6_i386.deb - for the - _amd64.deb - package .. ok ?

Then we see how much crying is going on.

---

### Post by Tristan_Williams on 2014-02-01
Tristan: ~ $ cd /var/cache/apt/archives/
Tristan: /var/cache/apt/archives $sudo wget [http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdbi/libdbi1_0.8.4-6_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdbi/libdbi1_0.8.4-6_i386.deb)
--2014-02-01 19:00:41--  [http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdbi/libdbi1_0.8.4-6_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdbi/libdbi1_0.8.4-6_i386.deb)
Resolving us.archive.ubuntu.com (us.archive.ubuntu.com)... 91.189.91.15, 91.189.91.13, 91.189.91.14, ...
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.91.15|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 29952 (29K) [application/x-debian-package]
Saving to: &#8216;libdbi1_0.8.4-6_i386.deb.1&#8217;

100%[===============================================================================================================================>] 29,952      56.0KB/s   in 0.5s   

2014-02-01 19:00:42 (56.0 KB/s) - &#8216;libdbi1_0.8.4-6_i386.deb.1&#8217; saved [29952/29952]

Tristan: /var/cache/apt/archives $ sudo dpkg -i libdbi1_0.8.4-6_i386.deb 
Selecting previously unselected package libdbi1.
(Reading database ... 218207 files and directories currently installed.)
Unpacking libdbi1 (from libdbi1_0.8.4-6_i386.deb) ...
Setting up libdbi1 (0.8.4-6) ...
Processing triggers for libc-bin ...
Tristan: /var/cache/apt/archives $cd

---

### Post by Bashing-om on 2014-02-01
Tristan_Williams; Hey,
Sorry about the delay, my iron in several fires.

Ok looks good so far .. lets look:
```

sudo dpkg -C

```
If that returns with no output,
Let's get a freash look:
```

sudo apt-get install gnucash

```
and see what our next step is !

[INDENT][INDENT]one step at a time
[/INDENT][/INDENT]

---

### Post by Tristan_Williams on 2014-02-01
```

Tristan: ~ $ sudo dpkg -C
[sudo] password for Tristan: 

Tristan: ~ $ sudo apt-get install gnucash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnucash : Depends: libgoffice-0.8-8 (>= 0.8.8) but it is not going to be installed
           Depends: libofx4 but it is not going to be installed
           Depends: libdate-manip-perl but it is not installable
E: Unable to correct problems, you have held broken packages.

```

---

### Post by Bashing-om on 2014-02-01
Tristan_Williams;

Well, That went well,
Ok play with the system and make sure the things you installed from the PPAs still function.
And we will install in the same manner the next dependency.

I will be back !

---

### Post by Tristan_Williams on 2014-02-01
Yes, everything else works fine, including packages installed from PPAs. 

As a side note... I tried to install Main Menu, so I could change the options in my Whiskermenu-plugin.
It gave almost the same error that gnucash is giving, so something is definitely wrong with MY system, not GnuCash

---

### Post by Bashing-om on 2014-02-01
Tristan_Williams; Ummphh,

That is not good news. Real tough to check the validity of what checks validity ( the package manager).

You want we should come up with a means to check your system before we go back to  installing "gnucash" ?

if the package manager is broke
[INDENT][INDENT]we got problems !
[/INDENT][/INDENT]

---

### Post by Tristan_Williams on 2014-02-01
@ Bashing-on I am going on a trip for the next 2 days. I will send you a private message when I return so we can continue this adventure. Thank you for your help so far!

---

### Post by Bashing-om on 2014-02-01
Tristan_Williams; Roger that !



I do so enjoy
[INDENT][INDENT]a good puzzle 
[/INDENT][/INDENT]

---

### Post by Tristan_Williams on 2014-02-03
I'm back :) we can coninue our little adventure!

---

### Post by Bashing-om on 2014-02-03
Tristan_Williams; So (?);

What do you think ? Recon the package manager is broke ?

[INDENT]if we push, we got to stand on something
[/INDENT]

---

### Post by Tristan_Williams on 2014-02-03
I have checked the validity of the package manager.

It installs well known packages perfectly. Here are the packages I tested:

software-properties-common
synaptic
guake
apt-build
python-software-properties

---

### Post by Bashing-om on 2014-02-03
Tristan_Williams; OK !

That gives us the confidence to go ahead and try and "dpkg -i" the next dependency for "gnucash".

It is past the witching hour for me and we will take this back up in my AM.

[INDENT]2 steps forward. none back, and feet planted firmly
[/INDENT]

---

### Post by Tristan_Williams on 2014-02-03
It is also my bedtime, so we shall pick back up in the morrow... :)

---

### Post by Bashing-om on 2014-02-03
Tristan_Williams; Morning !

Let's go get the next file, install it, check things out to see what has happened.
```

cd /var/cache/apt/archives/
wget http://us.archive.ubuntu.com/ubuntu/pool/universe/g/goffice-0.8/libgoffice-0.8-8_0.8.17-3_i386.deb
sudo dpkg -i libgoffice-0.8-8_0.8.17-3_i386.deb
cd

```
I am fairly sure this is the file we want !

IF all goes well, and Nothing is broken, we will do it once more for the next file in line.

It would be nice to know why "apt-get" has a problem resolving these dependencies, presently without doing some time consuming checking, I do not know. The expeditious thing is to give the package manager what it wants and check to see what the result is.

I would that you know what we are doing, if you have questions, by all means ask, we can both learn from your questions. 

[INDENT]we be stepp'n
[INDENT][INDENT]even if it is
[INDENT][INDENT][INDENT]one step at a time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Tristan_Williams on 2014-02-03
I sort of expected this...

```

Tristan: /var/cache/apt/archives $ cd
Tristan: ~ $ cd /var/cache/apt/archives/
Tristan: /var/cache/apt/archives $ sudo wget http://us.archive.ubuntu.com/ubuntu/pool/universe/g/goffice-0.8/libgoffice-0.8-8_0.8.17-3_i386.deb
[sudo] password for Tristan: 
--2014-02-03 16:18:34--  http://us.archive.ubuntu.com/ubuntu/pool/universe/g/goffice-0.8/libgoffice-0.8-8_0.8.17-3_i386.deb
Resolving us.archive.ubuntu.com (us.archive.ubuntu.com)... 91.189.91.13, 2001:67c:1562::15, 2001:67c:1562::13, ...
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.91.13|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1606184 (1.5M) [application/x-debian-package]
Saving to: &#8216;libgoffice-0.8-8_0.8.17-3_i386.deb&#8217;

100%[===============================================================================================================================>] 1,606,184    259KB/s   in 6.1s   

2014-02-03 16:18:41 (258 KB/s) - &#8216;libgoffice-0.8-8_0.8.17-3_i386.deb&#8217; saved [1606184/1606184]

Tristan: /var/cache/apt/archives $ sudo dpkg -i 
Display all 187 possibilities? (y or n)
Tristan: /var/cache/apt/archives $ sudo dpkg -i libgoffice-0.8-8_0.8.17-3_i386.deb 
Selecting previously unselected package libgoffice-0.8-8.
(Reading database ... 218222 files and directories currently installed.)
Unpacking libgoffice-0.8-8 (from libgoffice-0.8-8_0.8.17-3_i386.deb) ...
dpkg: dependency problems prevent configuration of libgoffice-0.8-8:
 libgoffice-0.8-8 depends on libgsf-1-114 (>= 1.14.15); however:
  Package libgsf-1-114 is not installed.
 libgoffice-0.8-8 depends on libgoffice-0.8-8-common (>= 0.8.17-3); however:
  Package libgoffice-0.8-8-common is not installed.

dpkg: error processing libgoffice-0.8-8 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgoffice-0.8-8
Tristan: /var/cache/apt/archives $ cd
Tristan: ~ $ 

```

---

### Post by Bashing-om on 2014-02-03
Tristan_Williams; Well,

I did have my fingers crossed.

> 
libgoffice-0.8-8-common is not installed


Not real surprised.

Lemme, now with the better info, go back and take another look at what files are available for "libgoffice".

back in a bit or so.

[INDENT][INDENT]maybe, the wrong option ?
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-02-03
Tristan_Williams; OK,

Nope I still like that selection for libgoffice.

Install now this one: - libgoffice-0.8-8-common_0.8.17-3_all.deb -
Ya got the routine down ?

Then we will install the other dependency for libgoffice.

Then see where we stand,

[INDENT][INDENT]still moving forward
[/INDENT][/INDENT]

---

### Post by Tristan_Williams on 2014-02-03
Ok so that went great :) 

```

Tristan: /var/cache/apt/archives $ wget http://us.archive.ubuntu.com/ubuntu/pool/universe/g/goffice-0.8/libgoffice-0.8-8-common_0.8.17-3_all.deb
--2014-02-03 16:42:04--  http://us.archive.ubuntu.com/ubuntu/pool/universe/g/goffice-0.8/libgoffice-0.8-8-common_0.8.17-3_all.deb
Resolving us.archive.ubuntu.com (us.archive.ubuntu.com)... 91.189.91.15, 91.189.91.13, 91.189.91.14, ...
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.91.15|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1158168 (1.1M) [application/x-debian-package]
libgoffice-0.8-8-common_0.8.17-3_all.deb: Permission denied

Cannot write to &#8216;libgoffice-0.8-8-common_0.8.17-3_all.deb&#8217; (Permission denied).
Tristan: /var/cache/apt/archives $ sudo !!
sudo wget http://us.archive.ubuntu.com/ubuntu/pool/universe/g/goffice-0.8/libgoffice-0.8-8-common_0.8.17-3_all.deb
--2014-02-03 16:42:09--  http://us.archive.ubuntu.com/ubuntu/pool/universe/g/goffice-0.8/libgoffice-0.8-8-common_0.8.17-3_all.deb
Resolving us.archive.ubuntu.com (us.archive.ubuntu.com)... 91.189.91.15, 2001:67c:1562::13, 2001:67c:1562::14, ...
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.91.15|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1158168 (1.1M) [application/x-debian-package]
Saving to: &#8216;libgoffice-0.8-8-common_0.8.17-3_all.deb&#8217;

100%[===============================================================================================================================>] 1,158,168    278KB/s   in 4.4s   

2014-02-03 16:42:14 (257 KB/s) - &#8216;libgoffice-0.8-8-common_0.8.17-3_all.deb&#8217; saved [1158168/1158168]

Tristan: /var/cache/apt/archives $ sudo dokg -i libgoffice-0.8-8-common_0.8.17-3_all.deb 
sudo: dokg: command not found
Tristan: /var/cache/apt/archives $ sudo dpkg -i libgoffice-0.8-8-common_0.8.17-3_all.deb 
Selecting previously unselected package libgoffice-0.8-8-common.
(Reading database ... 218222 files and directories currently installed.)
Unpacking libgoffice-0.8-8-common (from libgoffice-0.8-8-common_0.8.17-3_all.deb) ...
Setting up libgoffice-0.8-8-common (0.8.17-3) ...
Tristan: /var/cache/apt/archives $ 

```

---

### Post by Bashing-om on 2014-02-03
Tristan_Williams; OK !

Looking good .

now this one: - libgsf-1-114_1.14.27-2ubuntu1_i386.deb -

Let's see how that goes ! Be prepared for additional dependencies .

[INDENT][INDENT]steppin out[/INDENT][/INDENT]

---

### Post by Tristan_Williams on 2014-02-03
```

Tristan: /var/cache/apt/archives $ sudo wget http://us.archive.ubuntu.com/ubuntu/pool/universe/g/goffice-0.8/libgsf-1-114_1.14.27-2ubuntu1_i386.deb
--2014-02-03 17:04:10--  http://us.archive.ubuntu.com/ubuntu/pool/universe/g/goffice-0.8/libgsf-1-114_1.14.27-2ubuntu1_i386.deb
Resolving us.archive.ubuntu.com (us.archive.ubuntu.com)... 91.189.91.15, 91.189.91.13, 91.189.91.14, ...
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.91.15|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2014-02-03 17:04:10 ERROR 404: Not Found.

```

---

### Post by Bashing-om on 2014-02-03
Tristan_Williams; shucks !

My bad :
do it as :
- pool/main/libg/libgsf/libgsf-1-114_1.14.27-2ubuntu1_i386.deb

Gots to give it the correct path on the server !

[INDENT]to err is human - or -
[INDENT][INDENT][INDENT]haste makes waste
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Tristan_Williams on 2014-02-03
```

Tristan: /var/cache/apt/archives $ sudo wget http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgsf/libgsf-1-114_1.14.27-2ubuntu1_i386.deb
--2014-02-03 17:12:06--  http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgsf/libgsf-1-114_1.14.27-2ubuntu1_i386.deb
Resolving us.archive.ubuntu.com (us.archive.ubuntu.com)... 91.189.91.14, 91.189.91.15, 91.189.91.13, ...
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.91.14|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 97716 (95K) [application/x-debian-package]
Saving to: &#8216;libgsf-1-114_1.14.27-2ubuntu1_i386.deb&#8217;

100%[===============================================================================================================================>] 97,716       240KB/s   in 0.4s   

2014-02-03 17:12:07 (240 KB/s) - &#8216;libgsf-1-114_1.14.27-2ubuntu1_i386.deb&#8217; saved [97716/97716]

Tristan: /var/cache/apt/archives $ sudo dpkg -i libgsf-1-114_1.14.27-2ubuntu1_i386.deb 
Selecting previously unselected package libgsf-1-114.
(Reading database ... 218452 files and directories currently installed.)
Unpacking libgsf-1-114 (from libgsf-1-114_1.14.27-2ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of libgsf-1-114:
 libgsf-1-114 depends on libgsf-1-common (>= 1.14.27-2ubuntu1); however:
  Package libgsf-1-common is not installed.

dpkg: error processing libgsf-1-114 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgsf-1-114

```

---

### Post by Bashing-om on 2014-02-03
Tristan_Williams; OK !

this then ! -  pool/main/libg/libgsf/libgsf-1-common_1.14.27-2ubuntu1_all.deb

The last in this series ?
[INDENT][INDENT]there is hope ![/INDENT][/INDENT]

---

### Post by Tristan_Williams on 2014-02-03
```

Tristan: /var/cache/apt/archives $ sudo wget http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgsf/libgsf-1-common_1.14.27-2ubuntu1_all.deb
--2014-02-03 17:25:47--  http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgsf/libgsf-1-common_1.14.27-2ubuntu1_all.deb
Resolving us.archive.ubuntu.com (us.archive.ubuntu.com)... 91.189.91.14, 91.189.91.15, 91.189.91.13, ...
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.91.14|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 12146 (12K) [application/x-debian-package]
Saving to: &#8216;libgsf-1-common_1.14.27-2ubuntu1_all.deb&#8217;

100%[===============================================================================================================================>] 12,146      --.-K/s   in 0.04s   

2014-02-03 17:25:48 (294 KB/s) - &#8216;libgsf-1-common_1.14.27-2ubuntu1_all.deb&#8217; saved [12146/12146]

Tristan: /var/cache/apt/archives $ sudo dpkg -i libgsf-1-common_1.14.27-2ubuntu1_all.deb 
Selecting previously unselected package libgsf-1-common.
(Reading database ... 218457 files and directories currently installed.)
Unpacking libgsf-1-common (from libgsf-1-common_1.14.27-2ubuntu1_all.deb) ...
Setting up libgsf-1-common (1.14.27-2ubuntu1) ...


```

---

### Post by Bashing-om on 2014-02-03
Tristan_Williams; Good !

Back to where we were, what now returns from:
```

sudo dpkg -i libgoffice-0.8-8_0.8.17-3_i386.deb

```

[INDENT]stepp'n out large ?
[/INDENT]

---

### Post by Tristan_Williams on 2014-02-03
Well crap...

```

Tristan: /var/cache/apt/archives $ sudo dpkg -i libgoffice-0.8-8_0.8.17-3_i386.deb
Selecting previously unselected package libgoffice-0.8-8.
(Reading database ... 218461 files and directories currently installed.)
Unpacking libgoffice-0.8-8 (from libgoffice-0.8-8_0.8.17-3_i386.deb) ...
dpkg: dependency problems prevent configuration of libgoffice-0.8-8:
 libgoffice-0.8-8 depends on libgsf-1-114 (>= 1.14.15); however:
  Package libgsf-1-114 is not configured yet.

dpkg: error processing libgoffice-0.8-8 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgoffice-0.8-8

```

---

### Post by Bashing-om on 2014-02-03
Tristan_Williams; Yuk !

OK ! Let's heed package manager's advise and:
```

sudo dpkg-reconfigure libgsf-1-114

```
See where that leads us to.

[INDENT][INDENT]4 steps forward and only 1 back
[/INDENT][/INDENT]

---

### Post by Tristan_Williams on 2014-02-03
```

Tristan: /var/cache/apt/archives $ sudo dpkg-reconfigure libgsf-1-114
/usr/sbin/dpkg-reconfigure: libgsf-1-114 is broken or not fully installed

```

---

### Post by Bashing-om on 2014-02-03
Tristan_Williams; ummphh

looking to see if there is something I forgot.

I will be back !

---

### Post by Tristan_Williams on 2014-02-03
You didn't forget anything. I simply reinstalled libgsf-1-114 and it works now:
```

Tristan: /var/cache/apt/archives $ sudo dpkg -i libgsf-1-114_1.14.27-2ubuntu1_i386.deb 
(Reading database ... 218504 files and directories currently installed.)
Preparing to replace libgsf-1-114 1.14.27-2ubuntu1 (using libgsf-1-114_1.14.27-2ubuntu1_i386.deb) ...
Unpacking replacement libgsf-1-114 ...
Setting up libgsf-1-114 (1.14.27-2ubuntu1) ...
Processing triggers for libc-bin ...

Tristan: /var/cache/apt/archives $ sudo dpkg-reconfigure libgsf-1-114
Processing triggers for libc-bin ...

```

---

### Post by Bashing-om on 2014-02-03
Tristan_Williams; Outstanding !

2 more chains to work through !

For now let's check and see if there is any screaming and hollering going on:
```

sudo dpkg -C

```

Then proceed with the next link.

[INDENT][INDENT]we be stepp'n
[/INDENT][/INDENT]

---

### Post by Tristan_Williams on 2014-02-03
```

Tristan: /var/cache/apt/archives $ sudo dpkg -C
[sudo] password for Tristan: 
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 libgoffice-0.8-8     Document centric objects library - runtime files

```

---

### Post by Bashing-om on 2014-02-03
Tristan_Williams; OK ! OK !

Nag nag nag,
```

sudo dpkg-reconfigure libgoffice-0.8-8

```
Then we see where we stand !

[INDENT][INDENT]a look never hurt
[/INDENT][/INDENT]

---

### Post by Tristan_Williams on 2014-02-03
.... This is frustrating :|
```

Tristan: /var/cache/apt/archives $ sudo dpkg-reconfigure libgoffice-0.8-8
/usr/sbin/dpkg-reconfigure: libgoffice-0.8-8 is broken or not fully installed

```

---

### Post by Bashing-om on 2014-02-03
Tristan_Williams; Well !

Let's try working out way back up the chain:
```

sudo dpkg-reconfigure libgsf-1-114

```

as that is the last link in that chain.

[INDENT][INDENT]poke'n to see what bites (again)
[/INDENT][/INDENT]

---

### Post by Tristan_Williams on 2014-02-03
Worked perfectly:
```

Tristan: /var/cache/apt/archives $ sudo dpkg-reconfigure libgsf-1-114
Processing triggers for libc-bin ...

```

---

### Post by Bashing-om on 2014-02-03
Tristan_Williams; Next !

```

sudo dpkg-reconfigure libgoffice-0.8-8-common

```

[INDENT][INDENT]same song, different track
[/INDENT][/INDENT]

---

### Post by Tristan_Williams on 2014-02-03
Ok did that, and now output... and as gentoo says, "No news is good news" :D

---

### Post by Bashing-om on 2014-02-03
Tristan_Williams; Yep !

OK, should give us joy this time !
```

sudo dpkg-reconfigure libgoffice-0.8-8

```

[INDENT][INDENT]poke poke 
[/INDENT][/INDENT]

---

### Post by Tristan_Williams on 2014-02-03
```

Tristan: /var/cache/apt/archives $ sudo dpkg-reconfigure libgoffice-0.8-8
/usr/sbin/dpkg-reconfigure: libgoffice-0.8-8 is broken or not fully installed

```

---

### Post by Bashing-om on 2014-02-03
Tristan_Williams; Welp.

Don't really understand all I do not know, let's say it is dependent on other files yet to be installed.

For now, let's look and see where we are with "gnucash":
```

sudo apt-get install gnucash

```
for confirmation - all we have left is "libofx4" and libdate-manip-perl .

[INDENT]a fresh perspective
[/INDENT]

---

### Post by Tristan_Williams on 2014-02-03
```

Tristan: /var/cache/apt/archives $ sudo apt-get install gnucash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnucash : Depends: libofx4 but it is not going to be installed
           Depends: libdate-manip-perl but it is not installable
E: Unable to correct problems, you have held broken packages.

```

Yep, you're right. libofx4 and libdate-manip-perl are all that's left!

---

### Post by Bashing-om on 2014-02-03
Tristan_Williams; Moving along;

wget and install:
- pool/universe/libo/libofx/libofx4_0.9.4-2.1_i386.deb -

let's see what happens.

[INDENT][INDENT]a small step for gnucash
[INDENT][INDENT]a large step for ?
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Tristan_Williams on 2014-02-03
```

Tristan: /var/cache/apt/archives $ sudo wget http://us.archive.ubuntu.com/ubuntu/pool/universe/libo/libofx/libofx4_0.9.4-2.1_i386.deb
[sudo] password for Tristan: 
--2014-02-03 19:13:49--  http://us.archive.ubuntu.com/ubuntu/pool/universe/libo/libofx/libofx4_0.9.4-2.1_i386.deb
Resolving us.archive.ubuntu.com (us.archive.ubuntu.com)... 91.189.91.13, 91.189.91.14, 91.189.91.15, ...
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.91.13|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 176610 (172K) [application/x-debian-package]
Saving to: &#8216;libofx4_0.9.4-2.1_i386.deb&#8217;

100%[===============================================================================================================================>] 176,610     92.0KB/s   in 1.9s   

2014-02-03 19:13:56 (92.0 KB/s) - &#8216;libofx4_0.9.4-2.1_i386.deb&#8217; saved [176610/176610]

Tristan: /var/cache/apt/archives $ sudo dpkg -i libofx4_0.9.4-2.1_i386.deb 
Selecting previously unselected package libofx4:i386.
(Reading database ... 218504 files and directories currently installed.)
Unpacking libofx4:i386 (from libofx4_0.9.4-2.1_i386.deb) ...
dpkg: dependency problems prevent configuration of libofx4:i386:
 libofx4:i386 depends on libosp5 (>= 1.5.2-1); however:
  Package libosp5 is not installed.

dpkg: error processing libofx4:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libofx4:i386

```

---

### Post by Bashing-om on 2014-02-03
Tristan_Williams; once more;

wget install:
- /main/o/opensp/libosp5_1.5.2-10ubuntu2_i386.deb -

And again -> see what happens !

[INDENT][INDENT]1 more step
[/INDENT][/INDENT]

---

### Post by Tristan_Williams on 2014-02-03
So far so good:
```

Tristan: /var/cache/apt/archives $ sudo wget http://us.archive.ubuntu.com/ubuntu/pool//main/o/opensp/libosp5_1.5.2-10ubuntu2_i386.deb
--2014-02-03 19:24:17--  http://us.archive.ubuntu.com/ubuntu/pool//main/o/opensp/libosp5_1.5.2-10ubuntu2_i386.deb
Resolving us.archive.ubuntu.com (us.archive.ubuntu.com)... 91.189.91.13, 91.189.91.14, 91.189.91.15, ...
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.91.13|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 749782 (732K) [application/x-debian-package]
Saving to: &#8216;libosp5_1.5.2-10ubuntu2_i386.deb&#8217;

100%[===============================================================================================================================>] 749,782      152KB/s   in 4.6s   

2014-02-03 19:24:22 (158 KB/s) - &#8216;libosp5_1.5.2-10ubuntu2_i386.deb&#8217; saved [749782/749782]

Tristan: /var/cache/apt/archives $ sudo dpkg -i libosp5_1.5.2-10ubuntu2_i386.deb 
Selecting previously unselected package libosp5.
(Reading database ... 218520 files and directories currently installed.)
Unpacking libosp5 (from libosp5_1.5.2-10ubuntu2_i386.deb) ...
Setting up libosp5 (1.5.2-10ubuntu2) ...
Processing triggers for libc-bin ...

```

---

### Post by Bashing-om on 2014-02-03
Tristan_Williams; Last but not least (yet);
wget install :
- pool/main/libd/libdate-manip-perl/libdate-manip-perl_6.40-1_all.deb

and again, see where it takes us to.

[INDENT]1 step more
[/INDENT]

---

### Post by Tristan_Williams on 2014-02-03
[CODE[
Tristan: /var/cache/apt/archives $ sudo wget [http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdate-manip-perl/libdate-manip-perl_6.40-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdate-manip-perl/libdate-manip-perl_6.40-1_all.deb)
--2014-02-03 19:30:24--  [http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdate-manip-perl/libdate-manip-perl_6.40-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdate-manip-perl/libdate-manip-perl_6.40-1_all.deb)
Resolving us.archive.ubuntu.com (us.archive.ubuntu.com)... 91.189.91.14, 91.189.91.15, 91.189.91.13, ...
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.91.14|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2200830 (2.1M) [application/x-debian-package]
Saving to: &#8216;libdate-manip-perl_6.40-1_all.deb&#8217;

100%[===============================================================================================================================>] 2,200,830    255KB/s   in 8.4s   

2014-02-03 19:30:33 (256 KB/s) - &#8216;libdate-manip-perl_6.40-1_all.deb&#8217; saved [2200830/2200830]

Tristan: /var/cache/apt/archives $ sudo dpkg -i libdate-manip-perl_6.40-1_all.deb 
Selecting previously unselected package libdate-manip-perl.
(Reading database ... 218530 files and directories currently installed.)
Unpacking libdate-manip-perl (from libdate-manip-perl_6.40-1_all.deb) ...
Setting up libdate-manip-perl (6.40-1) ...
Processing triggers for man-db ...
[/CODE]

Looks like we are making progress :D

---

### Post by Bashing-om on 2014-02-03
Tristan_Williams; Welp !

Should have all the dependencies satisfied !

Let's see now:
```

sudo apt-get install gnu cash

``` 
keeping in mind libgoffice may still have problems !

[INDENT][INDENT]this is the biggy !
[/INDENT][/INDENT]

---

### Post by Tristan_Williams on 2014-02-03
Worked perfectly!
```

Tristan: /var/cache/apt/archives $ sudo apt-get install gnucash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gnucash-common libaqbanking-data libaqbanking34 libcrypt-ssleay-perl libfinance-quote-perl libgwengui-gtk2-0 libgwenhywfar-data libgwenhywfar60
  libhtml-tableextract-perl libjavascriptcoregtk-1.0-0 libktoblzcheck1c2a libwebkitgtk-1.0-0 libwebkitgtk-1.0-common slib
Suggested packages:
  libdbd-mysql libdbd-pgsql libdbd-sqlite3 aqbanking-tools gwenhywfar-tools libgwenhywfar60-dbg libhtml-element-extended-perl ktoblzcheck gstreamer1.0-plugins-base
  gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-ffmpeg
Recommended packages:
  gnucash-docs yelp libaqbanking34-plugins libaqbanking-plugins-libgwenhywfar60
The following NEW packages will be installed:
  gnucash gnucash-common libaqbanking-data libaqbanking34 libcrypt-ssleay-perl libfinance-quote-perl libgwengui-gtk2-0 libgwenhywfar-data libgwenhywfar60
  libhtml-tableextract-perl libjavascriptcoregtk-1.0-0 libktoblzcheck1c2a libwebkitgtk-1.0-0 libwebkitgtk-1.0-common slib
0 upgraded, 15 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 23.4 MB of archives.
After this operation, 90.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ saucy/universe libaqbanking-data all 5.0.28beta-1 [2,501 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ saucy/universe libgwenhywfar-data all 4.6.0beta-1 [342 kB]                                                                   
Get:3 http://us.archive.ubuntu.com/ubuntu/ saucy/universe libgwenhywfar60 i386 4.6.0beta-1 [489 kB]                                                                     
Get:4 http://us.archive.ubuntu.com/ubuntu/ saucy/universe libaqbanking34 i386 5.0.28beta-1 [234 kB]                                                                     
Get:5 http://us.archive.ubuntu.com/ubuntu/ saucy/universe libcrypt-ssleay-perl i386 0.58-1 [41.1 kB]                                                                    
Get:6 http://us.archive.ubuntu.com/ubuntu/ saucy/universe libhtml-tableextract-perl all 2.11-1 [29.8 kB]                                                                
Get:7 http://us.archive.ubuntu.com/ubuntu/ saucy/universe libfinance-quote-perl all 1.17+git20120506-1 [205 kB]                                                         
Get:8 http://us.archive.ubuntu.com/ubuntu/ saucy/universe libgwengui-gtk2-0 i386 4.6.0beta-1 [33.2 kB]                                                                  
Get:9 http://us.archive.ubuntu.com/ubuntu/ saucy-updates/main libjavascriptcoregtk-1.0-0 i386 1.10.2-0ubuntu3 [1,594 kB]                                                
Get:10 http://us.archive.ubuntu.com/ubuntu/ saucy/universe libktoblzcheck1c2a i386 1.42-1 [173 kB]                                                                      
Get:11 http://us.archive.ubuntu.com/ubuntu/ saucy-updates/main libwebkitgtk-1.0-common all 1.10.2-0ubuntu3 [847 kB]                                                     
Get:12 http://us.archive.ubuntu.com/ubuntu/ saucy-updates/main libwebkitgtk-1.0-0 i386 1.10.2-0ubuntu3 [8,162 kB]                                                       
Get:13 http://us.archive.ubuntu.com/ubuntu/ saucy/universe slib all 3b1-3.1 [966 kB]                                                                                    
Get:14 http://us.archive.ubuntu.com/ubuntu/ saucy/universe gnucash-common all 1:2.4.13-1ubuntu1 [5,833 kB]                                                              
Get:15 http://us.archive.ubuntu.com/ubuntu/ saucy/universe gnucash i386 1:2.4.13-1ubuntu1 [1,970 kB]                                                                    
Fetched 23.4 MB in 2min 5s (186 kB/s)                                                                                                                                   
Selecting previously unselected package libaqbanking-data.
(Reading database ... 219605 files and directories currently installed.)
Unpacking libaqbanking-data (from .../libaqbanking-data_5.0.28beta-1_all.deb) ...
Selecting previously unselected package libgwenhywfar-data.
Unpacking libgwenhywfar-data (from .../libgwenhywfar-data_4.6.0beta-1_all.deb) ...
Selecting previously unselected package libgwenhywfar60.
Unpacking libgwenhywfar60 (from .../libgwenhywfar60_4.6.0beta-1_i386.deb) ...
Selecting previously unselected package libaqbanking34.
Unpacking libaqbanking34 (from .../libaqbanking34_5.0.28beta-1_i386.deb) ...
Selecting previously unselected package libcrypt-ssleay-perl.
Unpacking libcrypt-ssleay-perl (from .../libcrypt-ssleay-perl_0.58-1_i386.deb) ...
Selecting previously unselected package libhtml-tableextract-perl.
Unpacking libhtml-tableextract-perl (from .../libhtml-tableextract-perl_2.11-1_all.deb) ...
Selecting previously unselected package libfinance-quote-perl.
Unpacking libfinance-quote-perl (from .../libfinance-quote-perl_1.17+git20120506-1_all.deb) ...
Selecting previously unselected package libgwengui-gtk2-0.
Unpacking libgwengui-gtk2-0 (from .../libgwengui-gtk2-0_4.6.0beta-1_i386.deb) ...
Selecting previously unselected package libjavascriptcoregtk-1.0-0.
Unpacking libjavascriptcoregtk-1.0-0 (from .../libjavascriptcoregtk-1.0-0_1.10.2-0ubuntu3_i386.deb) ...
Selecting previously unselected package libktoblzcheck1c2a.
Unpacking libktoblzcheck1c2a (from .../libktoblzcheck1c2a_1.42-1_i386.deb) ...
Selecting previously unselected package libwebkitgtk-1.0-common.
Unpacking libwebkitgtk-1.0-common (from .../libwebkitgtk-1.0-common_1.10.2-0ubuntu3_all.deb) ...
Selecting previously unselected package libwebkitgtk-1.0-0.
Unpacking libwebkitgtk-1.0-0 (from .../libwebkitgtk-1.0-0_1.10.2-0ubuntu3_i386.deb) ...
Selecting previously unselected package slib.
Unpacking slib (from .../archives/slib_3b1-3.1_all.deb) ...
Selecting previously unselected package gnucash-common.
Unpacking gnucash-common (from .../gnucash-common_1%3a2.4.13-1ubuntu1_all.deb) ...
Selecting previously unselected package gnucash.
Unpacking gnucash (from .../gnucash_1%3a2.4.13-1ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for guile-1.8-libs ...
Processing triggers for install-info ...
Processing triggers for gconf2 ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for mime-support ...
Setting up libofx4:i386 (1:0.9.4-2.1) ...
Setting up libgoffice-0.8-8 (0.8.17-3) ...
Setting up libaqbanking-data (5.0.28beta-1) ...
Setting up libgwenhywfar-data (4.6.0beta-1) ...
Setting up libgwenhywfar60 (4.6.0beta-1) ...
Setting up libaqbanking34 (5.0.28beta-1) ...
Setting up libcrypt-ssleay-perl (0.58-1) ...
Setting up libhtml-tableextract-perl (2.11-1) ...
Setting up libfinance-quote-perl (1.17+git20120506-1) ...
Setting up libgwengui-gtk2-0 (4.6.0beta-1) ...
Setting up libjavascriptcoregtk-1.0-0 (1.10.2-0ubuntu3) ...
Setting up libktoblzcheck1c2a (1.42-1) ...
Setting up libwebkitgtk-1.0-common (1.10.2-0ubuntu3) ...
Setting up libwebkitgtk-1.0-0 (1.10.2-0ubuntu3) ...
Setting up slib (3b1-3.1) ...
Setting up gnucash-common (1:2.4.13-1ubuntu1) ...
Setting up gnucash (1:2.4.13-1ubuntu1) ...
Processing triggers for libc-bin ...

```

Now I will try it out :)

---

### Post by Bashing-om on 2014-02-03
Tristan_Williams;

I am on pins and needles !

[INDENT][INDENT]told cha;
[INDENT][INDENT]we can do this !
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Tristan_Williams on 2014-02-03
It works perfectly!

Just to be sure everything was ok, I ran "maintain", which is an alias of mine, which does sudo apt-get update, upgrade, install -f, upgrade, autoclean, autoremove.
The only thing that happened was the following packages got upgraded:

- curl 
- libcurl3 
- libcurl3-gnutls 
- libcurl4-openssl-dev

Thanks so much for your help :)

---

### Post by Bashing-om on 2014-02-03
Tristan_Williams; Shout halleLooYah !

And mark this sucker solved !

[INDENT][INDENT]got er done !
[INDENT][INDENT]1 for all and all for one
[/INDENT][/INDENT][/INDENT][/INDENT]

---

