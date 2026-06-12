---
title: "System crash - reinstall then unable to update"
date: 2015-11-02
forum: General Help
---

### Post by bobmac on 2015-11-02
Folks,

I'm running a dual-boot system with windows 7 and ubuntu 12.04. Today when attempting to start ubuntu, my system stopped working. I tried everything to fix the problem with no result. Tried a startup disk, the supergrup with no joy.

I ended up reinstalling v 12.04 sucessfully. However, the system informed me that there were some 400 odd updates to install. This is where the problem occurred. Ubuntu informed me that it could not connect to the internet.

I then tried to update using 'sudo apt-get update'. The result here was as follows: (I've only copied a portion of what the update showed on the terminal)

```
sudo apt-get update
[sudo] password for calban: 
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                    
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise Release.gpg                           
  Something wicked happened resolving 'au.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                          
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates Release.gpg                   
  Something wicked happened resolving 'au.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports Release.gpg                 
  Something wicked happened resolving 'au.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources/DiffIndex         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources/DiffIndex               
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise Release                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources/DiffIndex   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages/DiffIndex             
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates Release                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources/DiffIndex     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages/DiffIndex       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports Release                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources/DiffIndex
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/main Sources/DiffIndex                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages/DiffIndex  
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/restricted Sources/DiffIndex          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages/DiffIndex
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/universe Sources/DiffIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages/DiffIndex
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/multiverse Sources/DiffIndex          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages/DiffIndex   
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/main amd64 Packages/DiffIndex         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages/DiffIndex
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/restricted amd64 Packages/DiffIndex   
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/universe amd64 Packages/DiffIndex     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages/DiffIndex
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/multiverse amd64 Packages/DiffIndex   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages/DiffIndex
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/main i386 Packages/DiffIndex          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/restricted i386 Packages/DiffIndex    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/universe i386 Packages/DiffIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/multiverse i386 Packages/DiffIndex    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/main TranslationIndex                 
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/multiverse TranslationIndex           
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/restricted TranslationIndex           
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/universe TranslationIndex             
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/main Sources/DiffIndex        
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/restricted Sources/DiffIndex  
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/universe Sources/DiffIndex    
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/multiverse Sources/DiffIndex  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname) and so on
```

Can anyone give me a clue as to the problem.

Regards,

Bob

---

### Post by DK1993 on 2015-11-02
So assuming that Ubuntu connected to the Internet knowing there were 400 updates, my only guess would be that there might be a DNS error somewhere. Are you able to try on a different device to see if it is resolving any of the above repo URLs in a web browser?

---

### Post by bobmac on 2015-11-02
DK1993,
OK I found out that I had to set up the router again so now I've got proper internet connection.

Tried again to download the updates, This time I get the message ---

 Requires installation of untrusted packages
The action would require the installation of packages from sources that are not authenticated.

I've no idea what this means

Regards,

Bob

---

### Post by mörgæs on 2015-11-02
Normally I don't like the answer "just google it" but in this case there are actually many good pages explaining what is going on.

Better than me rewriting the pages I guess it's faster for all of us if you search for the answer.

Besides, if you had to reinstall why did you choose the old 12.04?

---

