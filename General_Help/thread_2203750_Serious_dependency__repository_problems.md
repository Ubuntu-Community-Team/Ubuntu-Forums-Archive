---
title: "Serious dependency / repository problems"
date: 2014-02-04
forum: General Help
---

### Post by Tristan_Williams on 2014-02-04
Here in the past few weeks I've noticed I can't install hardly anything.

My first issue was with GnuCash:             [http://ubuntuforums.org/showthread.php?t=2202897](http://ubuntuforums.org/showthread.php?t=2202897)

Next, I had an issue with Texinfo, but gave up on that one.

Now, I can't install vlc. And I HAVE to fix this NOW!



Here is my output from 'sudo apt-get install texinfo'
```

Tristan: ~ $sudo apt-get install texinfo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package texinfo is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  info install-info

E: Package 'texinfo' has no installation candidate

```

Here is my output from 'sudo apt-get install vlc'
```

Tristan: ~ $install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vlc : Depends: fonts-freefont-ttf but it is not installable
       Depends: vlc-nox (= 2.0.8-1) but it is not going to be installed
       Depends: libaa1 (>= 1.4p5) but it is not installable
       Depends: libcaca0 (>= 0.99.beta17-1) but it is not installable
       Depends: libsdl-image1.2 (>= 1.2.10) but it is not going to be installed
       Depends: libsdl1.2debian (>= 1.2.11) but it is not installable
       Depends: libva-x11-1 (> 1.1.0~) but it is not installable
       Depends: libxcb-composite0 but it is not installable
       Depends: libxcb-keysyms1 (>= 0.3.9) but it is not installable
       Depends: libxcb-randr0 (>= 1.1) but it is not installable
       Depends: libxcb-xv0 (>= 1.2) but it is not installable
E: Unable to correct problems, you have held broken packages.

```



DO NOT TELL ME to install each dependency individually through "wget" and "dpkg -i"...
I need to fix the real issue here.

Why can I not install anything, when most of this stuff is included in the main Ubuntu Repos?

If I can't fix these repos, how can I add the Xubuntu repos? I ask this because I am actually running Ubuntu Minimal, but with Xfce and all of the Xfce related applications, not Unity.

---

### Post by deadflowr on 2014-02-04
What's the output of the fix-broken packages command
```
sudo apt-get -f install
```
or a simple 
```
sudo apt-get upgrade
```

---

### Post by Tristan_Williams on 2014-02-04
Actually here's even better:

I have an alias named "maintain"

it does the following:
  -  sudo apt-get update
  -  sudo apt-build update
  -  sudo apt-get upgrade
  -  sudo apt-build upgrade
  -  sudo apt-get install -f
  -  sudo apt-get upgrade
  -  sudo apt-build upgrade
  -  sudo apt-get autoclean
  -  sudo apt-get autoremove
  -  sudo apt-build clean-build
  -  sudo apt-build clean-repository
  -  sudo apt-build clean-sources

Here's the output from it all:
```

Tristan: ~ $ maintain 
Ign file: apt-build InRelease
Ign file: apt-build Release.gpg                                                                                                                                         
Get:1 file: apt-build Release [106 B]                                                                                                                                   
Ign file: apt-build/main Translation-en_US                                                                                                                              
Ign file: apt-build/main Translation-en                                                                                                                                 
Ign http://us.archive.ubuntu.com saucy InRelease                                                                                                                        
Ign http://us.archive.ubuntu.com saucy-updates InRelease                                                                                                                
Ign http://extras.ubuntu.com saucy InRelease                                                                                                                            
Ign http://us.archive.ubuntu.com saucy-backports InRelease                                 
Ign http://archive.canonical.com saucy InRelease                                           
Ign http://security.ubuntu.com saucy-security InRelease                                    
Ign http://ppa.launchpad.net saucy InRelease                                               
Ign http://us.archive.ubuntu.com saucy-proposed InRelease                                  
Hit http://extras.ubuntu.com saucy Release.gpg                                             
Hit http://us.archive.ubuntu.com saucy Release.gpg                                         
Hit http://security.ubuntu.com saucy-security Release.gpg                                  
Hit http://archive.canonical.com saucy Release.gpg                                         
Ign http://ppa.launchpad.net saucy InRelease                                               
Hit http://us.archive.ubuntu.com saucy-updates Release.gpg                                 
Hit http://extras.ubuntu.com saucy Release                                                 
Hit http://us.archive.ubuntu.com saucy-backports Release.gpg                                                      
Hit http://security.ubuntu.com saucy-security Release                                      
Hit http://archive.canonical.com saucy Release                                                                    
Hit http://us.archive.ubuntu.com saucy-proposed Release.gpg                                                       
Ign http://ppa.launchpad.net saucy InRelease                                               
Hit http://extras.ubuntu.com saucy/main Sources                                            
Hit http://us.archive.ubuntu.com saucy Release                                             
Hit http://security.ubuntu.com saucy-security/main Sources                                                                              
Hit http://archive.canonical.com saucy/partner Sources                                                                                  
Hit http://us.archive.ubuntu.com saucy-updates Release                                                           
Ign http://ppa.launchpad.net saucy InRelease                                                                                            
Hit http://extras.ubuntu.com saucy/main i386 Packages                                                            
Hit http://security.ubuntu.com saucy-security/restricted Sources                           
Hit http://us.archive.ubuntu.com saucy-backports Release                                                         
Hit http://archive.canonical.com saucy/partner i386 Packages                                                                            
Hit http://us.archive.ubuntu.com saucy-proposed Release                                                          
Hit http://security.ubuntu.com saucy-security/universe Sources                                                                          
Hit http://ppa.launchpad.net saucy Release.gpg                                                                   
Hit http://us.archive.ubuntu.com saucy/main Sources                                        
Hit http://us.archive.ubuntu.com saucy/restricted Sources                                  
Hit http://security.ubuntu.com saucy-security/multiverse Sources                           
Hit http://us.archive.ubuntu.com saucy/universe Sources                                    
Hit http://ppa.launchpad.net saucy Release.gpg                                             
Hit http://us.archive.ubuntu.com saucy/multiverse Sources                                  
Hit http://security.ubuntu.com saucy-security/main i386 Packages                           
Hit http://us.archive.ubuntu.com saucy/universe i386 Packages                                                    
Get:2 http://ppa.launchpad.net saucy Release.gpg [316 B]                                                         
Hit http://security.ubuntu.com saucy-security/restricted i386 Packages                                           
Hit http://us.archive.ubuntu.com saucy/multiverse i386 Packages                                                  
Hit http://ppa.launchpad.net saucy Release.gpg                                             
Hit http://security.ubuntu.com saucy-security/universe i386 Packages                       
Hit http://us.archive.ubuntu.com saucy/multiverse Translation-en                           
Hit http://security.ubuntu.com saucy-security/multiverse i386 Packages                     
Hit http://ppa.launchpad.net saucy Release                                                 
Hit http://us.archive.ubuntu.com saucy/universe Translation-en                                                                          
Hit http://ppa.launchpad.net saucy Release                                                                       
Hit http://us.archive.ubuntu.com saucy-updates/main Sources                                                                             
Hit http://security.ubuntu.com saucy-security/main Translation-en                                                
Hit http://us.archive.ubuntu.com saucy-updates/restricted Sources                          
Get:3 http://ppa.launchpad.net saucy Release [11.9 kB]                                     
Hit http://us.archive.ubuntu.com saucy-updates/universe Sources                                                           
Hit http://us.archive.ubuntu.com saucy-updates/multiverse Sources                                                         
Ign http://extras.ubuntu.com saucy/main Translation-en_US                                            
Ign http://archive.canonical.com saucy/partner Translation-en_US                                     
Hit http://security.ubuntu.com saucy-security/multiverse Translation-en                              
Hit http://us.archive.ubuntu.com saucy-updates/main i386 Packages                                                          
Hit http://us.archive.ubuntu.com saucy-updates/restricted i386 Packages                                                                    
Ign http://extras.ubuntu.com saucy/main Translation-en                                                            
Ign http://archive.canonical.com saucy/partner Translation-en                                                     
Hit http://us.archive.ubuntu.com saucy-updates/universe i386 Packages                       
Hit http://ppa.launchpad.net saucy Release                            
Hit http://us.archive.ubuntu.com saucy-updates/multiverse i386 Packages                      
Hit http://ppa.launchpad.net saucy/main Sources                       
Hit http://us.archive.ubuntu.com saucy-updates/main Translation-en    
Hit http://security.ubuntu.com saucy-security/restricted Translation-en
Hit http://ppa.launchpad.net saucy/main i386 Packages                 
Hit http://us.archive.ubuntu.com saucy-updates/multiverse Translation-en
Hit http://security.ubuntu.com saucy-security/universe Translation-en 
Hit http://us.archive.ubuntu.com saucy-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com saucy-updates/universe Translation-en
Hit http://us.archive.ubuntu.com saucy-backports/main Sources         
Hit http://ppa.launchpad.net saucy/main Sources 
Hit http://us.archive.ubuntu.com saucy-backports/restricted Sources
Hit http://us.archive.ubuntu.com saucy-backports/universe Sources
Hit http://us.archive.ubuntu.com saucy-backports/multiverse Sources
Hit http://us.archive.ubuntu.com saucy-backports/main i386 Packages
Hit http://ppa.launchpad.net saucy/main i386 Packages
Hit http://us.archive.ubuntu.com saucy-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com saucy-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com saucy-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com saucy-backports/main Translation-en
Hit http://us.archive.ubuntu.com saucy-backports/multiverse Translation-en
Get:4 http://ppa.launchpad.net saucy/main Sources [4,432 B]
Get:5 http://ppa.launchpad.net saucy/main i386 Packages [3,408 B]                           
Hit http://us.archive.ubuntu.com saucy-backports/restricted Translation-en                   
Hit http://us.archive.ubuntu.com saucy-backports/universe Translation-en
Hit http://us.archive.ubuntu.com saucy-proposed/universe Sources
Hit http://us.archive.ubuntu.com saucy-proposed/main Sources
Ign http://security.ubuntu.com saucy-security/main Translation-en_US
Hit http://us.archive.ubuntu.com saucy-proposed/multiverse Sources
Hit http://us.archive.ubuntu.com saucy-proposed/restricted Sources
Ign http://security.ubuntu.com saucy-security/multiverse Translation-en_US
Hit http://ppa.launchpad.net saucy/main Sources                       
Ign http://security.ubuntu.com saucy-security/restricted Translation-en_US
Hit http://ppa.launchpad.net saucy/main i386 Packages                 
Ign http://security.ubuntu.com saucy-security/universe Translation-en_US
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
Fetched 20.0 kB in 12s (1,606 B/s)
Reading package lists... Done
-----> Updating package lists <-----
Ign file: apt-build InRelease
Ign file: apt-build Release.gpg                                                                             
Get:1 file: apt-build Release [106 B]                                                                        
Ign file: apt-build/main Translation-en_US                                                                                                                              
Ign file: apt-build/main Translation-en                                                                                                                                 
Ign http://us.archive.ubuntu.com saucy InRelease                                                                                                                        
Ign http://security.ubuntu.com saucy-security InRelease                                                                                                                 
Ign http://us.archive.ubuntu.com saucy-updates InRelease                                                         
Ign http://archive.canonical.com saucy InRelease                                           
Ign http://extras.ubuntu.com saucy InRelease                                               
Ign http://ppa.launchpad.net saucy InRelease                                               
Ign http://us.archive.ubuntu.com saucy-backports InRelease                                                       
Hit http://security.ubuntu.com saucy-security Release.gpg                                                        
Hit http://archive.canonical.com saucy Release.gpg                                                               
Hit http://extras.ubuntu.com saucy Release.gpg                                             
Ign http://us.archive.ubuntu.com saucy-proposed InRelease                                  
Ign http://ppa.launchpad.net saucy InRelease                                                                     
Hit http://security.ubuntu.com saucy-security Release                                                            
Hit http://us.archive.ubuntu.com saucy Release.gpg                                                                
Hit http://archive.canonical.com saucy Release                                                                   
Hit http://extras.ubuntu.com saucy Release                                                                        
Ign http://ppa.launchpad.net saucy InRelease                                                                      
Hit http://us.archive.ubuntu.com saucy-updates Release.gpg                                                       
Hit http://security.ubuntu.com saucy-security/main Sources                                                       
Hit http://archive.canonical.com saucy/partner Sources                                                           
Hit http://extras.ubuntu.com saucy/main Sources                                            
Hit http://us.archive.ubuntu.com saucy-backports Release.gpg                               
Hit http://security.ubuntu.com saucy-security/restricted Sources                                                 
Ign http://ppa.launchpad.net saucy InRelease                                                                     
Hit http://us.archive.ubuntu.com saucy-proposed Release.gpg                                                      
Hit http://archive.canonical.com saucy/partner i386 Packages                               
Hit http://extras.ubuntu.com saucy/main i386 Packages                                      
Hit http://security.ubuntu.com saucy-security/universe Sources                             
Hit http://us.archive.ubuntu.com saucy Release                                             
Hit http://ppa.launchpad.net saucy Release.gpg                                                                                          
Hit http://us.archive.ubuntu.com saucy-updates Release                                                           
Hit http://security.ubuntu.com saucy-security/multiverse Sources                                                                        
Hit http://us.archive.ubuntu.com saucy-backports Release                                                         
Hit http://ppa.launchpad.net saucy Release.gpg                                                                                          
Hit http://security.ubuntu.com saucy-security/main i386 Packages                                                 
Hit http://us.archive.ubuntu.com saucy-proposed Release                                                          
Hit http://us.archive.ubuntu.com saucy/main Sources                                                                                     
Hit http://ppa.launchpad.net saucy Release.gpg                                                                   
Hit http://security.ubuntu.com saucy-security/restricted i386 Packages                     
Hit http://us.archive.ubuntu.com saucy/restricted Sources                                  
Hit http://security.ubuntu.com saucy-security/universe i386 Packages                       
Hit http://ppa.launchpad.net saucy Release.gpg                                             
Hit http://us.archive.ubuntu.com saucy/universe Sources                                    
Hit http://us.archive.ubuntu.com saucy/multiverse Sources                                  
Hit http://security.ubuntu.com saucy-security/multiverse i386 Packages                     
Hit http://ppa.launchpad.net saucy Release                                                 
Hit http://us.archive.ubuntu.com saucy/universe i386 Packages                                                                           
Hit http://ppa.launchpad.net saucy Release                                                                       
Hit http://security.ubuntu.com saucy-security/main Translation-en                                                                       
Hit http://us.archive.ubuntu.com saucy/multiverse i386 Packages                                                  
Hit http://ppa.launchpad.net saucy Release                                                 
Hit http://us.archive.ubuntu.com saucy/multiverse Translation-en                                                                        
Hit http://security.ubuntu.com saucy-security/multiverse Translation-en                                          
Hit http://ppa.launchpad.net saucy Release                                                 
Ign http://archive.canonical.com saucy/partner Translation-en_US                                                                        
Ign http://extras.ubuntu.com saucy/main Translation-en_US                                                        
Hit http://us.archive.ubuntu.com saucy/universe Translation-en                             
Hit http://ppa.launchpad.net saucy/main Sources                                                                  
Hit http://us.archive.ubuntu.com saucy-updates/main Sources                                                      
Ign http://archive.canonical.com saucy/partner Translation-en                                                    
Ign http://extras.ubuntu.com saucy/main Translation-en                                                           
Hit http://us.archive.ubuntu.com saucy-updates/restricted Sources                          
Hit http://ppa.launchpad.net saucy/main i386 Packages                
Hit http://security.ubuntu.com saucy-security/restricted Translation-en
Hit http://us.archive.ubuntu.com saucy-updates/universe Sources      
Hit http://us.archive.ubuntu.com saucy-updates/multiverse Sources    
Hit http://us.archive.ubuntu.com saucy-updates/main i386 Packages    
Hit http://security.ubuntu.com saucy-security/universe Translation-en
Hit http://us.archive.ubuntu.com saucy-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com saucy-updates/universe i386 Packages
Hit http://ppa.launchpad.net saucy/main Sources                      
Hit http://us.archive.ubuntu.com saucy-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com saucy-updates/main Translation-en
Hit http://ppa.launchpad.net saucy/main i386 Packages
Hit http://us.archive.ubuntu.com saucy-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com saucy-updates/restricted Translation-en
Hit http://ppa.launchpad.net saucy/main Sources
Hit http://us.archive.ubuntu.com saucy-updates/universe Translation-en
Hit http://us.archive.ubuntu.com saucy-backports/main Sources
Hit http://ppa.launchpad.net saucy/main i386 Packages
Hit http://us.archive.ubuntu.com saucy-backports/restricted Sources  
Hit http://us.archive.ubuntu.com saucy-backports/universe Sources    
Hit http://us.archive.ubuntu.com saucy-backports/multiverse Sources
Hit http://us.archive.ubuntu.com saucy-backports/main i386 Packages
Hit http://us.archive.ubuntu.com saucy-backports/restricted i386 Packages
Ign http://security.ubuntu.com saucy-security/main Translation-en_US
Hit http://us.archive.ubuntu.com saucy-backports/universe i386 Packages
Hit http://ppa.launchpad.net saucy/main Sources
Hit http://us.archive.ubuntu.com saucy-backports/multiverse i386 Packages
Ign http://security.ubuntu.com saucy-security/multiverse Translation-en_US
Hit http://ppa.launchpad.net saucy/main i386 Packages                
Ign http://security.ubuntu.com saucy-security/restricted Translation-en_US
Hit http://us.archive.ubuntu.com saucy-backports/main Translation-en
Ign http://security.ubuntu.com saucy-security/universe Translation-en_US
Hit http://us.archive.ubuntu.com saucy-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com saucy-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com saucy-backports/universe Translation-en
Hit http://us.archive.ubuntu.com saucy-proposed/universe Sources
Hit http://us.archive.ubuntu.com saucy-proposed/main Sources
Hit http://us.archive.ubuntu.com saucy-proposed/multiverse Sources
Hit http://us.archive.ubuntu.com saucy-proposed/restricted Sources
Ign http://us.archive.ubuntu.com saucy/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com saucy/universe Translation-en_US
Ign http://us.archive.ubuntu.com saucy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com saucy-updates/multiverse Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en_US
Ign http://us.archive.ubuntu.com saucy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com saucy-updates/universe Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en
Ign http://us.archive.ubuntu.com saucy-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com saucy-backports/multiverse Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en_US
Ign http://us.archive.ubuntu.com saucy-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com saucy-backports/universe Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en
Ign http://ppa.launchpad.net saucy/main Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en
Ign http://ppa.launchpad.net saucy/main Translation-en_US
Ign http://ppa.launchpad.net saucy/main Translation-en
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
-----> Upgrading () <-----
No packages need to be upgraded
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
-----> Upgrading () <-----
No packages need to be upgraded
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
-----> Cleaning the build tree <-----
-----> Cleaning the repository <-----
-----> Building repository <-----
-----> Cleaning sources <-----
find: `*.dsc': No such file or directory

```

I may be wrong but that looks pretty flawless to me.
I just DO NOT understand what is wrong here.

---

### Post by Tristan_Williams on 2014-02-05
I have fixed this Issue!

The solution that I found, which was actually VERY useful, is to generate a completely new /etc/apt/sources.list

You can find this 'sources.list generator' at the following site:
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)

It gives options for many extra PPAs and is extremely useful for when you have broken sources.list

---

