---
title: "After upgrade to 8.04 newer kernel doesnt work?"
date: 2008-04-23
forum: General Help
---

### Post by teryowen on 2008-04-23
Earlier today I upgraded my 7.10 to 8.04 using the update manager, everything went fine. I reboot I now have these entries in my menu.lst file

Ubuntu 8.04, kernel 2.6.24-16-generic 
Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
Ubuntu 8.04, kernel 2.6.22-14-generic
Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
Ubuntu 8.04, memtest86+

Before when i had 7.10 i only had 1 kernel so no problem, now i have 2 different kernel versions? How i dont know? Only the *2-14 one works the *4-16 doesn't work it boots for a while with the ubuntu splash screen and then i get a shell with a initframs (spelling?) prompt or something along those lines.

my question is, should i just use the *2-14 one and not worry about the *4-16. Or should i go about trying to make the *4-16 one work?

Thanks in advance.

---

### Post by giorgosc61 on 2008-04-24
I have the same problem.....is there a solution to this?

---

### Post by kadmiel on 2008-04-24
It sounds like the update didn't completely install the kernel modules.  Try apt-get update again.  . You can always revert back to the original kernel to begin to debugging the problem. You can always check dmesg to see if there was some type of logged event.  I suggest using synaptic to verify that all the kernel packages were in fact installed.

---

### Post by teryowen on 2008-04-24
alright so i tried the sudo apt-get update, and this is what happens:

```

sudo apt-get update
Ign http://ppa.launchpad.net hardy Release.gpg
Ign http://ppa.launchpad.net hardy/main Translation-en_US                                                              
Hit http://archive.canonical.com hardy Release.gpg                                                                     
Ign http://archive.canonical.com hardy/partner Translation-en_US                                 
Get:1 http://ppa.launchpad.net hardy Release [27.6kB]                                             
Hit http://archive.canonical.com hardy Release                                                    
Ign http://ppa.launchpad.net hardy/main Packages                                                                      
Hit http://archive.canonical.com hardy/partner Packages                                           
Hit http://ppa.launchpad.net hardy/main Packages                                                  
Hit http://archive.canonical.com hardy/partner Sources                                            
Hit http://security.ubuntu.com hardy-security Release.gpg                                         
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://us.archive.ubuntu.com hardy Release.gpg                                                                      
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US                                                           
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US                                                     
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US                                                       
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US                                                     
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg                                                              
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US                                                   
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US                                             
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US                                               
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US                                             
Hit http://us.archive.ubuntu.com hardy Release                                                                          
Hit http://us.archive.ubuntu.com hardy-updates Release                                                                  
Hit http://us.archive.ubuntu.com hardy/main Packages                                                                    
Hit http://us.archive.ubuntu.com hardy/restricted Packages                                                              
Hit http://us.archive.ubuntu.com hardy/main Sources                                                                     
Hit http://us.archive.ubuntu.com hardy/restricted Sources                                                               
Hit http://us.archive.ubuntu.com hardy/universe Packages                                                                
Hit http://us.archive.ubuntu.com hardy/universe Sources                                                                 
Hit http://us.archive.ubuntu.com hardy/multiverse Packages                                                              
Hit http://us.archive.ubuntu.com hardy/multiverse Sources                                                               
Hit http://us.archive.ubuntu.com hardy-updates/main Packages                                                            
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages                                                      
Hit http://us.archive.ubuntu.com hardy-updates/main Sources                                                             
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources                                                       
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages                                                        
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources                                                         
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages                                                      
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources                                                       
Fetched 1B in 10s (0B/s)                                                                                                
Reading package lists... Done

```

Not sure what the Hit vs Ign means (i guess igone which wouldnt be good)
and as for using the synaptic maneger it gives me some error as well when its downloading the pacgakges some say Done, others say Failed, and some say Hit. I dont know what to make of this?

Edit: before i ran the sudo apt-get update which i posted above i ran it a few minutes before and during that time it downloaded some things.
[/CODE]

---

