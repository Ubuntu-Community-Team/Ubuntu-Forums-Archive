---
title: "Unable to locate package? Need help installing PS3 Media Server"
date: 2013-12-07
forum: General Help
---

### Post by jferreir on 2013-12-07
I can't figure out how to install PS3 Media Server, as I keep getting various errors in Terminal. I also noticed a few errors when I run "sudo apt-get update". I have no idea what these errors mean, or if they are related in any way. The only thing I have done to the system files was to remove the various "scopes" (I don't even know if I did this right, or if it worked), but this is otherwise a fresh install of Ubuntu 13.10. The PS3 MS website says it supports 13.04, but I assume there's some way to get it working under 13.10 too. I need idiot-proof, step-by-step instructions, if someone would be so kind. 

Here are the errors:

```
Ign http://ca.archive.ubuntu.com saucy InRelease
Ign http://ca.archive.ubuntu.com saucy-updates InRelease                       
Ign http://ca.archive.ubuntu.com saucy-backports InRelease                     
Ign http://ppa.launchpad.net saucy InRelease                         
Ign http://security.ubuntu.com saucy-security InRelease              
Ign http://extras.ubuntu.com saucy InRelease                         
Hit http://ca.archive.ubuntu.com saucy Release.gpg                   
Ign http://ppa.launchpad.net saucy InRelease                         
Get:1 http://security.ubuntu.com saucy-security Release.gpg [933 B]  
Hit http://extras.ubuntu.com saucy Release.gpg                                 
Hit http://ca.archive.ubuntu.com saucy-updates Release.gpg           
Ign http://ppa.launchpad.net saucy Release.gpg                       
Hit http://ca.archive.ubuntu.com saucy-backports Release.gpg         
Hit http://ca.archive.ubuntu.com saucy Release                       
Get:2 http://security.ubuntu.com saucy-security Release [49.6 kB]              
Hit http://extras.ubuntu.com saucy Release                                     
Hit http://ca.archive.ubuntu.com saucy-updates Release                         
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Hit http://ca.archive.ubuntu.com saucy-backports Release                       
Hit http://ca.archive.ubuntu.com saucy/main Sources                            
Ign http://ppa.launchpad.net saucy Release                                     
Hit http://extras.ubuntu.com saucy/main Sources                                
Hit http://ca.archive.ubuntu.com saucy/restricted Sources                      
Hit http://ca.archive.ubuntu.com saucy/universe Sources                        
Hit http://ca.archive.ubuntu.com saucy/multiverse Sources                      
Hit http://ppa.launchpad.net saucy Release                                     
Hit http://extras.ubuntu.com saucy/main amd64 Packages                         
Hit http://ca.archive.ubuntu.com saucy/main amd64 Packages                     
Hit http://ca.archive.ubuntu.com saucy/restricted amd64 Packages         
Hit http://ca.archive.ubuntu.com saucy/universe amd64 Packages        
Hit http://extras.ubuntu.com saucy/main i386 Packages                 
Get:3 http://security.ubuntu.com saucy-security/main Sources [14.3 kB]
Hit http://ca.archive.ubuntu.com saucy/multiverse amd64 Packages               
Get:4 http://security.ubuntu.com saucy-security/restricted Sources [14 B]      
Hit http://ca.archive.ubuntu.com saucy/main i386 Packages                      
Hit http://ca.archive.ubuntu.com saucy/restricted i386 Packages                
Hit http://ca.archive.ubuntu.com saucy/universe i386 Packages         
Get:5 http://security.ubuntu.com saucy-security/universe Sources [6,794 B]
Hit http://ca.archive.ubuntu.com saucy/multiverse i386 Packages                
Hit http://ca.archive.ubuntu.com saucy/main Translation-en_CA                  
Hit http://ca.archive.ubuntu.com saucy/main Translation-en            
Get:6 http://security.ubuntu.com saucy-security/multiverse Sources [688 B]
Hit http://ppa.launchpad.net saucy/main amd64 Packages                         
Hit http://ca.archive.ubuntu.com saucy/multiverse Translation-en               
Hit http://ppa.launchpad.net saucy/main i386 Packages                 
Get:7 http://security.ubuntu.com saucy-security/main amd64 Packages [42.6 kB]
Hit http://ca.archive.ubuntu.com saucy/restricted Translation-en               
Hit http://ca.archive.ubuntu.com saucy/universe Translation-en_CA              
Hit http://ca.archive.ubuntu.com saucy/universe Translation-en                 
Hit http://ca.archive.ubuntu.com saucy-updates/main Sources                    
Hit http://ca.archive.ubuntu.com saucy-updates/restricted Sources              
Hit http://ca.archive.ubuntu.com saucy-updates/universe Sources                
Hit http://ca.archive.ubuntu.com saucy-updates/multiverse Sources              
Hit http://ca.archive.ubuntu.com saucy-updates/main amd64 Packages             
Get:8 http://security.ubuntu.com saucy-security/restricted amd64 Packages [14 B]
Ign http://extras.ubuntu.com saucy/main Translation-en_CA                      
Hit http://ca.archive.ubuntu.com saucy-updates/restricted amd64 Packages       
Get:9 http://security.ubuntu.com saucy-security/universe amd64 Packages [17.3 kB]
Ign http://extras.ubuntu.com saucy/main Translation-en                         
Hit http://ca.archive.ubuntu.com saucy-updates/universe amd64 Packages         
Hit http://ca.archive.ubuntu.com saucy-updates/multiverse amd64 Packages       
Hit http://ca.archive.ubuntu.com saucy-updates/main i386 Packages
Hit http://ca.archive.ubuntu.com saucy-updates/restricted i386 Packages
Hit http://ca.archive.ubuntu.com saucy-updates/universe i386 Packages
Hit http://ca.archive.ubuntu.com saucy-updates/multiverse i386 Packages        
Get:10 http://security.ubuntu.com saucy-security/multiverse amd64 Packages [1,155 B]
Hit http://ca.archive.ubuntu.com saucy-updates/main Translation-en             
Hit http://ca.archive.ubuntu.com saucy-updates/multiverse Translation-en
Get:11 http://security.ubuntu.com saucy-security/main i386 Packages [42.4 kB]
Hit http://ca.archive.ubuntu.com saucy-updates/restricted Translation-en       
Hit http://ca.archive.ubuntu.com saucy-updates/universe Translation-en         
Hit http://ca.archive.ubuntu.com saucy-backports/main Sources
Hit http://ca.archive.ubuntu.com saucy-backports/restricted Sources
Hit http://ca.archive.ubuntu.com saucy-backports/universe Sources
Hit http://ca.archive.ubuntu.com saucy-backports/multiverse Sources
Hit http://ca.archive.ubuntu.com saucy-backports/main amd64 Packages
Hit http://ca.archive.ubuntu.com saucy-backports/restricted amd64 Packages
Hit http://ca.archive.ubuntu.com saucy-backports/universe amd64 Packages
Hit http://ca.archive.ubuntu.com saucy-backports/multiverse amd64 Packages
Hit http://ca.archive.ubuntu.com saucy-backports/main i386 Packages
Hit http://ca.archive.ubuntu.com saucy-backports/restricted i386 Packages      
Hit http://ca.archive.ubuntu.com saucy-backports/universe i386 Packages
Hit http://ca.archive.ubuntu.com saucy-backports/multiverse i386 Packages
Get:12 http://security.ubuntu.com saucy-security/restricted i386 Packages [14 B]
Hit http://ca.archive.ubuntu.com saucy-backports/main Translation-en           
Get:13 http://security.ubuntu.com saucy-security/universe i386 Packages [17.6 kB]
Hit http://ca.archive.ubuntu.com saucy-backports/multiverse Translation-en     
Hit http://ca.archive.ubuntu.com saucy-backports/restricted Translation-en     
Hit http://ca.archive.ubuntu.com saucy-backports/universe Translation-en       
Err http://ppa.launchpad.net saucy/main amd64 Packages                
  404  Not Found
Get:14 http://security.ubuntu.com saucy-security/multiverse i386 Packages [1,389 B]
Err http://ppa.launchpad.net saucy/main i386 Packages                          
  404  Not Found
Ign http://ppa.launchpad.net saucy/main Translation-en_CA             
Ign http://ppa.launchpad.net saucy/main Translation-en
Hit http://security.ubuntu.com saucy-security/main Translation-en
Ign http://ppa.launchpad.net saucy/main Translation-en_CA
Hit http://security.ubuntu.com saucy-security/multiverse Translation-en
Ign http://ppa.launchpad.net saucy/main Translation-en                         
Hit http://security.ubuntu.com saucy-security/restricted Translation-en        
Hit http://security.ubuntu.com saucy-security/universe Translation-en          
Ign http://ca.archive.ubuntu.com saucy/multiverse Translation-en_CA            
Ign http://ca.archive.ubuntu.com saucy/restricted Translation-en_CA            
Ign http://ca.archive.ubuntu.com saucy-updates/main Translation-en_CA          
Ign http://ca.archive.ubuntu.com saucy-updates/multiverse Translation-en_CA    
Ign http://ca.archive.ubuntu.com saucy-updates/restricted Translation-en_CA    
Ign http://ca.archive.ubuntu.com saucy-updates/universe Translation-en_CA      
Ign http://ca.archive.ubuntu.com saucy-backports/main Translation-en_CA        
Ign http://ca.archive.ubuntu.com saucy-backports/multiverse Translation-en_CA  
Ign http://ca.archive.ubuntu.com saucy-backports/restricted Translation-en_CA  
Ign http://ca.archive.ubuntu.com saucy-backports/universe Translation-en_CA    
Ign http://security.ubuntu.com saucy-security/main Translation-en_CA           
Ign http://security.ubuntu.com saucy-security/multiverse Translation-en_CA     
Ign http://security.ubuntu.com saucy-security/restricted Translation-en_CA     
Ign http://security.ubuntu.com saucy-security/universe Translation-en_CA       
Fetched 195 kB in 9s (21.5 kB/s)                                               
W: Failed to fetch http://ppa.launchpad.net/happy-neko/ps3mediaserver/ubuntu/dists/saucy/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/happy-neko/ps3mediaserver/ubuntu/dists/saucy/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
jason@jason-All-Series:~$ sudo apt-get install ps3mediaserver
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ps3mediaserver
jason@jason-All-Series:~$ 

```

Thank you!

---

### Post by drmrgd on 2013-12-07
That error basically means that the author of the launchpad page has not yet updated the packages for Saucy.  I had a quick look at the Launchpad page, and sure enough, the most recent release there is for 13.04.  So, you won't be able to use the package manager to install ps3mediaserver from that PPA.

I don't know a lot about that package, but there seems to be two obvious solutions:


[LIST=1]
[*]Wait for the author to update the repository with compatibility for 13.10.
[*]Install the package (and any dependencies manually)
[/LIST]

I did a quick Google search for that package and found this thread at ps3media.org:

[http://www.ps3mediaserver.org/forum/viewtopic.php?f=3&t=17399](http://www.ps3mediaserver.org/forum/viewtopic.php?f=3&t=17399)

The last post suggests that you can manually change the repository entry to point to the Raring PPA and use that to install even though you're running Saucy.  Not sure that's a great idea, as you may run into trouble with any conflicting dependencies.  But, if you're feeling adventurous, you could possibly try that.  The thread also has a link and some instructions for how to build the package manually if you want to go that route.

Always, the problem with being on the bleeding edge of distributions is package compatibility.  ;)

---

### Post by jferreir on 2013-12-08
Sorry, I'm not the best with computers at all, so this is all foreign to me. After a bit of trial and error, I think I managed to install it manually. God awful menu bar icon, though. Thanks for the help!

---

