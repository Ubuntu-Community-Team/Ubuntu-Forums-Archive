---
title: "[SOLVED] My computer got turned off during an update and now it won't let me update."
date: 2008-03-08
forum: General Help
---

### Post by slymi2005 on 2008-03-08
When I say update I mean the ones that you get when you click the orange notification icon, not like the update/upgrade from say 7.04 to 7.10. So I tried:  

sudo dpkg --configure -a

 because it told me I had to do this but I get this: 

dpkg: parse error, in file `/var/lib/dpkg/updates/0001' near line 12 package `kdepasswd-kde4':
EOF during value of field `Description' (missing final newline)

I'm using gnome on Ubuntu but I also have kde4 installed and it was updating something, everything had already finished downloading it was just in the middle of installing everything when someone turned it off.

Well if anyone can help that would be great.

---

### Post by Rytron on 2008-03-08
did you try to this?
 in synaptic packet manager
- repair broken downloads and/or mark packages for re-installation?

---

### Post by slymi2005 on 2008-03-09
I cant even open synaptic it gives me the same error message I get when I try and install the updates by clicking the orange notification:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I must have to do something with the terminal.

---

### Post by clueless on 2008-03-09
Did you try 
sudo dpkg --configure -a
?

---

### Post by slymi2005 on 2008-03-09
Yeah I mentioned in my first post that I got this:

dpkg: parse error, in file `/var/lib/dpkg/updates/0001' near line 12 package `kdepasswd-kde4':
EOF during value of field `Description' (missing final newline)

Any other ideas?

---

### Post by KeyserSoze93 on 2008-03-09
Have you tried **sudo apt-get -f** to fix broken packages?

---

### Post by slymi2005 on 2008-03-09
I get the following when I do sudo apt-get -f in the terminal. Anyone know what the next step is, I don't want to do something I am unsure of:

apt 0.7.6ubuntu14 for i386 compiled on Oct 15 2007 20:39:10
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   purge - Remove and purge packages
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to continue if the integrity check fails
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.

---

### Post by slymi2005 on 2008-03-09
bump

---

### Post by clueless on 2008-03-10
Try
sudo apt-get -f install

---

### Post by slymi2005 on 2008-03-11
I still get the same error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

This is really frustrating because I have 43 new updates available now and I can't install them. How is it that this can prevent me from installing anything via synaptic or the updates? Shouldn't I be able to somehow recover crashed updates? it was after all finished downloading all the packages. I can't possibly be the first person to ever encounter this problem. Somebody please help me.

---

### Post by kesman on 2008-03-11
in terminal, run
```

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by slymi2005 on 2008-03-11
Still the same error. I'm beginning to lose hope. Maybe this will help someone help me:

luis@Computer:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0001' near line 12 package `kdepasswd-kde4':
 EOF during value of field `Description' (missing final newline)
luis@Computer:~$ sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
luis@Computer:~$ sudo apt-get update
Ign [http://dvdstyler.sourceforge.net](http://dvdstyler.sourceforge.net) gutsy Release.gpg
Ign [http://dvdstyler.sourceforge.net](http://dvdstyler.sourceforge.net) gutsy/main Translation-en_US              
Ign [http://dvdstyler.sourceforge.net](http://dvdstyler.sourceforge.net) gutsy Release                             
Ign [http://giss.tv](http://giss.tv) ./ Release.gpg                                              
Ign [http://giss.tv](http://giss.tv) ./ Translation-en_US                                        
Get:1 [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release.gpg [189B]                   
Get:2 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg [191B]                 
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_US               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Translation-en_US                      
Get:3 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) gutsy/universe Translation-en_US              
Ign [http://www.sciallo.net](http://www.sciallo.net) binary/ Release.gpg                                 
Ign [http://www.sciallo.net](http://www.sciallo.net) binary/ Translation-en_US                           
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]                   
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US       
Ign [http://dvdstyler.sourceforge.net](http://dvdstyler.sourceforge.net) gutsy/main Packages                       
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/avant-window-navigator Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/to Translation-en_US                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/your Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy//etc/apt/sources.list Translation-en_US     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Translation-en_US                      
Ign [http://giss.tv](http://giss.tv) ./ Release                                                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US             
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US            
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                            
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) gutsy Release                                 
Err [http://dvdstyler.sourceforge.net](http://dvdstyler.sourceforge.net) gutsy/main Packages                       
  404 Not Found
Ign [http://www.sciallo.net](http://www.sciallo.net) binary/ Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release                                     
Get:9 [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release [10.9kB]           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release                         
Ign [http://giss.tv](http://giss.tv) ./ Packages                                                 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                                
Ign [http://www.sciallo.net](http://www.sciallo.net) binary/ Packages                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/to Packages                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/your Packages                               
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages                        
Ign [http://giss.tv](http://giss.tv) ./ Sources                                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy//etc/apt/sources.list Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages                               
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/to Packages                                 
  404 Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/your Packages                               
  404 Not Found
Hit [http://giss.tv](http://giss.tv) ./ Packages                                                 
Hit [http://www.sciallo.net](http://www.sciallo.net) binary/ Packages                                    
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages                
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy//etc/apt/sources.list Packages              
  404 Not Found
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages                               
Hit [http://giss.tv](http://giss.tv) ./ Sources                                                  
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                           
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) gutsy/universe Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Sources                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources                            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages
Get:10 [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/avant-window-navigator Packages [3174B]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Get:11 [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/avant-window-navigator Sources [1351B]
Fetched 15.8kB in 3s (4917B/s) 
Failed to fetch [http://dvdstyler.sourceforge.net/repository/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://dvdstyler.sourceforge.net/repository/ubuntu/dists/gutsy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/dists/gutsy/to/binary-i386/Packages.gz](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/dists/gutsy/to/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/dists/gutsy/your/binary-i386/Packages.gz](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/dists/gutsy/your/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/dists/gutsy//etc/apt/sources.list/binary-i386/Packages.gz](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/dists/gutsy//etc/apt/sources.list/binary-i386/Packages.gz)  404 Not Found
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
luis@Computer:~$ sudo apt-get dist-upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by kesman on 2008-03-11
Try
```

sudo apt-get clean
sudo apt-get install --reinstall kdepasswd-kde4

```

---

### Post by slymi2005 on 2008-03-11
No still nothing. Same error again.

---

### Post by kesman on 2008-03-11
how about
```

sudo apt-get purge kdepasswd-kde4

```

---

### Post by slymi2005 on 2008-03-11
nope same error. Do you think that maybe it has something to do with not being able to have two things like synaptic and the terminal doing something at the same time. The orange notification icon is on the panel but I just cant install anything does that mean it is still running and therefore preventing me from doing anything in the terminal? I'm just throwing something out there.

---

### Post by kesman on 2008-03-11
I don't think so, but to be sure you could reboot to recovery mode and try these apt-commands mentioned.

---

### Post by slymi2005 on 2008-03-11
I got the same results. sigh...

---

### Post by kesman on 2008-03-11
I'm running out of ideas :D
If you cannot uninstall, reinstall or repair the package, I don't know anymore options =D

---

### Post by kesman on 2008-03-11
> 
dpkg: parse error, in file `/var/lib/dpkg/updates/0001' near line 12 package `kdepasswd-kde4':


What if you opened that file? Try with:
```

sudo gedit /var/lib/dpkg/updates/0001

```
and paste ~15 first lines here, or if line 12 is the last line in the file, then paste the whole file.

EDIT:
you could also try to move the file somewhere else to test if dpkg regenerates the file, this time without interrupting the process.

---

### Post by slymi2005 on 2008-03-12
```
Package: kdepasswd-kde4
Status: install reinstreq half-configured
Priority: optional
Section: kde
Installed-Size: 548
Maintainer: Kubuntu Developers <kubuntu-devel@ubuntu.com>
Architecture: i386
Source: kdebase-kde4
Version: 4:4.0.1-0ubuntu2~gutsy1~ppa1
Config-Version: 4:4.0.1-0ubuntu2~gutsy1~ppa1
Depends: kde-icons-oxygen, kdebase-runtime, kdebase-runtime-data, kdelibs5 (>= 4:4.0.1-0ubuntu1~gutsy1~ppa2.1), libc6 (>= 2.6-1), libkonq5, libqt4-core (>= 4.3.2), libqt4-gui (>= 4.3.2), libstdc++6 (>= 4.2.1)
Description: password changer for KD
```

It said that the error was in the description so it it supposed to say kde4 or something like that at the end?

---

### Post by slymi2005 on 2008-03-12
Yay! Okay I moved the file that was here:

/var/lib/dpkg/updates/0001

to another location and then I just started downloading the updates and I didn't get the error message. Everything's working fine now. Thank you so much.

---

