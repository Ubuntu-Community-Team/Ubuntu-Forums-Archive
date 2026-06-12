---
title: "Synaptic errors when using Add downloaded packages"
date: 2015-01-04
forum: General Help
---

### Post by peter169 on 2015-01-04
Hi, Please help :)

I'm using ubundu 14.04.1 Desktop amd64 with all updates installed

To add applications I use Synaptic and select the packages I want to add

I then use Generate package download script to generate a script in my home folder

I use terminal command line to execute the script

I think I may have moved these files to a flash drive using terminal  command line sudo -s and then mv, so that I could reformat the hard  drive, and then moved the files back in the same way.

I am now using Synaptic Add downloaded packages to add these packages and get a list of these two errors repeated:
E: Invalid archive signature
E: Internal error, could not locate member control.tar.{gzbz2xzlzma}

Lastly, there is one mention of this error at the end of the list of errors:
E: Archive is too short



That is the real problem though there is one other thing I'd like to fix (though it's easy enough to get around). In Synaptic the Home folder shortcut points to the /root folder instead of the /home/{current user} folder (though it still shows the icon for the Home folder for the shortcut and the folder path). The shortcut is called Home and the folder path shows root
This isn't the case in the Files app where the Home folder shortcut points to the /home/{current user} folder

---

### Post by bapoumba on 2015-01-04
I am not sure I understand what you have been doing here..
Why not use Synaptic to install the packages in the first place ?
So you moved files (the script ones ?) to an usb drive using sudo (why ?), reformatted the hard drive (the whole drive ?) and sudo-moved the files back (where ?) > likely to explain the /home files belong to root or are not at the correct place in the file structure, but I am very unsure ...

What do the following commands return ?
```
ls -l /home/
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by ajgreeny on 2015-01-04
Are these downloaded package files (.deb files I assume) available from the repositories or some third party packages not in any repo.

If the latter, and assuming you know they are trustworthy packages, you may be able to install them with gdebi, which will have to be installed first, which will then download any dependencies, providing they are in a repo somewhere.

Alternatively you may find that if you put all the .deb files you want to install in a new-folder, then run ```
sudo dpkg -i /path/to/new-folder/*.deb
```it will install everything for you.  If there are dependency problems using dpkg, I think it will just warn you with error messages but will not download and install those missing packages as gdebi does.

All this points to a very good reason for sticking wherever possible to the repos for Ubuntu instead of using packages not from them.

EDIT:
Just a second quick thought.
Are you aware that using synaptic to produce a download script does not actually download the packages; all it does is write a bash script that can be run later with one or more wget lines in it, one for each package, and it does not install those packages itself, just downloads them.

As an example here are the top few lines of a download script for dvdrip which I produced recently
```
#!/bin/sh
wget -c http://gb.archive.ubuntu.com/ubuntu/pool/universe/libq/libquicktime/libquicktime2_1.2.4-4ubuntu2_amd64.deb
wget -c http://gb.archive.ubuntu.com/ubuntu/pool/universe/s/sox/libsox2_14.4.1-3ubuntu1_amd64.deb
wget -c http://gb.archive.ubuntu.com/ubuntu/pool/universe/libv/libva/libva-glx1_1.3.0-2_amd64.deb
wget -c http://gb.archive.ubuntu.com/ubuntu/pool/multiverse/t/transcode/transcode_1.1.7-8_amd64.deb
wget -c http://gb.archive.ubuntu.com/ubuntu/pool/universe/g/gtk2-ex-formfactory/libgtk2-ex-formfactory-perl_0.67-0ubuntu1_all.deb
wget -c http://gb.archive.ubuntu.com/ubuntu/pool/universe/libe/libevent-perl/libevent-perl_1.21-1build1_amd64.deb
```

Also the /home for synaptic is root because it is running as root, not as user; if you run synaptic as a user from terminal with command **synaptic** you can not install or upgrade or do any of the activities it is made for.

---

### Post by peter169 on 2015-01-04
Let me explain:
[LIST]
[*]I am using Synaptic to install the packages 
[*]From Synaptic I generate a (download) script which includes all the packages which have been selected for installation. This script I save to ~/Downloads/Software/Updates/ubuntu-14.04.1-desktop-amd64 
[*]I run the script and all the packages are downloaded 
[*]I "Add downloaded packages" in Synaptic and it then installs these packes (which have already been downloaded) 
[*]This doesnt work when I get the errors I mentioned. Instead of installing these packages - which have already been downloaded - Synaptic wants to download and install 
[/LIST]
I moved all the files (script and all the downloaded .deb package files) so I could reformat the whole hard drive and reinstall then move the files back to previous directory so I could add all the downloaded packages using Synaptic

ls -l /home/
total 20
drwx------  2 root  root  16384 Jan  2 04:35 lost+found
drwxr-xr-x 20 peter peter  4096 Jan  4 11:28 peter

```
sudo apt-get update
[sudo] password for peter: 
Sorry, try again.
[sudo] password for peter: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty InRelease                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports InRelease           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty Release.gpg                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources       
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates Release.gpg                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports Release.gpg         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages             
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages       
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages       
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages              
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/main Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages        
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages          
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/universe Sources                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_GB                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages        
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/multiverse Sources                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/main amd64 Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/universe amd64 Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/multiverse amd64 Packages              
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/multiverse i386 Packages               
Get:1 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/main Translation-en_GB [96,8 kB]     
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/main Translation-en                    
Get:2 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/multiverse Translation-en_GB [98,3 kB]
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/multiverse Translation-en              
Get:3 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/restricted Translation-en_GB [3 483 B]
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/restricted Translation-en              
Get:4 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/universe Translation-en_GB [7 557 B] 
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/universe Translation-en                
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/main Sources                   
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/restricted Sources             
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/universe Sources               
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/multiverse Sources             
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/main amd64 Packages            
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/restricted amd64 Packages      
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/universe amd64 Packages        
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages      
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/main i386 Packages             
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/restricted i386 Packages       
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/universe i386 Packages         
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/multiverse i386 Packages       
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/universe Translation-en        
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/main Sources                 
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/universe Sources             
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/multiverse Sources           
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/main amd64 Packages          
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/restricted amd64 Packages    
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/universe amd64 Packages      
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages    
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/universe Translation-en      
Fetched 206 kB in 30s (6 831 B/s)                                              
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

Errors so closed Synaptic and ran again:

```
sudo apt-get update
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty InRelease
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release    
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates InRelease             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                    
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources              
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty Release.gpg                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates Release.gpg                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages             
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports Release.gpg                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages         
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages              
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages        
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/main Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_GB                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/multiverse Sources        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/main amd64 Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/universe amd64 Packages                
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/multiverse amd64 Packages              
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/main Translation-en_GB                 
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/multiverse Translation-en_GB           
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/restricted Translation-en_GB           
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/universe Translation-en_GB             
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty/universe Translation-en                
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/main Sources                   
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/restricted Sources             
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/universe Sources               
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/multiverse Sources             
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/main amd64 Packages            
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/restricted amd64 Packages      
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/universe amd64 Packages        
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages      
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/main i386 Packages             
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/restricted i386 Packages       
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/universe i386 Packages         
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/multiverse i386 Packages       
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-updates/universe Translation-en        
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/main Sources                 
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/universe Sources             
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/multiverse Sources           
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/main amd64 Packages          
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/restricted amd64 Packages    
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/universe amd64 Packages      
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages    
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) trusty-backports/universe Translation-en      
Reading package lists... Done                                                  

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```

---

### Post by peter169 on 2015-01-04
They are package files available from the repositories

---

### Post by ajgreeny on 2015-01-04
Why not copy all the .deb files from /var/cache/apt/archives to a USB drive before you reinstall, then copy them back to /var/cache/apt/archives after reinstalling, then run your update as normal and install everything you want again.

You can get a full list of all that is installed prior to your reinstallation by installing a single package and then running more dpkg commands
```
sudo apt-get install dselect
sudo dpkg --get-selections > install.log
sudo dpkg --set-selections > install.log
sudo dselect
```
I am not sure, however, if that avoids downloading everything again as first copying from, and then copying back to the cache does.

---

