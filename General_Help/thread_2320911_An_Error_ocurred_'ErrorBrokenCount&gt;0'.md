---
title: "An Error ocurred 'Error:BrokenCount&gt;0'"
date: 2016-04-18
forum: General Help
---

### Post by larry41 on 2016-04-18
[FONT=arial][SIZE=2]hello guys i'm new on linux i'm after installing few packages and working with my laptop for more than a week now i got this message. 

An error occurred, please run package manager from the right-click menu  or apt-get in the terminal to see what is wrong. The error message was:  'Error: BrokenCount > 0'. This usually means that your installed  packages have unmet dependencies

so i did that and i type 

```
larry3d@larry3d:~$ apt-get
apt 1.0.1ubuntu2 for amd64 compiled on Mar 11 2016 03:18:04
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
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
   changelog - Download and display the changelog for the given package
   download - Download the binary package into the current directory

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.

```

[/SIZE][/FONT][SIZE=5][FONT=arial][SIZE=2]after this i decided to type 

```
larry3d@larry3d:~$ sudo apt-get update
[sudo] password for larry3d: 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease [65.9 kB]          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [273 kB]        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease [65.9 kB]           
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [5,352 B] 
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [153 kB]    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [5,928 B] 
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages [755 kB] 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [15.9 kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages [358 kB]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [13.2 kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [722 kB] 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [15.6 kB]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [359 kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [13.6 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [112 kB]        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release            
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [4,035 B] 
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [35.5 kB]   
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [2,764 B] 
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [458 kB] 
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages    
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages [13.0 kB]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [126 kB]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages [4,982 B]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [431 kB]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [12.7 kB]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [127 kB]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [5,172 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Fetched 4,152 kB in 6s (609 kB/s)                                              
W: Failed to fetch [http://ppa.launchpad.net/ubuntuhandbook1/sigil/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/ubuntuhandbook1/sigil/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ubuntuhandbook1/sigil/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntuhandbook1/sigil/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
larry3d@larry3d:~$ 

than i type
larry3d@larry3d:~$ sudo aptitude
[sudo] password for larry3d: 
sudo: aptitude: command not found
larry3d@larry3d:~$ 
```

there is a red minos simbol on the right top area of my screen the last packages i installed was wine and ebook maestro , calibre , and sigil . when i was trying to update my laptop everything started i mean the red simbol and sometimes the laptop stops with frozen screen and software center have problems to remove wine
             PLEASE HELP :icon_frown:[/SIZE][/FONT][/SIZE]

---

### Post by slickymaster on 2016-04-18
Hi larry41, welcome to the forums.

Please, use color and font properties for highlighting portions of your text, and not for all of the text in your post. Please use the default font color and properties unless you need to highlight or draw attention to a part of your post. ALL CAPS is interpreted as screaming. Funky non-uniform font size/color is difficult for those who are visually impaired. If you are having problems with reading the font, please adjust your browser.

I invite you to have a read at the [forum posting guidelines]("http://ubuntuforums.org/showthread.php?t=2158945").

---

### Post by Bashing-om on 2016-04-18
larry41; Hello;

Please see and adhere to slickymaster's advisory .

As to your situation ... seems you have gone where you should not have in attempting to install sigil .

That package is wily/ , xenial/ , and devel/ NOT trusty. Installing the advanced package there is no telling now what advanced libraries have been installed to support sigil that has no support in the trusty install:
[http://ppa.launchpad.net/ubuntuhandbook1/sigil/ubuntu/dists/](http://ppa.launchpad.net/ubuntuhandbook1/sigil/ubuntu/dists/)

Maybe:
disable the sigil source in the source file and now what results:
```

sudo apt update
sudo apt full-upgrade
sudo apt-get -f install
sudo dpkg -C

```

Get an idea of what the damage might be.

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by larry41 on 2016-04-18
> **Bashing-om said:**
> larry41; Hello;

Please see and adhere to slickymaster's advisory .

As to your situation ... seems you have gone where you should not have in attempting to install sigil .

That package is wily/ , xenial/ , and devel/ NOT trusty. Installing the advanced package there is no telling now what advanced libraries have been installed to support sigil that has no support in the trusty install:
[http://ppa.launchpad.net/ubuntuhandbook1/sigil/ubuntu/dists/](http://ppa.launchpad.net/ubuntuhandbook1/sigil/ubuntu/dists/)

Maybe:
disable the sigil source in the source file and now what results:
```

sudo apt update
sudo apt full-upgrade
sudo apt-get -f install
sudo dpkg -C

```

Get an idea of what the damage might be.[INDENT][INDENT]maybe yes[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


i did as you told me my friend on the terminal this 
```
larry3d@larry3d:~$ sudo apt update
[sudo] password for larry3d: 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease [65.9 kB]          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [273 kB]        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [5,352 B] 
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [153 kB]    
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease [65.9 kB]           
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [5,928 B] 
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages [755 kB] 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [15.9 kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages [358 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [13.2 kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [722 kB] 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [112 kB]        
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [15.6 kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [359 kB]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [4,035 B] 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [13.6 kB]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en            
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [35.5 kB]   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources             
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [2,764 B] 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages    
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [458 kB] 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages [13.0 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [126 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages              
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages [4,982 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [431 kB]  
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [12.7 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [127 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en              
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [5,172 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Fetched 4,152 kB in 8s (515 kB/s)                                              
W: Failed to fetch [http://ppa.launchpad.net/ubuntuhandbook1/sigil/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/ubuntuhandbook1/sigil/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ubuntuhandbook1/sigil/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntuhandbook1/sigil/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
larry3d@larry3d:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libav-tools : Depends: ffmpeg
E: Unmet dependencies. Try using -f.
larry3d@larry3d:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libavdevice53 libavfilter3 libavresample1 linux-headers-4.2.0-27
  linux-headers-4.2.0-27-generic linux-image-4.2.0-27-generic
  linux-image-extra-4.2.0-27-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ffmpeg
Suggested packages:
  ffmpeg-doc
The following NEW packages will be installed:
  ffmpeg
0 upgraded, 1 newly installed, 0 to remove and 22 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,288 kB of archives.
After this operation, 1,917 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 280366 files and directories currently installed.)
Preparing to unpack .../ffmpeg_7%3a2.8-1~trusty+1_amd64.deb ...
Unpacking ffmpeg (7:2.8-1~trusty+1) ...
dpkg: error processing archive /var/cache/apt/archives/ffmpeg_7%3a2.8-1~trusty+1_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/ffmpeg', which is also in package clipgrab 3.5.6~trusty1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
E: Sub-process /usr/bin/dpkg returned an error code (1)
larry3d@larry3d:~$ sudo dpkg -C
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 libav-tools          Compatibility links for libav-tools (transitional package

larry3d@larry3d:~$
```

---

### Post by larry41 on 2016-04-18
the problem still on it even software center has problems with messages :cry:  . to turn off the laptop everytime i was just closing the laptop . and when the automatic update was appearing i was just closing those message and now that i want to make an update my laptop is not working properly. i can not even burn an iso file on my usb stick to install the new ubuntu 15.10 and the cd writter same problem


something crazy is crossing my mind is possible for someone to control this linux  platform through a malware or sophisticated software?

---

### Post by lisati on 2016-04-18
You need to disable the source for sigil in your sources.list file first, otherwise you're going to keep in getting the 404 errors.

---

### Post by Bashing-om on 2016-04-18
larry41; Hey:
> 
W: Failed to fetch [http://ppa.launchpad.net/ubuntuhandb...amd64/Packages](http://ppa.launchpad.net/ubuntuhandb...amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ubuntuhandb...-i386/Packages](http://ppa.launchpad.net/ubuntuhandb...-i386/Packages)  404  Not Found

E: Some index files failed to download.


You appear to have not disabled that troublesome PPA .

We can do that from terminal;
Post back the results of terminal commands:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

And once found, we edit the file with your favorite text editor .

[INDENT][INDENT]we can do that too
[/INDENT][/INDENT]

---

### Post by larry41 on 2016-04-18
> **Bashing-om said:**
> larry41; Hey:


You appear to have not disabled that troublesome PPA .

We can do that from terminal;
Post back the results of terminal commands:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

And once found, we edit the file with your favorite text editor .[INDENT][INDENT]we can do that too
[/INDENT]
[/INDENT]



please my friend tell me how can i do that i don't know to much about linux i can only copy and paste on terminal . i would like to use any epub editor to build kindle books . but i don't know what is the choice on ubuntu . frustation for building Epub files made me to install Sigil because i thought it was safe. what options i have on linux to build Epub  files? and how can i delete Sigil?

---

### Post by Bashing-om on 2016-04-18
larry41l Sure ...

In small steps:
activate a terminal and copy/paste the outputs of terminal commands:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

These files are what the system is fetching for updates/install .

Next up then is to diable that troublesome PPA ... then see what damage is done by attempting to install sigil .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by larry41 on 2016-04-18
> **Bashing-om said:**
> larry41l Sure ...

In small steps:
activate a terminal and copy/paste the outputs of terminal commands:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

These files are what the system is fetching for updates/install .

Next up then is to diable that troublesome PPA ... then see what damage is done by attempting to install sigil .[INDENT][INDENT]all in the process
[/INDENT]
[/INDENT]


ok my friend i did this 
```

larry3d@larry3d:~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1)]/ trusty main restricted
     2    
     3    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4    # newer versions of the distribution.
     5    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted
     6    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
    11    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
    17    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
    18    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe
    19    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
    27    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
    28    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
    29    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
    37    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
    38    
    39    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
    40    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
    41    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
    42    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
    43    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
    44    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
    51    # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
    56    deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
larry3d@larry3d:~$ tail -v -n +1 /etc/apt/sources.list.d/*

```
i still have the terminal open

---

### Post by Bashing-om on 2016-04-18
larry41; Well,

Code tags, please .. it does help to use code tags to help you .
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

There is no source for sigil in the file : /etc/apt/soures.list .
No return from the tail command .. we must assume that you have disabled that PPA from "software sources" and move on.

Show now what returns:
```

sudo apt update
sudo apt upgrade
sudo apt-get -f install
sudo dpkg -C

```
from each of these terminal commands.

[INDENT][INDENT]see what condition the condition is in
[/INDENT][/INDENT]

---

### Post by larry41 on 2016-04-18
> **Bashing-om said:**
> larry41; Well,

Code tags, please .. it does help to use code tags to help you .
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

There is no source for sigil in the file : /etc/apt/soures.list .
No return from the tail command .. we must assume that you have disabled that PPA from "software sources" and move on.

Show now what returns:
```

sudo apt update
sudo apt upgrade
sudo apt-get -f install
sudo dpkg -C

```
from each of these terminal commands.[INDENT][INDENT]see what condition the condition is in
[/INDENT]
[/INDENT]


```

larry3d@larry3d:~$ sudo apt update
[sudo] password for larry3d: 
Hit http://security.ubuntu.com trusty-security InRelease
Ign http://us.archive.ubuntu.com trusty InRelease                              
Hit http://us.archive.ubuntu.com trusty-updates InRelease                      
Hit http://us.archive.ubuntu.com trusty-backports InRelease                    
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security/main Sources                    
Hit http://us.archive.ubuntu.com trusty Release                                
Get:1 http://extras.ubuntu.com trusty Release.gpg [72 B]                       
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Hit http://us.archive.ubuntu.com trusty-updates/main Sources                   
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security/universe Sources                
Hit http://us.archive.ubuntu.com trusty-updates/restricted Sources             
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Hit http://us.archive.ubuntu.com trusty-updates/universe Sources               
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Sources             
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Hit http://us.archive.ubuntu.com trusty-updates/main amd64 Packages            
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages      
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages        
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages      
Hit http://us.archive.ubuntu.com trusty-updates/main i386 Packages             
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Hit http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages       
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Hit http://us.archive.ubuntu.com trusty-updates/universe i386 Packages         
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages       
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources  
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Ign http://ppa.launchpad.net trusty Release.gpg                    
Hit http://us.archive.ubuntu.com trusty/multiverse Sources         
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages        
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Ign http://ppa.launchpad.net trusty Release                       
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty/main i386 Packages        
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages  
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty/main Translation-en
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/universe Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US      
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Err http://ppa.launchpad.net trusty/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net trusty/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Fetched 72 B in 4s (17 B/s)
W: Failed to fetch http://ppa.launchpad.net/ubuntuhandbook1/sigil/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ubuntuhandbook1/sigil/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
larry3d@larry3d:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libav-tools : Depends: ffmpeg
E: Unmet dependencies. Try using -f.
larry3d@larry3d:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libavdevice53 libavfilter3 libavresample1 linux-headers-4.2.0-27
  linux-headers-4.2.0-27-generic linux-image-4.2.0-27-generic
  linux-image-extra-4.2.0-27-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ffmpeg
Suggested packages:
  ffmpeg-doc
The following NEW packages will be installed:
  ffmpeg
0 upgraded, 1 newly installed, 0 to remove and 22 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,288 kB of archives.
After this operation, 1,917 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 280366 files and directories currently installed.)
Preparing to unpack .../ffmpeg_7%3a2.8-1~trusty+1_amd64.deb ...
Unpacking ffmpeg (7:2.8-1~trusty+1) ...
dpkg: error processing archive /var/cache/apt/archives/ffmpeg_7%3a2.8-1~trusty+1_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/ffmpeg', which is also in package clipgrab 3.5.6~trusty1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/ffmpeg_7%3a2.8-1~trusty+1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
larry3d@larry3d:~$ sudo dpkg -C
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 libav-tools          Compatibility links for libav-tools (transitional package

larry3d@larry3d:~$ 


``` 

what am i need to do :( and i haven't dissable any PPA from "software sources" because i don't know how to do that

---

### Post by slickymaster on 2016-04-19
> **larry41 said:**
> <---snip--->

what am i need to do :( and i haven't dissable any PPA from "software sources" because i don't know how to do that
Head to Software Center -> Edit -> Software Sources… -> Other Software tab,  and un-tick the line with the ppa you want to disable. Afterwards run again ```
sudo apt-get update && sudo apt-get upgrade
```Post back in the thread the output you get, using code tags for the effect.

---

### Post by larry41 on 2016-04-19
> **slickymaster said:**
> Head to Software Center -> Edit -> Software Sources&#8230; -> Other Software tab,  and un-tick the line with the ppa you want to disable. Afterwards run again ```
sudo apt-get update && sudo apt-get upgrade
```Post back in the thread the output you get, using code tags for the effect.

i did as you can see
[LIST=1]
[*]```
   larry3d@larry3d:~$ sudo apt-get update
 [sudo] password for larry3d:  
 Ign http://us.archive.ubuntu.com trusty InRelease
 Get:1 http://us.archive.ubuntu.com trusty-updates InRelease [65.9 kB]           
 Get:2 http://us.archive.ubuntu.com trusty-backports InRelease [65.9 kB]         
 Ign http://extras.ubuntu.com trusty InRelease                                   
 Hit http://ppa.launchpad.net trusty InRelease                                   
 Hit http://extras.ubuntu.com trusty Release.gpg                                 
 Hit http://us.archive.ubuntu.com trusty Release.gpg                             
 Get:3 http://us.archive.ubuntu.com trusty-updates/main Sources [273 kB]         
 Hit http://extras.ubuntu.com trusty Release                                     
 Hit http://ppa.launchpad.net trusty InRelease                                   
 Get:4 http://security.ubuntu.com trusty-security InRelease [65.9 kB]            
 Hit http://ppa.launchpad.net trusty InRelease                                   
 Hit http://extras.ubuntu.com trusty/main Sources                                
 Get:5 http://us.archive.ubuntu.com trusty-updates/restricted Sources [5,352 B]  
 Get:6 http://us.archive.ubuntu.com trusty-updates/universe Sources [153 kB]     
 Hit http://extras.ubuntu.com trusty/main amd64 Packages                         
 Get:7 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [5,928 B]  
 Get:8 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [755 kB]  
 Hit http://extras.ubuntu.com trusty/main i386 Packages                          
 Get:9 http://security.ubuntu.com trusty-security/main Sources [112 kB]          
 Hit http://ppa.launchpad.net trusty/main amd64 Packages                         
 Hit http://ppa.launchpad.net trusty/main i386 Packages                          
 Get:10 http://security.ubuntu.com trusty-security/restricted Sources [4,035 B]  
 Hit http://ppa.launchpad.net trusty/main Translation-en                         
 Get:11 http://security.ubuntu.com trusty-security/universe Sources [35.5 kB]    
 Get:12 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.9 kB]
 Hit http://ppa.launchpad.net trusty/main amd64 Packages                         
 Get:13 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [358 kB]
 Hit http://ppa.launchpad.net trusty/main i386 Packages                          
 Get:14 http://security.ubuntu.com trusty-security/multiverse Sources [2,764 B]  
 Hit http://ppa.launchpad.net trusty/main Translation-en                         
 Get:15 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [13.2 kB]
 Get:16 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [722 kB]  
 Get:17 http://security.ubuntu.com trusty-security/main amd64 Packages [458 kB]  
 Hit http://ppa.launchpad.net trusty/main amd64 Packages                         
 Hit http://ppa.launchpad.net trusty/main i386 Packages                          
 Hit http://ppa.launchpad.net trusty/main Translation-en                         
 Get:18 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.6 kB]
 Ign http://extras.ubuntu.com trusty/main Translation-en_US                      
 Get:19 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [359 kB]
 Ign http://extras.ubuntu.com trusty/main Translation-en                         
 Get:20 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [13.6 kB]
 Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en             
 Get:21 http://security.ubuntu.com trusty-security/restricted amd64 Packages [13.0 kB]
 Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en       
 Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en       
 Get:22 http://us.archive.ubuntu.com trusty-backports/main Sources [8,948 B]     
 Get:23 http://us.archive.ubuntu.com trusty-backports/restricted Sources [28 B]  
 Get:24 http://us.archive.ubuntu.com trusty-backports/universe Sources [34.5 kB]
 Get:25 http://security.ubuntu.com trusty-security/universe amd64 Packages [126 kB]
 Get:26 http://us.archive.ubuntu.com trusty-backports/multiverse Sources [1,898 B]
 Get:27 http://us.archive.ubuntu.com trusty-backports/main amd64 Packages [9,998 B]
 Get:28 http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages [28 B]
 Get:29 http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages [41.5 kB]
 Get:30 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [4,982 B]
 Get:31 http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [1,571 B]
 Get:32 http://us.archive.ubuntu.com trusty-backports/main i386 Packages [9,974 B]
 Get:33 http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
 Get:34 http://us.archive.ubuntu.com trusty-backports/universe i386 Packages [41.5 kB]
 Get:35 http://security.ubuntu.com trusty-security/main i386 Packages [431 kB]   
 Get:36 http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,552 B]
 Get:37 http://us.archive.ubuntu.com trusty-backports/main Translation-en [5,986 B]
 Get:38 http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en [1,215 B]
 Get:39 http://us.archive.ubuntu.com trusty-backports/restricted Translation-en [28 B]
 Get:40 http://us.archive.ubuntu.com trusty-backports/universe Translation-en [36.0 kB]
 Hit http://us.archive.ubuntu.com trusty Release                                 
 Get:41 http://us.archive.ubuntu.com trusty-updates/universe Translation-en [187 kB]
 Get:42 http://security.ubuntu.com trusty-security/restricted i386 Packages [12.7 kB]
 Hit http://us.archive.ubuntu.com trusty/main Sources                            
 Hit http://us.archive.ubuntu.com trusty/restricted Sources                      
 Hit http://us.archive.ubuntu.com trusty/universe Sources                        
 Hit http://us.archive.ubuntu.com trusty/multiverse Sources                      
 Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                     
 Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages               
 Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                 
 Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages               
 Get:43 http://security.ubuntu.com trusty-security/universe i386 Packages [127 kB]
 Hit http://us.archive.ubuntu.com trusty/main i386 Packages                      
 Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages                
 Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                  
 Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages                
 Hit http://us.archive.ubuntu.com trusty/main Translation-en                     
 Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en               
 Get:44 http://security.ubuntu.com trusty-security/multiverse i386 Packages [5,172 B]
 Hit http://us.archive.ubuntu.com trusty/restricted Translation-en               
 Hit http://us.archive.ubuntu.com trusty/universe Translation-en                 
 Hit http://security.ubuntu.com trusty-security/main Translation-en              
 Hit http://security.ubuntu.com trusty-security/multiverse Translation-en        
 Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                  
 Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US            
 Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US            
 Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US              
 Hit http://security.ubuntu.com trusty-security/restricted Translation-en        
 Hit http://security.ubuntu.com trusty-security/universe Translation-en          
 Fetched 4,600 kB in 12s (358 kB/s)                                              
 Reading package lists... Done
 larry3d@larry3d:~$ sudo apt-get upgrade
 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 You might want to run 'apt-get -f install' to correct these.
 The following packages have unmet dependencies:
  libav-tools : Depends: ffmpeg
 E: Unmet dependencies. Try using -f.
 larry3d@larry3d:~$ ^C

  
``` 
the problem still on my laptop after all this process i restart my laptop and the problem is not fix yet :(
[/LIST]

---

### Post by slickymaster on 2016-04-19
Did you try to do what the package manager is advising? Run```
sudo apt-get -f install
```

---

### Post by larry41 on 2016-04-19
> **slickymaster said:**
> Did you try to do what the package manager is advising? Run```
sudo apt-get -f install
```

I forgot to do that but I will do it tonight after I get home will be kind of late when I post my next answer . I'm texting  from my mobile phone  :)

> **slickymaster said:**
> Did you try to do what the package manager is advising? Run```
sudo apt-get -f install
```

i just did that command on terminal 

```
larry3d@larry3d:~$ sudo apt-get -f install
[sudo] password for larry3d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libavdevice53 libavfilter3 libavresample1 linux-headers-4.2.0-27
  linux-headers-4.2.0-27-generic linux-image-4.2.0-27-generic
  linux-image-extra-4.2.0-27-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ffmpeg
Suggested packages:
  ffmpeg-doc
The following NEW packages will be installed:
  ffmpeg
0 upgraded, 1 newly installed, 0 to remove and 22 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,288 kB of archives.
After this operation, 1,917 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 280366 files and directories currently installed.)
Preparing to unpack .../ffmpeg_7%3a2.8-1~trusty+1_amd64.deb ...
Unpacking ffmpeg (7:2.8-1~trusty+1) ...
dpkg: error processing archive /var/cache/apt/archives/ffmpeg_7%3a2.8-1~trusty+1_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/ffmpeg', which is also in package clipgrab 3.5.6~trusty1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/ffmpeg_7%3a2.8-1~trusty+1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
larry3d@larry3d:~$ 

 
``` 

it looks that the problem still on my laptop :(

---

### Post by Bashing-om on 2016-04-20
larry41; Morning ...

Commands should be run in the order given.
Presently we have:
> 
0 upgraded, 1 newly installed, 0 to remove and [color=red]22 not upgraded[/color].

Our focus is to get this system updated .

Do now terminal commands:
```

sudp apt update
sudo apt upgrade
sudo apt-get -f install
sudo dpkg -C

```
And show us these outputs .

[INDENT][INDENT]we see what it will take to fix.
[/INDENT][/INDENT]

---

### Post by larry41 on 2016-04-20
> **Bashing-om said:**
> larry41; Morning ...

Commands should be run in the order given.
Presently we have:

Our focus is to get this system updated .

Do now terminal commands:
```

sudp apt update
sudo apt upgrade
sudo apt-get -f install
sudo dpkg -C

```
And show us these outputs .[INDENT][INDENT]we see what it will take to fix.
[/INDENT]
[/INDENT]

my friend i did those commands and everything still the same i'm so worry about my laptop at this point :(
```
larry3d@larry3d:~$ sudp apt update
No command 'sudp' found, did you mean:
 Command 'sudo' from package 'sudo-ldap' (universe)
 Command 'sudo' from package 'sudo' (main)
 Command 'sfdp' from package 'graphviz' (main)
 Command 'sup' from package 'sup' (universe)
sudp: command not found
larry3d@larry3d:~$ sudo apt update
[sudo] password for larry3d: 
Sorry, try again.
[sudo] password for larry3d: 
Ign http://us.archive.ubuntu.com trusty InRelease
Get:1 http://us.archive.ubuntu.com trusty-updates InRelease [65.9 kB]          
Get:2 http://us.archive.ubuntu.com trusty-backports InRelease [65.9 kB]        
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://us.archive.ubuntu.com trusty Release                                
Get:3 http://security.ubuntu.com trusty-security InRelease [65.9 kB]           
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://ppa.launchpad.net trusty InRelease                                  
Get:4 http://us.archive.ubuntu.com trusty-updates/main Sources [273 kB]        
Hit http://ppa.launchpad.net trusty InRelease                                  
Get:5 http://extras.ubuntu.com trusty Release.gpg [72 B]                       
Get:6 http://us.archive.ubuntu.com trusty-updates/restricted Sources [5,352 B] 
Get:7 http://us.archive.ubuntu.com trusty-updates/universe Sources [154 kB]    
Get:8 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [5,928 B] 
Hit http://ppa.launchpad.net trusty InRelease                                  
Get:9 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [755 kB] 
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:10 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.9 kB]
Get:11 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [358 kB]
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:12 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [13.2 kB]
Get:13 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [722 kB] 
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:14 http://security.ubuntu.com trusty-security/main Sources [112 kB]        
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:15 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.6 kB]
Get:16 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [360 kB]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:17 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [13.6 kB]
Get:18 http://us.archive.ubuntu.com trusty-updates/main Translation-en [377 kB]
Get:19 http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en [7,227 B]
Get:20 http://us.archive.ubuntu.com trusty-updates/restricted Translation-en [3,699 B]
Get:21 http://us.archive.ubuntu.com trusty-updates/universe Translation-en [188 kB]
Get:22 http://us.archive.ubuntu.com trusty-backports/main Sources [8,948 B]    
Get:23 http://us.archive.ubuntu.com trusty-backports/restricted Sources [28 B] 
Get:24 http://us.archive.ubuntu.com trusty-backports/universe Sources [34.5 kB]
Get:25 http://us.archive.ubuntu.com trusty-backports/multiverse Sources [1,898 B]
Get:26 http://us.archive.ubuntu.com trusty-backports/main amd64 Packages [9,998 B]
Get:27 http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages [28 B]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:28 http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages [41.5 kB]
Get:29 http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [1,571 B]
Get:30 http://us.archive.ubuntu.com trusty-backports/main i386 Packages [9,974 B]
Get:31 http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:32 http://us.archive.ubuntu.com trusty-backports/universe i386 Packages [41.5 kB]
Get:33 http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,552 B]
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Get:34 http://security.ubuntu.com trusty-security/restricted Sources [4,035 B] 
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Ign http://extras.ubuntu.com trusty/main Translation-en_US         
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages     
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Get:35 http://security.ubuntu.com trusty-security/universe Sources [35.5 kB]   
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Ign http://extras.ubuntu.com trusty/main Translation-en                      
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en            
Hit http://us.archive.ubuntu.com trusty/universe Translation-en              
Get:36 http://security.ubuntu.com trusty-security/multiverse Sources [2,764 B] 
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Get:37 http://security.ubuntu.com trusty-security/main amd64 Packages [457 kB]
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US       
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US         
Get:38 http://security.ubuntu.com trusty-security/restricted amd64 Packages [13.0 kB]
Get:39 http://security.ubuntu.com trusty-security/universe amd64 Packages [126 kB]
Get:40 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [4,982 B]
Get:41 http://security.ubuntu.com trusty-security/main i386 Packages [431 kB]
Get:42 http://security.ubuntu.com trusty-security/restricted i386 Packages [12.7 kB]
Get:43 http://security.ubuntu.com trusty-security/universe i386 Packages [127 kB]
Get:44 http://security.ubuntu.com trusty-security/multiverse i386 Packages [5,172 B]
Get:45 http://security.ubuntu.com trusty-security/main Translation-en [251 kB] 
Get:46 http://security.ubuntu.com trusty-security/multiverse Translation-en [2,570 B]
Get:47 http://security.ubuntu.com trusty-security/restricted Translation-en [3,206 B]
Get:48 http://security.ubuntu.com trusty-security/universe Translation-en [74.7 kB]
Fetched 5,280 kB in 8s (630 kB/s)                                              
Reading package lists... Done
larry3d@larry3d:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libav-tools : Depends: ffmpeg
E: Unmet dependencies. Try using -f.
larry3d@larry3d:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libavdevice53 libavfilter3 libavresample1 linux-headers-4.2.0-27
  linux-headers-4.2.0-27-generic linux-image-4.2.0-27-generic
  linux-image-extra-4.2.0-27-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ffmpeg
Suggested packages:
  ffmpeg-doc
The following NEW packages will be installed:
  ffmpeg
0 upgraded, 1 newly installed, 0 to remove and 32 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,288 kB of archives.
After this operation, 1,917 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 280366 files and directories currently installed.)
Preparing to unpack .../ffmpeg_7%3a2.8-1~trusty+1_amd64.deb ...
Unpacking ffmpeg (7:2.8-1~trusty+1) ...
dpkg: error processing archive /var/cache/apt/archives/ffmpeg_7%3a2.8-1~trusty+1_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/ffmpeg', which is also in package clipgrab 3.5.6~trusty1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/ffmpeg_7%3a2.8-1~trusty+1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
larry3d@larry3d:~$ sudo dpkg -C
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 libav-tools          Compatibility links for libav-tools (transitional package

larry3d@larry3d:~$ 

 
```
i did it for second time but now i unselect  everything from software source  other softwares as the picture describes 
```
larry3d@larry3d:~$ sudo apt update
[sudo] password for larry3d: 
Sorry, try again.
[sudo] password for larry3d: 
Ign http://us.archive.ubuntu.com trusty InRelease
Hit http://security.ubuntu.com trusty-security InRelease
Hit http://us.archive.ubuntu.com trusty-updates InRelease
Hit http://us.archive.ubuntu.com trusty-backports InRelease
Hit http://security.ubuntu.com trusty-security/main Sources
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://security.ubuntu.com trusty-security/restricted Sources
Hit http://us.archive.ubuntu.com trusty-updates/main Sources   
Hit http://security.ubuntu.com trusty-security/universe Sources    
Hit http://us.archive.ubuntu.com trusty-updates/restricted Sources 
Hit http://security.ubuntu.com trusty-security/multiverse Sources
Hit http://us.archive.ubuntu.com trusty-updates/universe Sources
Hit http://security.ubuntu.com trusty-security/main amd64 Packages
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Sources
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/main amd64 Packages 
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages
Hit http://security.ubuntu.com trusty-security/main i386 Packages   
Hit http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages
Hit http://security.ubuntu.com trusty-security/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/main i386 Packages  
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages
Hit http://security.ubuntu.com trusty-security/main Translation-en  
Hit http://us.archive.ubuntu.com trusty-updates/universe i386 Packages
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en 
Hit http://security.ubuntu.com trusty-security/universe Translation-en    
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en 
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/main Sources
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en
Hit http://us.archive.ubuntu.com trusty Release   
Hit http://us.archive.ubuntu.com trusty/main Sources
Hit http://us.archive.ubuntu.com trusty/restricted Sources
Hit http://us.archive.ubuntu.com trusty/universe Sources
Hit http://us.archive.ubuntu.com trusty/multiverse Sources
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty/main Translation-en
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/universe Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Reading package lists... Done 
larry3d@larry3d:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libav-tools : Depends: ffmpeg but it is not installable
E: Unmet dependencies. Try using -f.
larry3d@larry3d:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libaacs0 libass4 libavcodec-ffmpeg56 libavdevice-ffmpeg56 libavdevice53
  libavfilter-ffmpeg5 libavfilter3 libavformat-ffmpeg56 libavresample-ffmpeg2
  libavresample1 libavutil-ffmpeg54 libbluray1 libbs2b0 libcrystalhd3 libenca0
  libflite1 libgme0 libmodplug1 libpgm-5.1-0 libpostproc-ffmpeg53 libshine3
  libssh-gcrypt-4 libswresample-ffmpeg1 libswscale-ffmpeg3 libtwolame0
  libvdpau1 libx265-59 libzmq3 libzvbi-common libzvbi0 linux-headers-4.2.0-27
  linux-headers-4.2.0-27-generic linux-image-4.2.0-27-generic
  linux-image-extra-4.2.0-27-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  clipgrab libav-tools
0 upgraded, 0 newly installed, 2 to remove and 32 not upgraded.
1 not fully installed or removed.
After this operation, 955 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 280365 files and directories currently installed.)
Removing clipgrab (3.5.6~trusty1) ...
Removing libav-tools (7:2.8-1~trusty+1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
larry3d@larry3d:~$ sudo dpkg -C
larry3d@larry3d:~$ 


```
now clipgrab have been delete it but it looks that my laptop is fixed :) the updating system it woke up  it looks that everything comes to normal . hold on let me restore my laptop this is so exiting :)

yes yes yesssssss my laptop works and sigil ia working on it with no problems i'm including 2 more pictures where you can see very clear what i did on softwares update and one picture of sigil working on my laptop with no problems . i'm so happy  thank you to everyone for your help

i don't know how to do to make this thread is solved. i need the help of administrator please to make this thread resolved  and thank you so much ones again

---

### Post by slickymaster on 2016-04-21
Sorry for not coming to your thread before, but real life sometimes does get in the way. Anyway, I knew you here in good hands with bashing-om.

It does seems that all those PPAs were the culprits.

Glad you got it fixed. Just follow this [link on how to mark threads as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

