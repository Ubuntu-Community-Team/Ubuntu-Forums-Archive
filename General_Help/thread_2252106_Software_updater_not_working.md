---
title: "Software updater not working"
date: 2014-11-09
forum: General Help
---

### Post by 12458 on 2014-11-09
Hi,
I am having a problem with software updater saying failed to download repo info
here is the output of sudo apt-get update



```

Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty InRelease
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty Release.gpg
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty Release
Err cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/main amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/restricted amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/main Translation-en_SG
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/main Translation-en
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/restricted Translation-en_SG
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/restricted Translation-en
Ign http://dl.google.com stable InRelease                                      
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release                                        
Get:1 http://dl.google.com stable/main amd64 Packages [1,196 B]                
Get:2 http://dl.google.com stable/main i386 Packages [1,215 B]                 
Ign http://sg.archive.ubuntu.com utopic InRelease                              
Ign http://dl.google.com stable/main Translation-en_SG                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://sg.archive.ubuntu.com utopic-updates InRelease                      
Ign http://sg.archive.ubuntu.com utopic-backports InRelease                    
Ign http://sg.archive.ubuntu.com utopic-proposed InRelease                     
Hit http://sg.archive.ubuntu.com utopic Release.gpg                            
Hit http://sg.archive.ubuntu.com utopic-updates Release.gpg                    
Hit http://sg.archive.ubuntu.com utopic-backports Release.gpg                  
Hit http://sg.archive.ubuntu.com utopic-proposed Release.gpg                   
Ign http://ppa.launchpad.net utopic InRelease                                  
Hit http://sg.archive.ubuntu.com utopic Release                                
Hit http://sg.archive.ubuntu.com utopic-updates Release                        
Hit http://sg.archive.ubuntu.com utopic-backports Release                      
Ign http://archive.canonical.com trusty InRelease                              
Hit http://sg.archive.ubuntu.com utopic-proposed Release                       
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://sg.archive.ubuntu.com utopic/main amd64 Packages                    
Ign http://ppa.launchpad.net utopic InRelease                                  
Hit http://archive.canonical.com trusty Release.gpg                            
Ign http://security.ubuntu.com utopic-security InRelease                       
Ign http://extras.ubuntu.com utopic InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com trusty Release                                
Hit http://security.ubuntu.com utopic-security Release.gpg                     
Hit http://extras.ubuntu.com utopic Release.gpg                                
Hit http://ppa.launchpad.net utopic Release.gpg                                
Hit http://sg.archive.ubuntu.com utopic/universe i386 Packages                 
Hit http://sg.archive.ubuntu.com utopic/multiverse i386 Packages               
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://security.ubuntu.com utopic-security Release                         
Hit http://extras.ubuntu.com utopic Release                                    
Hit http://ppa.launchpad.net utopic Release.gpg                                
Get:3 http://sg.archive.ubuntu.com utopic-updates/multiverse Sources [14 B]    
Hit http://sg.archive.ubuntu.com utopic-updates/main amd64 Packages            
Hit http://extras.ubuntu.com utopic/main Sources                               
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://security.ubuntu.com utopic-security/restricted Sources              
Hit http://extras.ubuntu.com utopic/main amd64 Packages                        
Hit http://ppa.launchpad.net utopic Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://security.ubuntu.com utopic-security/universe Sources                
Hit http://extras.ubuntu.com utopic/main i386 Packages                         
Hit http://sg.archive.ubuntu.com utopic-updates/universe Translation-en        
Hit http://sg.archive.ubuntu.com utopic-backports/main Sources                 
Hit http://sg.archive.ubuntu.com utopic-backports/restricted Sources           
Hit http://sg.archive.ubuntu.com utopic-backports/universe Sources             
Hit http://ppa.launchpad.net utopic Release                                    
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://sg.archive.ubuntu.com utopic-backports/restricted amd64 Packages    
Hit http://security.ubuntu.com utopic-security/multiverse Sources              
Hit http://sg.archive.ubuntu.com utopic-backports/universe amd64 Packages      
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://sg.archive.ubuntu.com utopic-backports/restricted i386 Packages     
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://sg.archive.ubuntu.com utopic-backports/universe i386 Packages       
Hit http://sg.archive.ubuntu.com utopic-backports/multiverse Translation-en    
Hit http://sg.archive.ubuntu.com utopic-backports/restricted Translation-en    
Hit http://sg.archive.ubuntu.com utopic-backports/universe Translation-en      
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Get:4 http://sg.archive.ubuntu.com utopic-proposed/restricted Sources [1,752 B]
Hit http://security.ubuntu.com utopic-security/restricted amd64 Packages       
Ign http://archive.canonical.com trusty/partner Translation-en                 
Hit http://sg.archive.ubuntu.com utopic/main Sources                           
Hit http://security.ubuntu.com utopic-security/multiverse amd64 Packages       
Hit http://sg.archive.ubuntu.com utopic/restricted Sources                     
Hit http://sg.archive.ubuntu.com utopic/multiverse Translation-en              
Hit http://sg.archive.ubuntu.com utopic/universe Translation-en                
Hit http://security.ubuntu.com utopic-security/restricted i386 Packages        
Get:5 http://sg.archive.ubuntu.com utopic-updates/restricted Sources [13.8 kB] 
Get:6 http://sg.archive.ubuntu.com utopic-updates/universe Sources [40 B]      
Hit http://ppa.launchpad.net utopic/main amd64 Packages                        
Ign http://extras.ubuntu.com utopic/main Translation-en_SG                     
Hit http://sg.archive.ubuntu.com utopic-updates/restricted Translation-en
Hit http://security.ubuntu.com utopic-security/multiverse i386 Packages        
Hit http://sg.archive.ubuntu.com utopic-backports/multiverse Sources           
Hit http://ppa.launchpad.net utopic/main i386 Packages                         
Hit http://sg.archive.ubuntu.com utopic-backports/main amd64 Packages          
Hit http://sg.archive.ubuntu.com utopic-backports/multiverse amd64 Packages    
Hit http://sg.archive.ubuntu.com utopic-backports/main i386 Packages           
Hit http://sg.archive.ubuntu.com utopic-backports/multiverse i386 Packages     
Ign http://extras.ubuntu.com utopic/main Translation-en                        
Hit http://sg.archive.ubuntu.com utopic-backports/main Translation-en          
Hit http://ppa.launchpad.net utopic/main Translation-en                        
Get:7 http://sg.archive.ubuntu.com utopic-proposed/multiverse Sources [40 B]   
Hit http://ppa.launchpad.net trusty/main Sources                               
Hit http://sg.archive.ubuntu.com utopic-proposed/universe amd64 Packages       
Hit http://sg.archive.ubuntu.com utopic-proposed/restricted amd64 Packages     
Hit http://security.ubuntu.com utopic-security/multiverse Translation-en       
Hit http://ppa.launchpad.net utopic/main amd64 Packages                        
Hit http://ppa.launchpad.net utopic/main i386 Packages                         
Hit http://ppa.launchpad.net utopic/main Translation-en                        
Hit http://security.ubuntu.com utopic-security/restricted Translation-en       
Hit http://ppa.launchpad.net trusty/main Sources                               
Err http://sg.archive.ubuntu.com utopic/multiverse Sources            
  Bad header line
Err http://sg.archive.ubuntu.com utopic/universe amd64 Packages
  Bad header line
Err http://sg.archive.ubuntu.com utopic/main i386 Packages
  404  Not Found
Err http://sg.archive.ubuntu.com utopic/restricted i386 Packages
  404  Not Found
Err http://sg.archive.ubuntu.com utopic-updates/main Sources
  404  Not Found
Err http://sg.archive.ubuntu.com utopic-updates/restricted amd64 Packages
  404  Not Found
Hit http://security.ubuntu.com utopic-security/main Sources
Err http://sg.archive.ubuntu.com utopic-updates/universe amd64 Packages
  404  Not Found
Err http://sg.archive.ubuntu.com utopic-updates/multiverse amd64 Packages
  404  Not Found
Err http://sg.archive.ubuntu.com utopic-updates/main i386 Packages             
  404  Not Found
Err http://sg.archive.ubuntu.com utopic-updates/restricted i386 Packages       
  404  Not Found
Err http://sg.archive.ubuntu.com utopic-updates/universe i386 Packages         
  404  Not Found
Hit http://security.ubuntu.com utopic-security/main amd64 Packages             
Err http://sg.archive.ubuntu.com utopic-updates/multiverse i386 Packages       
  404  Not Found
Hit http://sg.archive.ubuntu.com utopic-updates/main Translation-en            
Hit http://sg.archive.ubuntu.com utopic-updates/multiverse Translation-en      
Err http://sg.archive.ubuntu.com utopic-proposed/universe Sources              
  404  Not Found
Err http://sg.archive.ubuntu.com utopic-proposed/main Sources                  
  404  Not Found
Err http://sg.archive.ubuntu.com utopic-proposed/multiverse amd64 Packages     
  404  Not Found
Hit http://security.ubuntu.com utopic-security/universe amd64 Packages         
Hit http://sg.archive.ubuntu.com utopic-proposed/main amd64 Packages           
Err http://sg.archive.ubuntu.com utopic-proposed/multiverse i386 Packages      
  404  Not Found
Hit http://sg.archive.ubuntu.com utopic-proposed/universe i386 Packages        
Err http://sg.archive.ubuntu.com utopic-proposed/restricted i386 Packages      
  404  Not Found
Hit http://sg.archive.ubuntu.com utopic-proposed/main i386 Packages            
Hit http://sg.archive.ubuntu.com utopic-proposed/main Translation-en           
Hit http://sg.archive.ubuntu.com utopic-proposed/multiverse Translation-en     
Hit http://security.ubuntu.com utopic-security/main i386 Packages              
Hit http://sg.archive.ubuntu.com utopic-proposed/restricted Translation-en     
Hit http://sg.archive.ubuntu.com utopic-proposed/universe Translation-en       
Hit http://sg.archive.ubuntu.com utopic/universe Sources                       
Err http://sg.archive.ubuntu.com utopic/restricted amd64 Packages              
  404  Not Found
Err http://sg.archive.ubuntu.com utopic/multiverse amd64 Packages              
  404  Not Found
Hit http://security.ubuntu.com utopic-security/universe i386 Packages          
Hit http://sg.archive.ubuntu.com utopic/restricted Translation-en              
Hit http://security.ubuntu.com utopic-security/main Translation-en             
Hit http://sg.archive.ubuntu.com utopic/main Translation-en                    
Hit http://security.ubuntu.com utopic-security/universe Translation-en         
Fetched 18.0 kB in 7s (2,399 B/s)                                              
W: Failed to fetch cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)/dists/trusty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)/dists/trusty/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)/dists/trusty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)/dists/trusty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/utopic/multiverse/source/Sources  Bad header line


W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/utopic/restricted/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/utopic/universe/binary-amd64/Packages  Bad header line


W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/utopic/multiverse/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/utopic/main/binary-i386/Packages  404  Not Found


W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/utopic/restricted/binary-i386/Packages  404  Not Found


W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/utopic-updates/main/source/Sources  404  Not Found


W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/utopic-updates/restricted/source/Sources  Hash Sum mismatch


W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/utopic-updates/restricted/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/utopic-updates/universe/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/utopic-updates/multiverse/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/utopic-updates/main/binary-i386/Packages  404  Not Found


W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/utopic-updates/restricted/binary-i386/Packages  404  Not Found


W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/utopic-updates/universe/binary-i386/Packages  404  Not Found


W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/utopic-updates/multiverse/binary-i386/Packages  404  Not Found


W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/utopic-proposed/universe/source/Sources  404  Not Found


W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/utopic-proposed/restricted/source/Sources  Hash Sum mismatch


W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/utopic-proposed/main/source/Sources  404  Not Found


W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/utopic-proposed/multiverse/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/utopic-proposed/multiverse/binary-i386/Packages  404  Not Found


W: Failed to fetch http://sg.archive.ubuntu.com/ubuntu/dists/utopic-proposed/restricted/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.



```

---

### Post by deadflowr on 2014-11-09
Open up the program called "Software and Updates".
Then first go to the section marked "Other Software"

Uncheck the entries for CDROM:
(They should be the top entries)

Then go back to the section "Ubuntu Software"
And click on the box next to the line Download from:
You should have three options, Main Server, Server where you are, and Other.
Go To Other and in the top right section should be a button for Choose best server, or something like that, click on it and the system will look for the best server for you.
When it finishes, select OK and then close the program and re-run the update command.
See if that helps.

---

### Post by claracc on 2014-11-09
You have a messed /etc/apt/sources.list file where there are repositories from trusty and utopic. What is the ubuntu release you are running?, trusty or utopic?, have you tried to upgrade release and it went bad?.

To avoid the cd-rom error you will have to disable the download from cd-rom in update manager. Also you have added ppa repositories as [http://dl.google.com](http://dl.google.com) stable/main Translation-en_SG which can give errors, try to disable them from software sources in update manager.

I think the straight forward solution will be to reinstall ubuntu, but you can wait for more expertize advice.

---

### Post by 12458 on 2014-11-10
> **deadflowr said:**
> Open up the program called "Software and Updates".
Then first go to the section marked "Other Software"

Uncheck the entries for CDROM:
(They should be the top entries)

Then go back to the section "Ubuntu Software"
And click on the box next to the line Download from:
You should have three options, Main Server, Server where you are, and Other.
Go To Other and in the top right section should be a button for Choose best server, or something like that, click on it and the system will look for the best server for you.
When it finishes, select OK and then close the program and re-run the update command.
See if that helps.
Thanks it worked :)

---

