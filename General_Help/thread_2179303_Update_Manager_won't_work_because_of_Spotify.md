---
title: "Update Manager won't work because of Spotify"
date: 2013-10-07
forum: General Help
---

### Post by TravisMarkus on 2013-10-07
I am a noob when it comes to Linux and I am looking for some help with my update manager. I am running Ubuntu 12.04 and I only have it on my laptop which I don't use on a daily basis. A few months ago I was very happy to learn I could finally get Spotify on Ubuntu and I installed it - the version I have is 0.9.0.133.gd18ed589. Well, Spotify works great but shortly after I got it I noticed an update for it in the Update Manager. However, I get an error message saying, "Error authenticating some packages. It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages." The only thing in the list is "spotify-client." Now, whenever I try to do ANY updates I get a dialog box that says "Not all updates can be installed. Run a partial upgrade, to install as many updates as possible." Here I can either run a partial upgrade or close it. Well I have tried running the partial upgrade and I have tried going through beforehand and manually unchecking the Spotify update to bypass it, but either way it still ends up running for a while and then giving me the same "Error authenticating some packages" message. 

Lo and behold I have 187 updates that have accumulated and I would like to just install them. I tried searching around for solutions and I found one that instructed me to run some commands in Terminal. I can't find the same thread but the code had to do with "clean" something. When I ran it, all the updates seemed to take place in Terminal but the next time I started my computer up, there were the 187 updates still waiting. It's to the point where I am willing to uninstall Spotify to get stuff to update, but when I searched how to do THAT I couldn't find any solution either. The only thread I found had commands with "sudo aptitude..." and commands for removing and purging Wine. Everything I tried came back "aptitude is not a recognized command." So, I would prefer to keep Spotify, but if I have to get rid of it, whatever.

Thank you for any and all assistance.

---

### Post by Patrick_Burger on 2013-10-07
first  things first open a terminal (CTRL + T) and type in 
```

"sudo apt-get clean"

```
then supply your password (it will not show up as anything not even asterisks, this is normal. After that has returned you to the command promt, type 
```

sudo apt-get update

```
if you notice any errors there, please post them in the forums here. if you do not notice any problems, type 
```

sudo apt-get upgrade

```

If the cache has been corrupted or is pulling from an outdated source this will clear the cached repositories and find the current ones. then it will update with the new information and complete your updates. 

I hope this helps, if not, it's the first trouble shooting step. To me it sounds like a bad cache though.

---

### Post by michaelcranie on 2013-10-07
Looks like you haven't installed the spotify repository follow the  instructions in this link   /http://www.omgubuntu.co.uk/2013/01/how-to-install-spotify-in-ubuntu-12-04-12-10#content    . If you want to use the terminalcopy paste the following code
```
sudo add-apt-repository "deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free"
[I]sudo apt-key adv --keyserver keyserver.ubuntu.com--recv-keys 94558F59
[/I]sudo apt-get update && sudo apt-get install spotify-client
```

---

### Post by TravisMarkus on 2013-10-07
When I ran sudo-apt-get update it ran a whole bunch of stuff and everything seemed to be going fine and then i got this line

W: GPG error: [http://repository.spotify.com](http://repository.spotify.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 082CCEDF94558F59

Then I ran sudo upgrade and it took a long time but I saw no errors and it seemed to complete. I restarted and the Update Manager never popped back up. I came on here to post about it and then I saw the message from Michaelcranie so I tried what he said too, especially as it seems to be related. However, after running the second line of his code I got the following

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.OvOB81Dgrl --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com--recv-keys 94558f59
gpg: can't open `94558f59'


As far as my update issue, it seems to be resolved, but if you guys have answers on how to fix Spotify so I don't have this problem in the future, that would be awesome. Either way, thanks for clearing up the major headache!

---

### Post by oldos2er on 2013-10-07
You might need to try putting the entire alphanumeric in the command: ```
sudo apt-key adv --keyserver keyserver.ubuntu.com--recv-keys 082CCEDF94558F59
```

---

### Post by TravisMarkus on 2013-10-08
> **oldos2er said:**
> You might need to try putting the entire alphanumeric in the command: ```
sudo apt-key adv --keyserver keyserver.ubuntu.com--recv-keys 082CCEDF94558F59
```

I tried this too and got the same error message 

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.597IEKVh1L --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com--recv-keys 082CCEDF94558F59
gpg: can't open `082CCEDF94558F59'


bummer.

---

### Post by oldos2er on 2013-10-08
Ok, try ```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 082CCEDF94558F59
```

---

### Post by michaelcranie on 2013-10-08
Only just noticed the key  on the ppa didn't work for me either. the one in the post above is ok.By the way oldos2er do you really need the keyserver.

---

### Post by oldos2er on 2013-10-09
Do you mean the "--keyserver" bit in the command? gpg needs to know where to get the key from, so yeah.

---

### Post by TravisMarkus on 2013-10-13
> **oldos2er said:**
> Ok, try ```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 082CCEDF94558F59
```

OK so I tried this line of code and it worked. Then when I did the third orignal line of code (sudo apt-get update && sudo apt-get install spotify-client) I got the following readout (sorry it's long)

```
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Get:3 [http://repository.spotify.com](http://repository.spotify.com) stable Release.gpg [489 B]                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                    
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [71 B]                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                     
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://repository.spotify.com](http://repository.spotify.com) stable Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise Release.gpg                          
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise Release                              
Ign [http://repository.spotify.com](http://repository.spotify.com) stable Release                               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free amd64 Packages/DiffIndex        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free amd64 Packages/DiffIndex    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages/DiffIndex         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages/DiffIndex     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free TranslationIndex                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free TranslationIndex            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11.9 kB]                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Sources/DiffIndex            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free amd64 Packages                  
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free amd64 Packages              
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages                   
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages               
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en_US               
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en                  
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en_US           
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en              
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [420 kB]       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages         
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free amd64 Packages/DiffIndex     
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free i386 Packages/DiffIndex      
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free TranslationIndex             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [1,826 B]                  
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages [3,002 B]           
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [3,789 B]           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [7,006 B]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [97.8 kB] 
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [8,343 B]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [695 kB]
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Sources                      
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free amd64 Packages               
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free i386 Packages                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US            
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [11.5 kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [219 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [13.9 kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [715 kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [11.4 kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [223 kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [14.0 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en     
Fetched 2,507 kB in 8s (289 kB/s)                                              
W: GPG error: [http://repository.spotify.com](http://repository.spotify.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 082CCEDF94558F59
W: Failed to fetch [http://packages.medibuntu.org/dists/precise/Release.gpg](http://packages.medibuntu.org/dists/precise/Release.gpg)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/free/binary-amd64/Packages](http://packages.medibuntu.org/dists/precise/free/binary-amd64/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/binary-amd64/Packages](http://packages.medibuntu.org/dists/precise/non-free/binary-amd64/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en_US](http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en_US)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en_US](http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en_US)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by Bashing-om on 2013-10-13
TravisMarkus; Hi !

The medibuntu edition/repository is no longer maintained, It is now a part of our history and as such, disable that source in "other software".
For the signing key after you have disabled "medibuntu", try:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com  082CCEDF94558F59

```
Hoping our server holds spotify's keys.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

