---
title: "Error code-Help"
date: 2007-03-02
forum: General Help
---

### Post by helliewm on 2007-03-02
How do I correct this error code?

E: Sub-process /usr/bin/dpkg returned an error code (1)

I have tried sudo gedit /usr/bin/dpkg

to look at file but see attached screenshot for error message.

I cannot download any more software from the repositories because of it?

Helen

---

### Post by taurus on 2007-03-02
Why do you need to edit /usr/bin/dpkg and besides, you suppose to use gksudo when you use gedit?

What happens when you run these two commands from a terminal?

Applications  -> Accessories  -> Terminal
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by helliewm on 2007-03-02
I want to have a look at gedit to see if was anything obvious I read in a thread a while back for a similar problem. This error occurred after trying to install vmware player.


   
helen@helen-laptop:~$ sudo aptitude update
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release.gpg [191B]                      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Translation-en_US                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                            
Get:3 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]           
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Translation-en_US              
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Translation-en_US                
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/multiverse Translation-en_US              
Get:4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates Release.gpg [191B]              
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Translation-en_US            
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Translation-en_US      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/universe Translation-en_US        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release                                   
Get:5 [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy Release.gpg [191B]                           
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Translation-en_US                         
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates Release                           
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy Release                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Packages                             
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages                
Get:6 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]                       
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Packages                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Packages                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/multiverse Packages                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Sources                              
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                                  
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Sources                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Sources                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/multiverse Sources                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US         
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release.gpg [191B]                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Translation-en_US              
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/universe Packages                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/multiverse Packages    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Sources           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Translation-en_US
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Sources     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/universe Sources     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/multiverse Sources   
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release                 
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
Fetched 9B in 1s (7B/s)  
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: Couldn't rebuild package cache
helen@helen-laptop:~$ 



helen@helen-laptop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.10.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install 
already exists.  Overwrite? [yes] y

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.107.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] y

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
helen@helen-laptop:~$ 

 
helen@helen-laptop:~$ sudo aptitude update
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Translation-en_US                    
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Translation-en_US              
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Translation-en_US                
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/multiverse Translation-en_US              
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates Release.gpg [191B]              
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Translation-en_US            
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Translation-en_US      
Get:4 [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy Release.gpg [191B]                           
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Translation-en_US                         
Get:5 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]           
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US         
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release.gpg [191B]                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Translation-en_US          
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US              
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy Release                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release                        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/universe Translation-en_US        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release                                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates Release                           
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                            
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Packages                             
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Packages                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/multiverse Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Sources                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Sources             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Sources               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/multiverse Sources             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/universe Packages                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/multiverse Packages    
Get:9 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]            
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Sources      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Sources            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/universe Sources                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/multiverse Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources      
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages
Fetched 9B in 1s (7B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: Couldn't rebuild package cache
helen@helen-laptop:~$ 

        
helen@helen-laptop:~$ sudo dpkg --configure -a
Setting up ubuntu-docs (6.10.4.2) ...
E: dpkg was interrupted, you must manually run 'dpkg --confighelen@helen-laptop:lation-en_US          ubuntu.com edgy-security/universe Trans 
bash: Ign: command not found
ure -a' to correct the problem. 
E: Couldn't rebuild package cache
helen@helen-lahelen@helen-laptop:~$ Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/nslation-en_US        
bash: Ign: command not found
ptop:~$ 

helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                            
bash: Hit: command not found
helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release                             
bash: Hit: command not found
helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release                             
bash: Hit: command not found
helen@helen-laptop:~$ Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                            
bash: Hit: command not found
helen@helen-laptop:~$ Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                                  
bash: Ign: command not found
helen@helen-laptop:~$ Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                  
bash: Hit: command not found
helen@helen-laptop:~$ Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Packages                             
bash: Hit: command not found
helen@helen-laptop:~$ Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                                  
bash: Hit: command not found
helen@helen-laptop:~$ Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Packages                       
bash: Hit: command not found
helen@helen-laptop:~$ Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe P
bash: Hit: command not found
helen@helen-laptop:~$ Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/multiverse Packages            
bash: Hit: command not found
helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restrict
bash: Hit: command not found
helen@helen-laptop:~$ Hit [http://gb.archive.ubuntu.co](http://gb.archive.ubuntu.co)
bash: Hit: command not found
helen@helen-laptop:~$ Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) 
bash: Hit: command not found
helen@helen-laptop:~$ Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) ed
bash: Hit: command not found
helen@helen-laptop:~$ Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) ed
bash: Hit: command not found
helen@helen-laptop:~$ Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Package
bash: Hit: command not found
helen@helen-laptop:~$ Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Packages    
bash: Hit: command not found
helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages                      
bash: Hit: command not found
helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages                
bash: Hit: command not found
helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages                  
bash: Hit: command not found
helen@helen-laptop:~$ Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                      
bash: Hit: command not found
helen@helen-laptop:~$ Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/universe Packages                 
bash: Hit: command not found
helen@helen-laptop:~$ Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/multiverse Packages    
bash: Hit: command not found
helen@helen-laptop:~$ Get:9 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]            
bash: Get:9: command not found
helen@helen-laptop:~$ Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US          
bash: Ign: command not found
helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Sources      
bash: Hit: command not found
helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Sources            
bash: Hit: command not found
helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Sources      
bash: Hit: command not found
helen@helen-laptop:~$ Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                
bash: Hit: command not found
helen@helen-laptop:~$ Hit [http://gb.arc](http://gb.arc)
helen@helen-laptop:~$ E: dpkg was interrupted, you must manually run 'dpkg --confighelen@helen-laptop:lation-en_US          ubuntu.com edgy-security/universe Trans 
> bash: Ign: command not found
> ure -a' to correct the problem. 
: Hit: command not found
helen@helen-laptop:~$ Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Sources                
bash: Hit: command not found
helen@helen-laptop:~$ Hit [http://security.ubuntubash:](http://security.ubuntubash:) E:: command not found
helen@helen-laptop:~$ E: Couldn't rebuild package cache
> helen@helen-lahelen@helen-laptop:~$ Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/nslation-en_US        
> bash: Ign: command not found
> ptop:~$ 
> 
> helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                            
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release                             
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release                             
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                            
> bash: Hit: command not found
> helen@helen-laptop:~$ Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                                  
> bash: Ign: command not found
> helen@helen-laptop:~$ Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                  
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Packages                             
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                                  
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Packages                       
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe P
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/multiverse Packages            
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restrict
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://gb.archive.ubuntu.co](http://gb.archive.ubuntu.co)
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) 
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) ed
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) ed
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Package
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Packages    
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages                      
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages                
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages                  
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                      
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/universe Packages                 
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/multiverse Packages    
> bash: Hit: command not found
> helen@helen-laptop:~$ Get:9 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]            
> bash: Get:9: command not found
> helen@helen-laptop:~$ Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US          
> bash: Ign: command not found
> helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Sources      
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Sources            
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Sources      
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Sources                      
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Sources                
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                  
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/universe Sources                  
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/multiverse Sources                
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Sources                   
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Packages                 
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Packages                       
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Packages                 
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Packages                   
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages     
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources            
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources      
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources        
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources      
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                         
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Sources
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Sources
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Sources
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Sources
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
> bash: Hit: command not found
> helen@helen-laptop:~$ Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages
> bash: Hit: command not found
> helen@helen-laptop:~$ Fetched 9B in 1s (7B/s)
> bash: syntax error near unexpected token `('
bash: E:: command not found
helen@helen-laptop:~$ helen@helen-laptop:~$ E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
bash: helen@helen-laptop:~$: command not found
helen@helen-laptop:~$ bash: E:: command not found
bash: bash:: command not found
helen@helen-laptop:~$ helen@helen-laptop:~$ E: Couldn't rebuild package cache
> > helen@helen-laptop:~$ 
> > 
> > 
> 
>

---

### Post by helliewm on 2007-03-02
Solved I found this code  that worked in other thread.

>  I just did
rm -rf /var/lib/dpkg/info/vm*
then
apt-get remove vmware-player

Brilliant this was seriously annoying.

Helen

---

