---
title: "Cannot install new software and cannot update software"
date: 2015-05-15
forum: General Help
---

### Post by kindafunnylookin on 2015-05-15
When I try to install new software using Ubuntu Software Center I get this message:
       [B][I]"New software cannot be installed because there is a problem with the
         software currently installed. Do you want to repair this problem now?"[/I][/B]
There is a check box to "Repair" and another to "Ignore" I check "Repair" and it starts another
message like the one above.

I have also been getting another message that the kernel cannot update because the boot
partition is full.

It seems to me that these two problems must be connected in some way but I'm stuck.

---

### Post by v3.xx on 2015-05-15
Do a terminal update/upgrade and post any errors
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by kindafunnylookin on 2015-05-15
```
peter@TosTec-Ubuntu-14:~$ sudo apt-get update
Get:1 http://repository.spotify.com stable InRelease [2,954 B]
Ign http://dl.google.com stable InRelease                                      
Ign http://repository.spotify.com stable InRelease                             
Ign http://repository.spotify.com stable/non-free amd64 Packages/DiffIndex     
Hit http://dl.google.com stable Release.gpg                                    
Ign http://repository.spotify.com stable/non-free i386 Packages/DiffIndex      
Hit http://dl.google.com stable Release                                        
Hit http://dl.google.com stable/main amd64 Packages                            
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://us.archive.ubuntu.com trusty InRelease                              
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://security.ubuntu.com trusty-security Release.gpg                     
Ign http://us.archive.ubuntu.com trusty-updates InRelease                      
Ign http://archive.canonical.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://repository.spotify.com stable/non-free amd64 Packages               
Hit http://security.ubuntu.com trusty-security Release                         
Ign http://us.archive.ubuntu.com trusty-backports InRelease                    
Hit http://repository.spotify.com stable/non-free i386 Packages                
Ign http://repository.spotify.com stable/non-free Translation-en_US            
Ign http://repository.spotify.com stable/non-free Translation-en               
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://security.ubuntu.com trusty-security/main Sources                    
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://archive.canonical.com trusty Release.gpg                            
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty-updates Release.gpg                    
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg                  
Hit http://security.ubuntu.com trusty-security/universe Sources                
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://archive.canonical.com trusty Release                                
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Hit http://us.archive.ubuntu.com trusty-updates Release                        
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://extras.ubuntu.com trusty/main Sources                               
Ign http://ppa.launchpad.net trusty Release.gpg                                
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://us.archive.ubuntu.com trusty-backports Release                      
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Ign https://private-ppa.launchpad.net trusty InRelease                         
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit https://private-ppa.launchpad.net trusty Release.gpg                       
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Get:2 http://archive.canonical.com trusty/partner Translation-en [4,588 B]     
Ign http://ppa.launchpad.net trusty Release                                    
Hit https://private-ppa.launchpad.net trusty Release                           
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Hit http://ppa.launchpad.net trusty Release                                    
Hit https://private-ppa.launchpad.net trusty/main amd64 Packages               
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit https://private-ppa.launchpad.net trusty/main i386 Packages                
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en  
Ign http://extras.ubuntu.com trusty/main Translation-en_US         
Hit http://ppa.launchpad.net trusty/main Sources                   
Hit http://us.archive.ubuntu.com trusty/universe Translation-en    
Ign http://extras.ubuntu.com trusty/main Translation-en            
Hit http://ppa.launchpad.net trusty/main amd64 Packages            
Hit http://us.archive.ubuntu.com trusty-updates/main Sources       
Hit http://us.archive.ubuntu.com trusty-updates/restricted Sources
Hit http://ppa.launchpad.net trusty/main i386 Packages                    
Hit http://us.archive.ubuntu.com trusty-updates/universe Sources          
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Sources  
Hit http://ppa.launchpad.net trusty/main Translation-en
Ign https://private-ppa.launchpad.net trusty/main Translation-en_US
Hit http://us.archive.ubuntu.com trusty-updates/main amd64 Packages 
Hit http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages
Hit http://ppa.launchpad.net trusty/main Sources                   
Ign https://private-ppa.launchpad.net trusty/main Translation-en   
Hit http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages
Hit http://ppa.launchpad.net trusty/main Translation-en           
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en       
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
Err http://ppa.launchpad.net trusty/main Sources                               
  404  Not Found
Err http://ppa.launchpad.net trusty/main amd64 Packages                        
  404  Not Found
Err http://ppa.launchpad.net trusty/main i386 Packages                         
  404  Not Found
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Fetched 7,542 B in 8s (935 B/s)                                                
W: GPG error: http://repository.spotify.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 082CCEDF94558F59
W: Failed to fetch http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/trusty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used 
```

```
peter@TosTec-Ubuntu-14:~$ sudo apt-get update
Get:1 http://repository.spotify.com stable InRelease [2,954 B]
Ign http://dl.google.com stable InRelease                                      
Ign http://repository.spotify.com stable InRelease                             
Ign http://repository.spotify.com stable/non-free amd64 Packages/DiffIndex     
Hit http://dl.google.com stable Release.gpg                                    
Ign http://repository.spotify.com stable/non-free i386 Packages/DiffIndex      
Hit http://dl.google.com stable Release                                        
Hit http://dl.google.com stable/main amd64 Packages                            
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://us.archive.ubuntu.com trusty InRelease                              
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://security.ubuntu.com trusty-security Release.gpg                     
Ign http://us.archive.ubuntu.com trusty-updates InRelease                      
Ign http://archive.canonical.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://repository.spotify.com stable/non-free amd64 Packages               
Hit http://security.ubuntu.com trusty-security Release                         
Ign http://us.archive.ubuntu.com trusty-backports InRelease                    
Hit http://repository.spotify.com stable/non-free i386 Packages                
Ign http://repository.spotify.com stable/non-free Translation-en_US            
Ign http://repository.spotify.com stable/non-free Translation-en               
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://security.ubuntu.com trusty-security/main Sources                    
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://archive.canonical.com trusty Release.gpg                            
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty-updates Release.gpg                    
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg                  
Hit http://security.ubuntu.com trusty-security/universe Sources                
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://archive.canonical.com trusty Release                                
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Hit http://us.archive.ubuntu.com trusty-updates Release                        
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://extras.ubuntu.com trusty/main Sources                               
Ign http://ppa.launchpad.net trusty Release.gpg                                
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://us.archive.ubuntu.com trusty-backports Release                      
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Ign https://private-ppa.launchpad.net trusty InRelease                         
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit https://private-ppa.launchpad.net trusty Release.gpg                       
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Get:2 http://archive.canonical.com trusty/partner Translation-en [4,588 B]     
Ign http://ppa.launchpad.net trusty Release                                    
Hit https://private-ppa.launchpad.net trusty Release                           
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Hit http://ppa.launchpad.net trusty Release                                    
Hit https://private-ppa.launchpad.net trusty/main amd64 Packages               
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit https://private-ppa.launchpad.net trusty/main i386 Packages                
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en  
Ign http://extras.ubuntu.com trusty/main Translation-en_US         
Hit http://ppa.launchpad.net trusty/main Sources                   
Hit http://us.archive.ubuntu.com trusty/universe Translation-en    
Ign http://extras.ubuntu.com trusty/main Translation-en            
Hit http://ppa.launchpad.net trusty/main amd64 Packages            
Hit http://us.archive.ubuntu.com trusty-updates/main Sources       
Hit http://us.archive.ubuntu.com trusty-updates/restricted Sources
Hit http://ppa.launchpad.net trusty/main i386 Packages                    
Hit http://us.archive.ubuntu.com trusty-updates/universe Sources          
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Sources  
Hit http://ppa.launchpad.net trusty/main Translation-en
Ign https://private-ppa.launchpad.net trusty/main Translation-en_US
Hit http://us.archive.ubuntu.com trusty-updates/main amd64 Packages 
Hit http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages
Hit http://ppa.launchpad.net trusty/main Sources                   
Ign https://private-ppa.launchpad.net trusty/main Translation-en   
Hit http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages
Hit http://ppa.launchpad.net trusty/main Translation-en           
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en       
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
Err http://ppa.launchpad.net trusty/main Sources                               
  404  Not Found
Err http://ppa.launchpad.net trusty/main amd64 Packages                        
  404  Not Found
Err http://ppa.launchpad.net trusty/main i386 Packages                         
  404  Not Found
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Fetched 7,542 B in 8s (935 B/s)                                                
W: GPG error: http://repository.spotify.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 082CCEDF94558F59
W: Failed to fetch http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/trusty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used 

```

---

### Post by v3.xx on 2015-05-15
Start by removing or disabling the 404 PPAs.  No trusty package.

[http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/)

Correct the GPG Error.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=gpg+error+no_pubkey&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=gpg+error+no_pubkey&sa=Search&cof=FORID:9)

I like this fix (post #11)

[http://ubuntuforums.org/showthread.php?t=1869890&p=11396851&viewfull=1#post11396851](http://ubuntuforums.org/showthread.php?t=1869890&p=11396851&viewfull=1#post11396851)

Then run another update

---

### Post by kindafunnylookin on 2015-05-15
Still getting the same message from the Software Center.

---

### Post by Bashing-om on 2015-05-15
kindafunnylookin; Hello:

Passing by here and I note that :
[http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/)
Has no index for 'trusty' .
Disable the 'gwibber' PPA(s) and now see what results:
```

sudo apt-get update
sudo apt-get upgrade

```

Then maybe consider the advise given:
[https://answers.launchpad.net/ubuntu/+question/247843](https://answers.launchpad.net/ubuntu/+question/247843)
-------------------------
ninja'd by v3.xx :)

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by kindafunnylookin on 2015-05-15
Disregard my last post please.
Thank you for your answer but I'm afraid it;s way to advanced for me, I do not understand enough to see what your instructions mean. Perhaps at this time I'm better off doing a whole new installation.

---

### Post by v3.xx on 2015-05-15
Hay Bashing

Stick around :D

---

### Post by v3.xx on 2015-05-15
> Perhaps at this time I'm better off doing a whole new installation. 
If you wish.  This is a upgrade from 12.04?  A fresh install is the preferred method.  Could save you some other headache down the road.

---

### Post by Bashing-om on 2015-05-15
v3.xx; Hey friend;

> **v3.xx said:**
> Hay Bashing

Stick around :D

[INDENT][INDENT]in for a penny
[INDENT][INDENT][INDENT]in for a pound[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-05-15
kindafunnylookin;

> **kindafunnylookin said:**
> Disregard my last post please.
Thank you for your answer but I'm afraid it;s way to advanced for me, I do not understand enough to see what your instructions mean. [color=blue]Perhaps at this time I'm better off doing a whole new installation.[/color]

Naw, we get into our teaching mode and we work to get you up to speed.
Small things, but one of them at the time.
Where are we loosing you at ?

[INDENT][INDENT]none of us were born knowing
[/INDENT][/INDENT]

---

### Post by v3.xx on 2015-05-15
> we get into our teaching mode and we work to get you up to speed.
We can do this :)

---

### Post by mc4man on 2015-05-15
You can remove a ppa similar to how they can be added, ex. for here
```
sudo add-apt-repository -r ppa:gwibber-daily/ppa
```
then a sudo apt-get update

---

### Post by Bashing-om on 2015-05-15
@mc4man; Me curious ;

in your opinion, what would result if the 'gwibber'  were "ppa-purge" ? As 'gwibber' is no longer maintained and has been replaced by 'friends-app' ; is the package manager smart enough to make the translation ?

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by mc4man on 2015-05-15
> **Bashing-om said:**
> @mc4man; Me curious ;

in your opinion, what would result if the 'gwibber'  were "ppa-purge" ? As 'gwibber' is no longer maintained and has been replaced by 'friends-app' ; is the package manager smart enough to make the translation ?

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]
Well if one had installed packages from a ppa & then wanted to purge using ppa-purge you'd want the ppa enabled to run ppa-purge (ppa-purge would disable the ppa as part of it's process
In this case I believe the intent is to just remove the ppa from sources.

As far as whether a package manager knows (is smart enough) whether package 'b' is the replacement for package 'a',  that's up to whoever produced package 'b' to add a Replaces:  & or Conflicts: or in some cases a Provides: to package 'b's control file.

---

### Post by kindafunnylookin on 2015-05-15
kindafunnylookin; Hello:

Passing by here and I note that :
[http://ppa.launchpad.net/gwibber-dai.../ubuntu/dists/]("http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/")
Has no index for 'trusty' .
Disable the 'gwibber' PPA(s) and now see what results:
 	Code:

 	sudo apt-get update
sudo apt-get upgrade 
Then maybe consider the advise given:
[https://answers.launchpad.net/ubuntu/+question/247843](https://answers.launchpad.net/ubuntu/+question/247843)


Bashing-om
what do you mean by.....Disable the 'gwibber' PPA(s)....... and how to do it please.

---

### Post by Bashing-om on 2015-05-15
mc4man; Thanks:

Good info to keep in mind.

In this case I do stand in correction:
```

apt-cache show gwibber

```

Yepper, it is available in 14.04's repo .. why I guess that PPA is no longer supported !
```

Version: 3.7.0bzr13.04.05-0ubuntu1
Depends: friends-app
Filename: pool/universe/g/gwibber/gwibber_3.7.0bzr13.04.05-0ubuntu1_all.deb

```

In this instance rather than "just remove the ppa from sources" maybe kindafunnylookin is better served to revert the PPA package  to what is available in the repository ?


[INDENT][INDENT]maybe a good thought ?
[/INDENT][/INDENT]

---

### Post by v3.xx on 2015-05-15
PPA Purge should be smart enough to do that.  Could also use y-ppa-manager, it has a gui.

---

### Post by v3.xx on 2015-05-15
Got to go, good luck

---

### Post by Bashing-om on 2015-05-15
@kindafunnylookin; Hey, hey

> 
Bashing-om
what do you mean by.....Disable the 'gwibber' PPA(s)....... and how to do it please.


I am making more out if this than it originally was. Please bear with us while we determine what is in "your best interest".
A direct response is just to activate "software sources" from within the "Software Settings" utility and uncheck the box for 'gwibber'.

If you want to continue to use 'gwibber' then we do alter our thought process to make that happen. 
So, do we remove it, or restore the application ?

[INDENT][INDENT]what to do, oh what to do
[/INDENT][/INDENT]

---

### Post by kindafunnylookin on 2015-05-16
I will wait a few hours to see if anyone can help me out here, if I hear nothing then I will do a re-install.
Thanks to those of you who gave it a shot.

---

### Post by bapoumba on 2015-05-16
Please post the output to :
```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
```

---

### Post by kindafunnylookin on 2015-05-16
```
peter@TosTec-Ubuntu-14:~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main restricted
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
    50    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
    51    deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
    56    deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
    57    ##deb [http://ubuntu.p2-next.org/trusty](http://ubuntu.p2-next.org/trusty) main
    58    ## deb-src [http://ubuntu.p2-next.org/trusty](http://ubuntu.p2-next.org/trusty) main
    59    
    60    deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
```
```
peter@TosTec-Ubuntu-14:~$ ls -la /etc/apt/sources.list.d
total 40
drwxr-xr-x 2 root root 4096 Mar  2 12:44 .
drwxr-xr-x 6 root root 4096 May 15 11:31 ..
-rw-r--r-- 1 root root  175 May 15 18:32 google-earth.list
-rw-r--r-- 1 root root  175 May 15 18:32 google-earth.list.save
-rw-r--r-- 1 root root    0 May 15 18:32 gwibber-daily-ppa-trusty.list
-rw-r--r-- 1 root root    0 May 15 18:32 gwibber-daily-ppa-trusty.list.save
-rw-r--r-- 1 root root  163 May 15 18:32 private-ppa.launchpad.net_commercial-ppa-uploaders_mindfulclock_ubuntu.list
-rw-r--r-- 1 root root  163 May 15 18:32 private-ppa.launchpad.net_commercial-ppa-uploaders_mindfulclock_ubuntu.list.save
-rw-r--r-- 1 root root  138 May 15 18:32 skunk-pepper-flash-trusty.list
-rw-r--r-- 1 root root  138 May 15 18:32 skunk-pepper-flash-trusty.list.save
-rw-r--r-- 1 root root  124 May 15 18:32 venerix-pkg-trusty.list
-rw-r--r-- 1 root root  124 May 15 18:32 venerix-pkg-trusty.list.save
```
```
peter@TosTec-Ubuntu-14:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/google-earth.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable main

==> /etc/apt/sources.list.d/google-earth.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable main

==> /etc/apt/sources.list.d/gwibber-daily-ppa-trusty.list <==

==> /etc/apt/sources.list.d/gwibber-daily-ppa-trusty.list.save <==

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_mindfulclock_ubuntu.list <==
deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/mindfulclock/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/mindfulclock/ubuntu) trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_mindfulclock_ubuntu.list.save <==
deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/mindfulclock/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/mindfulclock/ubuntu) trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf

==> /etc/apt/sources.list.d/skunk-pepper-flash-trusty.list <==
deb [http://ppa.launchpad.net/skunk/pepper-flash/ubuntu](http://ppa.launchpad.net/skunk/pepper-flash/ubuntu) trusty main
deb-src [http://ppa.launchpad.net/skunk/pepper-flash/ubuntu](http://ppa.launchpad.net/skunk/pepper-flash/ubuntu) trusty main

==> /etc/apt/sources.list.d/skunk-pepper-flash-trusty.list.save <==
deb [http://ppa.launchpad.net/skunk/pepper-flash/ubuntu](http://ppa.launchpad.net/skunk/pepper-flash/ubuntu) trusty main
deb-src [http://ppa.launchpad.net/skunk/pepper-flash/ubuntu](http://ppa.launchpad.net/skunk/pepper-flash/ubuntu) trusty main

==> /etc/apt/sources.list.d/venerix-pkg-trusty.list <==
deb [http://ppa.launchpad.net/venerix/pkg/ubuntu](http://ppa.launchpad.net/venerix/pkg/ubuntu) trusty main
deb-src [http://ppa.launchpad.net/venerix/pkg/ubuntu](http://ppa.launchpad.net/venerix/pkg/ubuntu) trusty main

==> /etc/apt/sources.list.d/venerix-pkg-trusty.list.save <==
deb [http://ppa.launchpad.net/venerix/pkg/ubuntu](http://ppa.launchpad.net/venerix/pkg/ubuntu) trusty main
deb-src [http://ppa.launchpad.net/venerix/pkg/ubuntu](http://ppa.launchpad.net/venerix/pkg/ubuntu) trusty main
peter@TosTec-Ubuntu-14:~$
```

---

### Post by Bashing-om on 2015-05-16
kindafunnylookin; Hey ;

I am back on.
I do apologize if my efforts have confused you, or this issue. It is a simple one .
Anything that you do not understand, please ask for clarification on the why and how as to what we are doing.

> **kindafunnylookin said:**
> I will wait a few hours to see if anyone can help me out here, if I hear nothing then I will do a re-install.
Thanks to those of you who gave it a shot.

Huh ? (RE-)install, I see no need to take that nuclear approach. Presently you look to be in good shape.
verify the system status with terminal commands:
```

sudo apt-get update
sudo apt-get upgrade

```
I do expect these to run clean, and now the only question remaining then is if you want to install 'gwibber' .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by kindafunnylookin on 2015-05-16
```
peter@TosTec-Ubuntu-14:~$ sudo apt-get update
[sudo] password for peter: 
Get:1 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease [2,954 B]                 
Ign [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                             
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free amd64 Packages/DiffIndex     
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free i386 Packages/DiffIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                              
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg                     
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release                         
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free amd64 Packages               
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free i386 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty InRelease                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages       
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                 
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages         
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty Release.gpg                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty Release                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages        
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main amd64 Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main i386 Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources                   
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
Fetched 2,954 B in 11s (256 B/s)                                               
Reading package lists... Done
W: GPG error: [http://repository.spotify.com](http://repository.spotify.com) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 082CCEDF94558F59


peter@TosTec-Ubuntu-14:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-signed-image-3.13.0-49-generic : Depends: linux-image-3.13.0-49-generic (= 3.13.0-49.83) but 3.13.0-49.81 is installed
E: Unmet dependencies. Try using -f.
peter@TosTec-Ubuntu-14:~$
```

---

### Post by kindafunnylookin on 2015-05-16
```
peter@TosTec-Ubuntu-14:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-3.13.0-49-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following packages will be upgraded:
  linux-image-3.13.0-49-generic
1 upgraded, 0 newly installed, 0 to remove and 173 not upgraded.
8 not fully installed or removed.
Need to get 0 B/15.1 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 352806 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-49-generic_3.13.0-49.83_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-49-generic (3.13.0-49.83) over (3.13.0-49.81) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-49-generic_3.13.0-49.83_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-3.13.0-49-generic' to '/boot/vmlinuz-3.13.0-49-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-49-generic_3.13.0-49.83_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
peter@TosTec-Ubuntu-14:~$
```

---

### Post by Bashing-om on 2015-05-16
kindafunnylookin; Well; OK,

Not as I had hoped for, but we deal with it.

For the 1st - spotify - not holding the key; execute terminal command:
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 082CCEDF94558F59

```
to import the signing key.

For the linux-signed-image dependency issue; let's do some Prior Prudent Planning, see what we have to work with and to work toward:
What kernel is presently booted ?
```

uname -a

```
What kernels are presently installed ?
```

dpkg -l | grep linux-

```
Do we have the corresponding source code ?
```

ls -al /usr/src

```
Make sure we have the operating headroom:
```

df -h
df -i

```

Once these are known we try and remove the old kernels. In this endeavor see what hints the package manager provides; use these guides as to how to proceed.
-------------------
Please provide the outputs here Between Code Tags:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

So much easier to read when formatted .

EDIT: We do not have the operating headroom.
> 
failed to write (No space left on device)


Provide the above and we proceed to  fix .

[INDENT][INDENT]it is what it is
[/INDENT][/INDENT]

---

### Post by kindafunnylookin on 2015-05-16
OK, here we go:
[HTML]peter@TosTec-Ubuntu-14:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 082CCEDF94558F59
[sudo] password for peter: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --homedir /tmp/tmp.FpYFaryrA4 --no-auto-check-trustdb --trust-model always --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyring /etc/apt/trusted.gpg.d/gwibber-daily-ppa.gpg --keyring /etc/apt/trusted.gpg.d/skunk-pepper-flash.gpg --keyring /etc/apt/trusted.gpg.d/venerix-pkg.gpg --keyserver keyserver.ubuntu.com --recv-keys 082CCEDF94558F59
gpg: requesting key 94558F59 from hkp server keyserver.ubuntu.com
gpg: key 94558F59: "Spotify Public Repository Signing Key <operations@spotify.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
peter@TosTec-Ubuntu-14:~$ 
[/HTML]

[HTML]peter@TosTec-Ubuntu-14:~$ uname -a
Linux TosTec-Ubuntu-14 3.13.0-48-generic #80-Ubuntu SMP Thu Mar 12 11:16:15 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
peter@TosTec-Ubuntu-14:~$ 

[/HTML]
[HTML]peter@TosTec-Ubuntu-14:~$ dpkg -l | grep linux-
ii  linux-firmware                                        1.127.11                                            all          Firmware for Linux kernel drivers
iU  linux-generic                                         3.13.0.49.56                                        amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-43                               3.13.0-43.72                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-43-generic                       3.13.0-43.72                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-44                               3.13.0-44.73                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-44-generic                       3.13.0-44.73                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-45                               3.13.0-45.74                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-45-generic                       3.13.0-45.74                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-46                               3.13.0-46.79                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic                       3.13.0-46.79                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-48                               3.13.0-48.80                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-48-generic                       3.13.0-48.80                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-49                               3.13.0-49.81                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic                       3.13.0-49.81                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.49.56                                        amd64        Generic Linux kernel headers
rc  linux-image-3.13.0-32-generic                         3.13.0-32.57                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-40-generic                         3.13.0-40.69                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-43-generic                         3.13.0-43.72                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-44-generic                         3.13.0-44.73                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-45-generic                         3.13.0-45.74                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-46-generic                         3.13.0-46.79                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-48-generic                         3.13.0-48.80                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-49-generic                         3.13.0-49.81                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-32-generic                   3.13.0-32.57                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-40-generic                   3.13.0-40.69                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-43-generic                   3.13.0-43.72                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-44-generic                   3.13.0-44.73                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic                   3.13.0-45.74                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic                   3.13.0-46.79                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iF  linux-image-extra-3.13.0-48-generic                   3.13.0-48.80                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iF  linux-image-extra-3.13.0-49-generic                   3.13.0-49.83                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-generic                                   3.13.0.49.56                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-49.81                                        amd64        Linux Kernel Headers for development
iU  linux-signed-generic                                  3.13.0.49.56                                        amd64        Complete Signed Generic Linux kernel and headers
rc  linux-signed-image-3.13.0-40-generic                  3.13.0-40.69                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-43-generic                  3.13.0-43.72                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-44-generic                  3.13.0-44.73                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-45-generic                  3.13.0-45.74                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-46-generic                  3.13.0-46.79                                        amd64        Signed kernel image generic
iU  linux-signed-image-3.13.0-48-generic                  3.13.0-48.80                                        amd64        Signed kernel image generic
iU  linux-signed-image-3.13.0-49-generic                  3.13.0-49.83                                        amd64        Signed kernel image generic
iU  linux-signed-image-generic                            3.13.0.49.56                                        amd64        Signed Generic Linux kernel image
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
peter@TosTec-Ubuntu-14:~$ dpkg -l | grep linux-

[/HTML]
[HTML]peter@TosTec-Ubuntu-14:~$ ls -al /usr/src
total 56
drwxr-xr-x 14 root root 4096 Apr 10 08:20 .
drwxr-xr-x 11 root root 4096 Feb 13 08:20 ..
drwxr-xr-x 24 root root 4096 Dec 15 10:56 linux-headers-3.13.0-43
drwxr-xr-x  7 root root 4096 Dec 15 10:56 linux-headers-3.13.0-43-generic
drwxr-xr-x 24 root root 4096 Jan 21 14:54 linux-headers-3.13.0-44
drwxr-xr-x  7 root root 4096 Jan 21 14:54 linux-headers-3.13.0-44-generic
drwxr-xr-x 24 root root 4096 Jan 31 13:41 linux-headers-3.13.0-45
drwxr-xr-x  7 root root 4096 Jan 31 13:41 linux-headers-3.13.0-45-generic
drwxr-xr-x 24 root root 4096 Mar 12 20:47 linux-headers-3.13.0-46
drwxr-xr-x  7 root root 4096 Mar 12 20:48 linux-headers-3.13.0-46-generic
drwxr-xr-x 24 root root 4096 Apr  7 17:45 linux-headers-3.13.0-48
drwxr-xr-x  7 root root 4096 Apr  7 17:45 linux-headers-3.13.0-48-generic
drwxr-xr-x 24 root root 4096 Apr 10 08:20 linux-headers-3.13.0-49
drwxr-xr-x  7 root root 4096 Apr 10 08:20 linux-headers-3.13.0-49-generic
peter@TosTec-Ubuntu-14:~$ 

[/HTML]
[HTML]peter@TosTec-Ubuntu-14:~$ df -i
Filesystem                    Inodes  IUsed    IFree IUse% Mounted on
/dev/mapper/ubuntu--vg-root 30220288 409290 29810998    2% /
none                          495163      2   495161    1% /sys/fs/cgroup
udev                          491232    523   490709    1% /dev
tmpfs                         495163    578   494585    1% /run
none                          495163      4   495159    1% /run/lock
none                          495163     10   495153    1% /run/shm
none                          495163     24   495139    1% /run/user
/dev/sda2                      62496    320    62176    1% /boot
/dev/sda1                          0      0        0     - /boot/efi
peter@TosTec-Ubuntu-14:~$ 

[/HTML]
[HTML]peter@TosTec-Ubuntu-14:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  454G   39G  392G  10% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         1.9G  4.0K  1.9G   1% /dev
tmpfs                        387M  1.3M  386M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         1.9G  144K  1.9G   1% /run/shm
none                         100M   28K  100M   1% /run/user
/dev/sda2                    237M  234M     0 100% /boot
/dev/  3.4M  508M   1% /boot/efi
peter@TosTec-Ubuntu-14:~$ 

[/HTML]

Hope I have done this properly.

---

### Post by Bashing-om on 2015-05-16
kindafunnylookin; Hey, Hey

A rather small /boot partition (to support LVM) and it is full of old kernels.
As we have:
> 
/dev/sda2                    237M  234M     0 100% /boot

showing /boot at 100% capacity, we may have no operating headroom at all; but. let's try the easy way to remove the old kernels before we have to get down and dirty ( we can do that !).

What results:
```

sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove

```
This has only a very small chance of running, but worth a shot.

[INDENT][INDENT]maybe YES
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kindafunnylookin on 2015-05-16
[HTML]   

                                                                                                                                                                                                                                                         [HTML]peter@TosTec-Ubuntu-14:~$ sudo apt-get autoclean
[sudo] password for peter: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done


[/HTML]
[html]
peter@TosTec-Ubuntu-14:~$ sudo apt-get clean
peter@TosTec-Ubuntu-14:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-signed-image-3.13.0-49-generic : Depends: linux-image-3.13.0-49-generic (= 3.13.0-49.83) but 3.13.0-49.81 is installed
E: Unmet dependencies. Try using -f.
peter@TosTec-Ubuntu-14:~$ ^C
[/HTML] 

[HTML]peter@TosTec-Ubuntu-14:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
peter@TosTec-Ubuntu-14:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-3.13.0-49-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following packages will be upgraded:
  linux-image-3.13.0-49-generic
1 upgraded, 0 newly installed, 0 to remove and 173 not upgraded.
8 not fully installed or removed.
Need to get 15.1 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-3.13.0-49-generic amd64 3.13.0-49.83 [15.1 MB]
Fetched 15.1 MB in 5min 42s (44.2 kB/s)                                        
(Reading database ... 352806 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-49-generic_3.13.0-49.83_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-49-generic (3.13.0-49.83) over (3.13.0-49.81) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-49-generic_3.13.0-49.83_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-3.13.0-49-generic' to '/boot/vmlinuz-3.13.0-49-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-49-generic_3.13.0-49.83_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
peter@TosTec-Ubuntu-14:~$ [/HTML]

Just  tried and still cannot download software. I will have to deal with the full partition next, there is plenty of room on the HD  500GIB

---

### Post by Bashing-om on 2015-05-16
kindafunnylookin; Yeah;

Not at all surprised.
The thing is not the space at large on the hard drive, it is the lack of space in /boot.
Let's take this approach, see if the package manager will allow us:
```

sudo dpkg -P linux-image-3.13.0-32-generic
sudo dpkg -P linux-image-extra3.13.0-32-generic

```

What we are working toward is to address:
> 
iU  linux-generic 

where the 'U' in 'iU' indicates a problem, and as it is linux-generic .. well we have a problem. We are going to have to find a way to get it installed.

Here :
> 
rc  linux-image-extra-3.13.0-32-generic

the 'rc' says the package is (R)emoved but (C)onfig files remain. Let's see what dpkg has to advise. now 'rc' in and of it's self is not a bad thing. I expect more 'rc' files to exist when we get to removing kernels for real. We will deal with them when we know more.

If purging what might remain of the -32 kernel goes well, we see what results when we tackle the fully installed kernels. Presently I am doing all we can to remain within the realm of the package manager and let the package manager do it's job. Else, it can get real dirty.

[INDENT][INDENT]it's a dirty job
[INDENT][INDENT][INDENT]but somebody has got to do it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kindafunnylookin on 2015-05-17
[HTML]peter@TosTec-Ubuntu-14:~$ sudo dpkg -P linux-image-3.13.0-32-generic
[sudo] password for peter: 
(Reading database ... 352805 files and directories currently installed.)
Removing linux-image-3.13.0-32-generic (3.13.0-32.57) ...
Purging configuration files for linux-image-3.13.0-32-generic (3.13.0-32.57) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]

[/HTML]
[HTML]peter@TosTec-Ubuntu-14:~$ sudo dpkg -P linux-image-extra3.13.0-32-generic
dpkg: warning: ignoring request to remove linux-image-extra3.13.0-32-generic which isn't installed
peter@TosTec-Ubuntu-14:~$ 

[/HTML]

Once again Im not too sure about where we stand now. What I am sure of is that I'm grateful that you have stuck with me thus far.

---

### Post by bapoumba on 2015-05-17
Several things.

**First**, from post #30 :  ```
cannot copy extracted data for './boot/vmlinuz-3.13.0-49-generic' to '/boot/vmlinuz-3.13.0-49-generic.dpkg-new': failed to write (No space left on device)
```
You need to clear some space.
To verify /boot is full indeed :
```
df -h
```
To see which kernels you have installed :
```
dpkg --list | grep linux-image
```
Best is to keep the working kernel and the previous working one when clearing space. You can have a look here for scripts : [http://ubuntuforums.org/showthread.php?t=1658648](http://ubuntuforums.org/showthread.php?t=1658648). The one I used long time ago is from CharlesA, post #35. Not used that for some time as I do my house cleaning on a regular basis now :)

**Second**.
Some f your repositories I cannot reach in a browser :
[http://ubuntu.p2-next.org/trusty](http://ubuntu.p2-next.org/trusty)
[http://repository.spotify.com/](http://repository.spotify.com/)
and they should not be in your sources.list anyway.

[https://dl.google.com/linux/earth/deb/](https://dl.google.com/linux/earth/deb/) > 404
skunk and venerix are duplicated (not a problem, but one is enough), the private ppa needs authentication.

So first you need to make some room where needed and second you need to straighten up your repositories and ppas. Do you need all the extra repositories ?

---

### Post by Bashing-om on 2015-05-17
kindafunnylookin; Good morning,

AND back to it;
See bapoumba's posting above .

As advised the package manager will give us hints, and guidance as to what we need to do.
Now there is this hint:
> 
The link /initrd.img is a damaged link
Removing symbolic link initrd.img

So, let us take a look at what is presently:
```

ls -al /

```
which will show the files present in the directory '/' and how booting is controlled.

I anticipate removing old kernels to gain space, then we MUST address the warning:
> 
you may need to re-run your boot loader[grub]


And finally, once more, address the sources.list files .

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by kindafunnylookin on 2015-05-17
[HTML]
peter@TosTec-Ubuntu-14:~$ 
peter@TosTec-Ubuntu-14:~$ 
peter@TosTec-Ubuntu-14:~$ sudo dpkg -P linux-image-3.13.0-32-generic
[sudo] password for peter: 
(Reading database ... 352805 files and directories currently installed.)
Removing linux-image-3.13.0-32-generic (3.13.0-32.57) ...
Purging configuration files for linux-image-3.13.0-32-generic (3.13.0-32.57) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub][/HTML]


[HTML]peter@TosTec-Ubuntu-14:~$ sudo dpkg -P linux-image-extra3.13.0-32-generic
dpkg: warning: ignoring request to remove linux-image-extra3.13.0-32-generic which isn't installed
peter@TosTec-Ubuntu-14:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  454G   40G  392G  10% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         1.9G  4.0K  1.9G   1% /dev
tmpfs                        387M  1.3M  386M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         1.9G  144K  1.9G   1% /run/shm
none                         100M   28K  100M   1% /run/user
/dev/sda2                    237M  234M     0 100% /boot
/dev/sda1                    511M  3.4M  508M   1% /boot/efi[/HTML]

[HTML]peter@TosTec-Ubuntu-14:~$ dpkg --list | grep linux-image
rc   linux-image-3.13.0-40-generic                          3.13.0-40.69                                        amd64        Linux  kernel image for version 3.13.0 on 64 bit x86 SMP
ii   linux-image-3.13.0-43-generic                          3.13.0-43.72                                        amd64        Linux  kernel image for version 3.13.0 on 64 bit x86 SMP
ii   linux-image-3.13.0-44-generic                          3.13.0-44.73                                        amd64        Linux  kernel image for version 3.13.0 on 64 bit x86 SMP
ii   linux-image-3.13.0-45-generic                          3.13.0-45.74                                        amd64        Linux  kernel image for version 3.13.0 on 64 bit x86 SMP
ii   linux-image-3.13.0-46-generic                          3.13.0-46.79                                        amd64        Linux  kernel image for version 3.13.0 on 64 bit x86 SMP
ii   linux-image-3.13.0-48-generic                          3.13.0-48.80                                        amd64        Linux  kernel image for version 3.13.0 on 64 bit x86 SMP
ii   linux-image-3.13.0-49-generic                          3.13.0-49.81                                        amd64        Linux  kernel image for version 3.13.0 on 64 bit x86 SMP
rc   linux-image-extra-3.13.0-32-generic                    3.13.0-32.57                                        amd64        Linux  kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc   linux-image-extra-3.13.0-40-generic                    3.13.0-40.69                                        amd64        Linux  kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii   linux-image-extra-3.13.0-43-generic                    3.13.0-43.72                                        amd64        Linux  kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii   linux-image-extra-3.13.0-44-generic                    3.13.0-44.73                                        amd64        Linux  kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii   linux-image-extra-3.13.0-45-generic                    3.13.0-45.74                                        amd64        Linux  kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii   linux-image-extra-3.13.0-46-generic                    3.13.0-46.79                                        amd64        Linux  kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iF   linux-image-extra-3.13.0-48-generic                    3.13.0-48.80                                        amd64        Linux  kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iF   linux-image-extra-3.13.0-49-generic                    3.13.0-49.83                                        amd64        Linux  kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU   linux-image-generic                                    3.13.0.49.56                                        amd64        Generic  Linux kernel image[/HTML]peter@TosTec-Ubuntu-14:~$ sudo dpkg -P linux-image-extra3.13.0-32-generic
dpkg: warning: ignoring request to remove linux-image-extra3.13.0-32-generic which isn't installed[/HTML]

[HTML]peter@TosTec-Ubuntu-14:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  454G   40G  392G  10% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         1.9G  4.0K  1.9G   1% /dev
tmpfs                        387M  1.3M  386M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         1.9G  144K  1.9G   1% /run/shm
none                         100M   28K  100M   1% /run/user
/dev/sda2                    237M  234M     0 100% /boot
/dev/sda1                    511M  3.4M  508M   1% /boot/efi
peter@TosTec-Ubuntu-14:~$ dpkg --list | grep linux-image
rc   linux-image-3.13.0-40-generic                          3.13.0-40.69                                        amd64        Linux  kernel image for version 3.13.0 on 64 bit x86 SMP
ii   linux-image-3.13.0-43-generic                          3.13.0-43.72                                        amd64        Linux  kernel image for version 3.13.0 on 64 bit x86 SMP
ii   linux-image-3.13.0-44-generic                          3.13.0-44.73                                        amd64        Linux  kernel image for version 3.13.0 on 64 bit x86 SMP
ii   linux-image-3.13.0-45-generic                          3.13.0-45.74                                        amd64        Linux  kernel image for version 3.13.0 on 64 bit x86 SMP
ii   linux-image-3.13.0-46-generic                          3.13.0-46.79                                        amd64        Linux  kernel image for version 3.13.0 on 64 bit x86 SMP
ii   linux-image-3.13.0-48-generic                          3.13.0-48.80                                        amd64        Linux  kernel image for version 3.13.0 on 64 bit x86 SMP
ii   linux-image-3.13.0-49-generic                          3.13.0-49.81                                        amd64        Linux  kernel image for version 3.13.0 on 64 bit x86 SMP
rc   linux-image-extra-3.13.0-32-generic                    3.13.0-32.57                                        amd64        Linux  kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc   linux-image-extra-3.13.0-40-generic                    3.13.0-40.69                                        amd64        Linux  kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii   linux-image-extra-3.13.0-43-generic                    3.13.0-43.72                                        amd64        Linux  kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii   linux-image-extra-3.13.0-44-generic                    3.13.0-44.73                                        amd64        Linux  kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii   linux-image-extra-3.13.0-45-generic                    3.13.0-45.74                                        amd64        Linux  kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii   linux-image-extra-3.13.0-46-generic                    3.13.0-46.79                                        amd64        Linux  kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iF   linux-image-extra-3.13.0-48-generic                    3.13.0-48.80                                        amd64        Linux  kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iF   linux-image-extra-3.13.0-49-generic                    3.13.0-49.83                                        amd64        Linux  kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU   linux-image-generic                                    3.13.0.49.56                                        amd64        Generic  Linux kernel image[/HTML]

[HTML]peter@TosTec-Ubuntu-14:~$ dpkg -l 'linux-*' | sed  '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]*  [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge 
[sudo] password for peter: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6-dev : Depends: linux-libc-dev but it is not going to be installed
 linux-headers-generic : Depends: linux-headers-3.13.0-49-generic but it is not going to be installed
 linux-image-extra-3.13.0-49-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed
 linux-signed-image-3.13.0-49-generic  : Depends: linux-image-3.13.0-49-generic (= 3.13.0-49.83) but it is not  going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[/HTML]

[HTML]peter@TosTec-Ubuntu-14:~$ sudo dpkg -P linux-image-3.13.0-32-generic
[sudo] password for peter: 
(Reading database ... 352805 files and directories currently installed.)
Removing linux-image-3.13.0-32-generic (3.13.0-32.57) ...
Purging configuration files for linux-image-3.13.0-32-generic (3.13.0-32.57) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub][/HTML]

[HTML]peter@TosTec-Ubuntu-14:~$ sudo dpkg -P linux-image-extra3.13.0-32-generic
dpkg: warning: ignoring request to remove linux-image-extra3.13.0-32-generic which isn't installed
peter@TosTec-Ubuntu-14:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  454G   40G  392G  10% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         1.9G  4.0K  1.9G   1% /dev
tmpfs                        387M  1.3M  386M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         1.9G  144K  1.9G   1% /run/shm
none                         100M   28K  100M   1% /run/user
/dev/sda2                    237M  234M     0 100% /boot
/dev/sda1                    511M  3.4M  508M   1% /boot/efi
peter@TosTec-Ubuntu-14:~$ dpkg --list | grep linux-image
rc  linux-image-3.13.0-40-generic                         3.13.0-40.69                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-43-generic                         3.13.0-43.72                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-44-generic                         3.13.0-44.73                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-45-generic                         3.13.0-45.74                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-46-generic                         3.13.0-46.79                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-48-generic                         3.13.0-48.80                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-49-generic                         3.13.0-49.81                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-32-generic                   3.13.0-32.57                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-40-generic                   3.13.0-40.69                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-43-generic                   3.13.0-43.72                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-44-generic                   3.13.0-44.73                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic                   3.13.0-45.74                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic                   3.13.0-46.79                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iF  linux-image-extra-3.13.0-48-generic                   3.13.0-48.80                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iF  linux-image-extra-3.13.0-49-generic                   3.13.0-49.83                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-generic                                   3.13.0.49.56                                        amd64        Generic Linux kernel image[/HTML]

[HTML]peter@TosTec-Ubuntu-14:~$ dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge 
[sudo] password for peter: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6-dev : Depends: linux-libc-dev but it is not going to be installed
 linux-headers-generic : Depends: linux-headers-3.13.0-49-generic but it is not going to be installed
 linux-image-extra-3.13.0-49-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.13.0-49-generic but it is not going to be installed
 linux-signed-image-3.13.0-49-generic : Depends: linux-image-3.13.0-49-generic (= 3.13.0-49.83) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[/HTML]

[HTML]peter@TosTec-Ubuntu-14:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
peter@TosTec-Ubuntu-14:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-3.13.0-49-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following packages will be upgraded:
  linux-image-3.13.0-49-generic
1 upgraded, 0 newly installed, 0 to remove and 173 not upgraded.
8 not fully installed or removed.
Need to get 0 B/15.1 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 352806 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-49-generic_3.13.0-49.83_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-49-generic (3.13.0-49.83) over (3.13.0-49.81) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-49-generic_3.13.0-49.83_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-3.13.0-49-generic' to '/boot/vmlinuz-3.13.0-49-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-49-generic_3.13.0-49.83_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
peter@TosTec-Ubuntu-14:~$ 
[/HTML]


Okey, I think that is everything that was asked for.

---

### Post by Bashing-om on 2015-05-17
kindafunnylookin; OK;

We do have the hope that the package manager can and will cope with this:
Try:
```

sudo dpkg -P linux-image-3.13.0-43-generic
sudo dpkg -P linux-image-extra-3.13.0-43-generic
sudo dpkg -P linux-signed-image-3.13.0-43-generic
sudo dpkg -P linux-headers-3.13.0-43
sudo dpkg -P linux-image-3.13.0-43-generic

```
And let's see what happens before delving in deeper .

[INDENT][INDENT]small steps, far between
[INDENT][INDENT][INDENT]but we are getting there
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kindafunnylookin on 2015-05-17
Bashing-om,
just have seen your latest, at same time was called into work for the night. Will Resume as soon as possible
Thanks again

---

### Post by Bashing-om on 2015-05-17
kindafunnylookin; K

We work at your pace.

[INDENT][INDENT]sometimes;
[INDENT][INDENT]life gets in the way
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kindafunnylookin on 2015-05-18
Good morning, the new day brought sucess.

Bapoumba gave me a link to a command posted by Timmer1240 that cleaned out my collection of old kernals in my boot partition, this is how it went:

[HTML]
p { margin-bottom: 0.1in; line-height: 120%; }   peter@TosTec-Ubuntu-14:~$     dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 The following packages were automatically installed and are no longer required:  
   alien at debugedit gir1.2-gtk-2.0 gir1.2-rsvg-2.0 lib32z1  
   libcairo-script-interpreter2 libenca-dev libgmp-dev libgmpxx4ldbl  
   libgnutls-xssl0 libgnutlsxx28 libgpg-error-dev libharfbuzz-dev  
   libharfbuzz-gobject0 libjbig-dev liblua5.1-0 liblzma-dev libp11-kit-dev  
   libpcrecpp0 libpixman-1-dev libreadline-dev libreadline6-dev librpmbuild3  
   librpmsign1 libtasn1-6-dev libtiffxx5 libtinfo-dev libwebp-dev libwebpdemux1  
   libxcomposite-dev libxcursor-dev libxi-dev libxrandr-dev libxrender-dev  
   lsb-security ncurses-term nettle-dev pax rpm x11proto-composite-dev  
   x11proto-randr-dev x11proto-render-dev  
 Use 'apt-get autoremove' to remove them.  
 The following extra packages will be installed:  
   linux-generic linux-headers-3.13.0-52 linux-headers-3.13.0-52-generic  
   linux-headers-generic linux-image-3.13.0-52-generic  
   linux-image-extra-3.13.0-52-generic linux-image-generic linux-signed-generic  
   linux-signed-image-3.13.0-52-generic linux-signed-image-generic  
 Suggested packages:  
   fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools  
 The following packages will be REMOVED:  
   build-essential* g++* g++-4.8* google-earth-stable:i386* libaa1-dev*  
   libass-dev* libatk1.0-dev* libc6-dev* libcaca-dev* libcairo2-dev*  
   libcdio-dev* libdc1394-22-dev* libexpat1-dev* libfontconfig1-dev*  
   libfreetype6-dev* libgcrypt11-dev* libgdk-pixbuf2.0-dev* libglib2.0-dev*  
   libgnutls28-dev* libgtk2.0-dev* libid3tag0-dev* libiso9660-dev* libjpeg-dev*  
   libjpeg-turbo8-dev* libjpeg8-dev* liblircclient-dev* liblua5.1-0-dev* 
   libncurses5-dev* libncursesw5-dev* libnotify-dev* libpango1.0-dev*  
   libpcre3-dev* libpng12-dev* libpulse-dev* librsvg2-dev* libsdl-image1.2-dev*  
   libsdl1.2-dev* libslang2-dev* libsqlite3-dev* libstdc++-4.8-dev*  
   libtiff5-dev* libtool* libtwolame-dev* libvcdinfo-dev* libxft-dev*  
   libzvbi-dev* linux-headers-3.13.0-43-generic* linux-headers-3.13.0-44*  
   linux-headers-3.13.0-44-generic* linux-headers-3.13.0-45*  
   linux-headers-3.13.0-45-generic* linux-headers-3.13.0-46*  
   linux-headers-3.13.0-46-generic* linux-headers-3.13.0-49*  
   linux-headers-3.13.0-49-generic* linux-image-3.13.0-44-generic*  
   linux-image-3.13.0-45-generic* linux-image-3.13.0-46-generic*  
   linux-image-3.13.0-49-generic* linux-image-extra-3.13.0-44-generic*  
   linux-image-extra-3.13.0-45-generic* linux-image-extra-3.13.0-46-generic*  
   linux-image-extra-3.13.0-49-generic* linux-libc-dev*  
   linux-signed-image-3.13.0-44-generic* linux-signed-image-3.13.0-45-generic*  
   linux-signed-image-3.13.0-46-generic* linux-signed-image-3.13.0-49-generic*  
   lsb-core* zlib1g-dev*  
 The following NEW packages will be installed:  
   linux-headers-3.13.0-52 linux-headers-3.13.0-52-generic  
   linux-image-3.13.0-52-generic linux-image-extra-3.13.0-52-generic  
   linux-signed-image-3.13.0-52-generic  
 The following packages will be upgraded:  
   linux-generic linux-headers-generic linux-image-generic linux-signed-generic  
   linux-signed-image-generic  
 5 upgraded, 5 newly installed, 70 to remove and 165 not upgraded.  
 8 not fully installed or removed.  
 Need to get 61.5 MB of archives.  
 After this operation, 1,129 MB disk space will be freed.  
 Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-3.13.0-52-generic amd64 3.13.0-52.86 [15.1 MB]  
 Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-extra-3.13.0-52-generic amd64 3.13.0-52.86 [36.8 MB]  
 Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-signed-image-3.13.0-52-generic amd64 3.13.0-52.86 [4,016 B]  
 Get:4 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-signed-generic amd64 3.13.0.52.59 [1,814 B]  
 Get:5 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-signed-image-generic amd64 3.13.0.52.59 [2,386 B]  
 Get:6 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-3.13.0-52 all 3.13.0-52.86 [8,867 kB]  
 Get:7 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-3.13.0-52-generic amd64 3.13.0-52.86 [695 kB]  
 Get:8 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-generic amd64 3.13.0.52.59 [1,786 B]  
 Get:9 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-generic amd64 3.13.0.52.59 [2,334 B]  
 Get:10 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-generic amd64 3.13.0.52.59 [2,350 B]  
 Fetched 61.5 MB in 47s (1,293 kB/s)                                             
 Selecting previously unselected package linux-image-3.13.0-52-generic.  
 (Reading database ... 347984 files and directories currently installed.)  
 Preparing to unpack .../linux-image-3.13.0-52-generic_3.13.0-52.86_amd64.deb ...  
 Done.  
 Unpacking linux-image-3.13.0-52-generic (3.13.0-52.86) ...  
 Selecting previously unselected package linux-image-extra-3.13.0-52-generic.  
 Preparing to unpack .../linux-image-extra-3.13.0-52-generic_3.13.0-52.86_amd64.deb ...  
 Unpacking linux-image-extra-3.13.0-52-generic (3.13.0-52.86) ...  
 Selecting previously unselected package linux-signed-image-3.13.0-52-generic.  
 Preparing to unpack .../linux-signed-image-3.13.0-52-generic_3.13.0-52.86_amd64.deb ...  
 Unpacking linux-signed-image-3.13.0-52-generic (3.13.0-52.86) ...  
 Preparing to unpack .../linux-signed-generic_3.13.0.52.59_amd64.deb ...  
 Unpacking linux-signed-generic (3.13.0.52.59) over (3.13.0.49.56) ...  
 Preparing to unpack .../linux-signed-image-generic_3.13.0.52.59_amd64.deb ...  
 Unpacking linux-signed-image-generic (3.13.0.52.59) over (3.13.0.49.56) ...  
 Selecting previously unselected package linux-headers-3.13.0-52.  
 Preparing to unpack .../linux-headers-3.13.0-52_3.13.0-52.86_all.deb ...  
 Unpacking linux-headers-3.13.0-52 (3.13.0-52.86) ...  
 Selecting previously unselected package linux-headers-3.13.0-52-generic.  
 Preparing to unpack .../linux-headers-3.13.0-52-generic_3.13.0-52.86_amd64.deb ...  
 Unpacking linux-headers-3.13.0-52-generic (3.13.0-52.86) ...  
 Preparing to unpack .../linux-generic_3.13.0.52.59_amd64.deb ...  
 Unpacking linux-generic (3.13.0.52.59) over (3.13.0.49.56) ...  
 Preparing to unpack .../linux-headers-generic_3.13.0.52.59_amd64.deb ...  
 Unpacking linux-headers-generic (3.13.0.52.59) over (3.13.0.49.56) ...  
 Preparing to unpack .../linux-image-generic_3.13.0.52.59_amd64.deb ...  
 Unpacking linux-image-generic (3.13.0.52.59) over (3.13.0.49.56) ...  
 (Reading database ... 377622 files and directories currently installed.)  
 Removing linux-signed-image-3.13.0-49-generic (3.13.0-49.83) ...  
 Generating grub configuration file ...  
 Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.  
 Found linux image: /boot/vmlinuz-3.13.0-52-generic  
 Found linux image: /boot/vmlinuz-3.13.0-49-generic  
 Found initrd image: /boot/initrd.img-3.13.0-49-generic  
 Found linux image: /boot/vmlinuz-3.13.0-48-generic  
 Found initrd image: /boot/initrd.img-3.13.0-48-generic  
 Found linux image: /boot/vmlinuz-3.13.0-46-generic  
 Found initrd image: /boot/initrd.img-3.13.0-46-generic  
 Found linux image: /boot/vmlinuz-3.13.0-45-generic  
 Found initrd image: /boot/initrd.img-3.13.0-45-generic  
 Found linux image: /boot/vmlinuz-3.13.0-44-generic  
 Found initrd image: /boot/initrd.img-3.13.0-44-generic  
 Adding boot menu entry for EFI firmware configuration  
 done  
 Purging configuration files for linux-signed-image-3.13.0-49-generic (3.13.0-49.83) ...  
 Removing linux-image-extra-3.13.0-49-generic (3.13.0-49.83) ...  
 run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic  
 run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic  
 update-initramfs: Generating /boot/initrd.img-3.13.0-49-generic  
 

 gzip: stdout: No space left on device  
 E: mkinitramfs failure cpio 141 gzip 1  
 update-initramfs: failed for /boot/initrd.img-3.13.0-49-generic with 1.  
 run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1  
 dpkg: error processing package linux-image-extra-3.13.0-49-generic (--purge):  
  subprocess installed post-removal script returned error exit status 1  
 Removing build-essential (11.6ubuntu6) ...  
 Removing g++ (4:4.8.2-1ubuntu6) ...  
 Removing g++-4.8 (4.8.2-19ubuntu1) ...  
 Removing google-earth-stable (7.1.2.2041-r0) ...  
 Purging configuration files for google-earth-stable (7.1.2.2041-r0) ...  
 Removing libaa1-dev (1.4p5-41) ...  
 Removing libass-dev:amd64 (0.10.1-3ubuntu1) ...  

 Removing libgtk2.0-dev (2.24.23-0ubuntu1.2) ...  
 Removing libatk1.0-dev (2.10.0-2ubuntu2) ...  
 Removing libsdl-image1.2-dev:amd64 (1.2.12-5build2) ...  
 Removing libtiff5-dev:amd64 (4.0.3-7ubuntu0.3) ...  
 Removing liblua5.1-0-dev:amd64 (5.1.5-5ubuntu0.1) ...  
 Removing libgcrypt11-dev (1.5.3-2ubuntu4.2) ...  
 Removing libpango1.0-dev (1.36.3-1ubuntu1.1) ...  

 Removing libsdl1.2-dev (1.2.15-8ubuntu1.1) ...  
 Removing libcaca-dev (0.99.beta18-1ubuntu5) ...  
 Removing librsvg2-dev (2.40.2-1) ...  
 Removing libcairo2-dev (1.13.0~20140204-0ubuntu1.1) ...  
 Removing libvcdinfo-dev (0.7.24+dfsg-0.1ubuntu2) ...  
 Removing libiso9660-dev (0.83-4.1ubuntu1) ...  
 Removing libcdio-dev (0.83-4.1ubuntu1) ...  
 Removing libdc1394-22-dev:amd64 (2.2.1-2ubuntu2) ...  
 Removing libxft-dev (2.3.1-2) ...  
 Removing libfontconfig1-dev (2.11.0-0ubuntu4.1) ...  
 Removing libexpat1-dev:amd64 (2.1.0-4ubuntu1) ...  
 Removing libnotify-dev (0.7.6-1ubuntu3) ...  
 Removing libgdk-pixbuf2.0-dev (2.30.7-0ubuntu1) ...  
 Removing libpulse-dev:amd64 (1:4.0-0ubuntu11.1) ...  
 Removing libglib2.0-dev (2.40.2-0ubuntu1) ...  
 Removing libgnutls28-dev:amd64 (3.2.11-2ubuntu1) ...  
 Removing libid3tag0-dev (0.15.1b-10ubuntu1) ...  
 Removing libjpeg-dev:amd64 (8c-2ubuntu8) ...  
 Removing libjpeg8-dev:amd64 (8c-2ubuntu8) ...  
 Removing libjpeg-turbo8-dev:amd64 (1.3.0-0ubuntu2) ...  
 Removing liblircclient-dev (0.9.0-0ubuntu5) ...  
 Removing libncurses5-dev:amd64 (5.9+20140118-1ubuntu1) ...  
 Removing libncursesw5-dev:amd64 (5.9+20140118-1ubuntu1) ...  
 Removing libpcre3-dev:amd64 (1:8.31-2ubuntu2) ...  
 Removing libzvbi-dev:amd64 (0.2.35-2) ...  
 Removing libslang2-dev:amd64 (2.2.4-15ubuntu1) ...  
 Removing libsqlite3-dev:amd64 (3.8.2-1ubuntu2) ...  
 Removing libstdc++-4.8-dev:amd64 (4.8.2-19ubuntu1) ...  
 Removing libtool (2.4.2-1.7ubuntu1) ...  
 Removing libtwolame-dev (0.3.13-1ubuntu1) ...  
 Removing linux-headers-3.13.0-43-generic (3.13.0-43.72) ...  
 dpkg: warning: while removing linux-headers-3.13.0-43-generic, directory '/lib/modules/3.13.0-43-generic' not empty so not removed  
 Removing linux-headers-3.13.0-44-generic (3.13.0-44.73) ...  
 Removing linux-headers-3.13.0-44 (3.13.0-44.73) ...  
 Removing linux-headers-3.13.0-45-generic (3.13.0-45.74) ...  
 Removing linux-headers-3.13.0-45 (3.13.0-45.74) ...  
 Removing linux-headers-3.13.0-46-generic (3.13.0-46.79) ...  
 Removing linux-headers-3.13.0-46 (3.13.0-46.79) ...  
 Removing linux-headers-3.13.0-49-generic (3.13.0-49.81) ...  
 Removing linux-headers-3.13.0-49 (3.13.0-49.81) ...  
 Removing linux-signed-image-3.13.0-44-generic (3.13.0-44.73) ...  
 Generating grub configuration file ...  
 Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.  
 Found linux image: /boot/vmlinuz-3.13.0-52-generic  
 Found linux image: /boot/vmlinuz-3.13.0-49-generic  
 Found initrd image: /boot/initrd.img-3.13.0-49-generic  
 Found linux image: /boot/vmlinuz-3.13.0-48-generic  
 Found initrd image: /boot/initrd.img-3.13.0-48-generic  
 Found linux image: /boot/vmlinuz-3.13.0-46-generic  
 Found initrd image: /boot/initrd.img-3.13.0-46-generic  
 Found linux image: /boot/vmlinuz-3.13.0-45-generic  
 Found initrd image: /boot/initrd.img-3.13.0-45-generic  
 Found linux image: /boot/vmlinuz-3.13.0-44-generic  
 Found initrd image: /boot/initrd.img-3.13.0-44-generic  
 Adding boot menu entry for EFI firmware configuration  
 done  
 Purging configuration files for linux-signed-image-3.13.0-44-generic (3.13.0-44.73) ...  
 Removing linux-image-extra-3.13.0-44-generic (3.13.0-44.73) ...  
 run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-44-generic /boot/vmlinuz-3.13.0-44-generic  
 run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-44-generic /boot/vmlinuz-3.13.0-44-generic  
 update-initramfs: Generating /boot/initrd.img-3.13.0-44-generic  
 

 gzip: stdout: No space left on device  
 E: mkinitramfs failure cpio 141 gzip 1  
 update-initramfs: failed for /boot/initrd.img-3.13.0-44-generic with 1.  
 run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1  
 dpkg: error processing package linux-image-extra-3.13.0-44-generic (--purge):  
  subprocess installed post-removal script returned error exit status 1  
 Removing linux-image-3.13.0-44-generic (3.13.0-44.73) ...  
 Examining /etc/kernel/postrm.d .  
 run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-44-generic /boot/vmlinuz-3.13.0-44-generic  
 update-initramfs: Deleting /boot/initrd.img-3.13.0-44-generic  
 run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-44-generic /boot/vmlinuz-3.13.0-44-generic  
 Generating grub configuration file ...  
 Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.  
 Found linux image: /boot/vmlinuz-3.13.0-52-generic  
 Found linux image: /boot/vmlinuz-3.13.0-49-generic  
 Found initrd image: /boot/initrd.img-3.13.0-49-generic  
 Found linux image: /boot/vmlinuz-3.13.0-48-generic  
 Found initrd image: /boot/initrd.img-3.13.0-48-generic  
 Found linux image: /boot/vmlinuz-3.13.0-46-generic  
 Found initrd image: /boot/initrd.img-3.13.0-46-generic  
 Found linux image: /boot/vmlinuz-3.13.0-45-generic  
 Found initrd image: /boot/initrd.img-3.13.0-45-generic  
 Adding boot menu entry for EFI firmware configuration  
 done  
 Purging configuration files for linux-image-3.13.0-44-generic (3.13.0-44.73) ...  
 Examining /etc/kernel/postrm.d .  
 run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-44-generic /boot/vmlinuz-3.13.0-44-generic  
 run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-44-generic /boot/vmlinuz-3.13.0-44-generic  
 Removing linux-signed-image-3.13.0-45-generic (3.13.0-45.74) ...  
 Generating grub configuration file ...  
 Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.  
 Found linux image: /boot/vmlinuz-3.13.0-52-generic  
 Found linux image: /boot/vmlinuz-3.13.0-49-generic  
 Found initrd image: /boot/initrd.img-3.13.0-49-generic  
 Found linux image: /boot/vmlinuz-3.13.0-48-generic  
 Found initrd image: /boot/initrd.img-3.13.0-48-generic  
 Found linux image: /boot/vmlinuz-3.13.0-46-generic  
 Found initrd image: /boot/initrd.img-3.13.0-46-generic  
 Found linux image: /boot/vmlinuz-3.13.0-45-generic  
 Found initrd image: /boot/initrd.img-3.13.0-45-generic  
 Adding boot menu entry for EFI firmware configuration  
 done  
 Purging configuration files for linux-signed-image-3.13.0-45-generic (3.13.0-45.74) ...  
 Removing linux-image-extra-3.13.0-45-generic (3.13.0-45.74) ...  
 run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic  
 run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic  
 update-initramfs: Generating /boot/initrd.img-3.13.0-45-generic  
 run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic  
 run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic  
 run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic  
 Generating grub configuration file ...  
 Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.  
 Found linux image: /boot/vmlinuz-3.13.0-52-generic  
 Found linux image: /boot/vmlinuz-3.13.0-49-generic  
 Found initrd image: /boot/initrd.img-3.13.0-49-generic  
 Found linux image: /boot/vmlinuz-3.13.0-48-generic  
 Found initrd image: /boot/initrd.img-3.13.0-48-generic  
 Found linux image: /boot/vmlinuz-3.13.0-46-generic  
 Found initrd image: /boot/initrd.img-3.13.0-46-generic  
 Found linux image: /boot/vmlinuz-3.13.0-45-generic  
 Found initrd image: /boot/initrd.img-3.13.0-45-generic  
 Adding boot menu entry for EFI firmware configuration  
 done  
 Purging configuration files for linux-image-extra-3.13.0-45-generic (3.13.0-45.74) ...  
 Removing linux-image-3.13.0-45-generic (3.13.0-45.74) ...  
 Examining /etc/kernel/postrm.d .  
 run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic  
 update-initramfs: Deleting /boot/initrd.img-3.13.0-45-generic  
 run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic  
 Generating grub configuration file ...  
 Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.  
 Found linux image: /boot/vmlinuz-3.13.0-52-generic  
 Found linux image: /boot/vmlinuz-3.13.0-49-generic  
 Found initrd image: /boot/initrd.img-3.13.0-49-generic  
 Found linux image: /boot/vmlinuz-3.13.0-48-generic  
 Found initrd image: /boot/initrd.img-3.13.0-48-generic  
 Found linux image: /boot/vmlinuz-3.13.0-46-generic  
 Found initrd image: /boot/initrd.img-3.13.0-46-generic  
 Adding boot menu entry for EFI firmware configuration  
 done  
 Purging configuration files for linux-image-3.13.0-45-generic (3.13.0-45.74) ...  
 Examining /etc/kernel/postrm.d .  
 run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic  
 run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic  
 Removing linux-signed-image-3.13.0-46-generic (3.13.0-46.79) ...  
 Generating grub configuration file ...  
 Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.  
 Found linux image: /boot/vmlinuz-3.13.0-52-generic  
 Found linux image: /boot/vmlinuz-3.13.0-49-generic  
 Found initrd image: /boot/initrd.img-3.13.0-49-generic  
 Found linux image: /boot/vmlinuz-3.13.0-48-generic  
 Found initrd image: /boot/initrd.img-3.13.0-48-generic  
 Found linux image: /boot/vmlinuz-3.13.0-46-generic  
 Found initrd image: /boot/initrd.img-3.13.0-46-generic  
 Adding boot menu entry for EFI firmware configuration  
 done  
 Purging configuration files for linux-signed-image-3.13.0-46-generic (3.13.0-46.79) ...  
 Removing linux-image-extra-3.13.0-46-generic (3.13.0-46.79) ...  
 run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic  
 run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic  
 update-initramfs: Generating /boot/initrd.img-3.13.0-46-generic  
 run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic  
 run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic  
 run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic  
 Generating grub configuration file ...  
 Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.  
 Found linux image: /boot/vmlinuz-3.13.0-52-generic  
 Found linux image: /boot/vmlinuz-3.13.0-49-generic  
 Found initrd image: /boot/initrd.img-3.13.0-49-generic  
 Found linux image: /boot/vmlinuz-3.13.0-48-generic  
 Found initrd image: /boot/initrd.img-3.13.0-48-generic  
 Found linux image: /boot/vmlinuz-3.13.0-46-generic  
 Found initrd image: /boot/initrd.img-3.13.0-46-generic  
 Adding boot menu entry for EFI firmware configuration  
 done  
 Purging configuration files for linux-image-extra-3.13.0-46-generic (3.13.0-46.79) ...  
 Removing linux-image-3.13.0-46-generic (3.13.0-46.79) ...  
 Examining /etc/kernel/postrm.d .  
 run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic  
 update-initramfs: Deleting /boot/initrd.img-3.13.0-46-generic  
 run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic  
 Generating grub configuration file ...  
 Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.  
 Found linux image: /boot/vmlinuz-3.13.0-52-generic  
 Found linux image: /boot/vmlinuz-3.13.0-49-generic  
 Found initrd image: /boot/initrd.img-3.13.0-49-generic  
 Found linux image: /boot/vmlinuz-3.13.0-48-generic  
 Found initrd image: /boot/initrd.img-3.13.0-48-generic  
 Adding boot menu entry for EFI firmware configuration  
 done  
 Purging configuration files for linux-image-3.13.0-46-generic (3.13.0-46.79) ...  
 Examining /etc/kernel/postrm.d .  
 run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic  
 run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic  
 Removing linux-image-3.13.0-49-generic (3.13.0-49.83) ...  
 Examining /etc/kernel/postrm.d .  
 run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic  
 update-initramfs: Deleting /boot/initrd.img-3.13.0-49-generic  
 run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic  
 Generating grub configuration file ...  
 Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.  
 Found linux image: /boot/vmlinuz-3.13.0-52-generic  
 Found linux image: /boot/vmlinuz-3.13.0-48-generic  
 Found initrd image: /boot/initrd.img-3.13.0-48-generic  
 Adding boot menu entry for EFI firmware configuration  
 done  
 The link /vmlinuz is a damaged link  
 Removing symbolic link vmlinuz  
  you may need to re-run your boot loader[grub]  
 The link /initrd.img is a damaged link  
 Removing symbolic link initrd.img  
  you may need to re-run your boot loader[grub]  
 Purging configuration files for linux-image-3.13.0-49-generic (3.13.0-49.83) ...  
 Examining /etc/kernel/postrm.d .  
 run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic  
 run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-49-generic /boot/vmlinuz-3.13.0-49-generic  
 Removing lsb-core (4.1+Debian11ubuntu6) ...  
 Purging configuration files for lsb-core (4.1+Debian11ubuntu6) ...  
 Removing libfreetype6-dev (2.5.2-1ubuntu2.4) ...  
 Removing libpng12-dev (1.2.50-1ubuntu2) ...  
 Removing zlib1g-dev:amd64 (1:1.2.8.dfsg-1ubuntu1) ...  
 Removing libc6-dev:amd64 (2.19-0ubuntu6.6) ...  
 Removing linux-libc-dev:amd64 (3.13.0-49.81) ...  
 Processing triggers for man-db (2.6.7.1-1ubuntu1) ...  
 Processing triggers for install-info (5.2.0.dfsg.1-2) ...  
 Processing triggers for doc-base (0.10.5) ...  
 Processing 4 removed doc-base files...  
 Registering documents with scrollkeeper...  
 Processing triggers for libglib2.0-0:i386 (2.40.2-0ubuntu1) ...  
 Processing triggers for libglib2.0-0:amd64 (2.40.2-0ubuntu1) ...  
 Errors were encountered while processing:  
  linux-image-extra-3.13.0-49-generic  
  linux-image-extra-3.13.0-44-generic  
 E: Sub-process /usr/bin/dpkg returned an error code (1)  
 peter@TosTec-Ubuntu-14:~$ 
[/HTML]

I then was able to successfully *update* and [I]upgrade.

Thank you all for helping, especially  Bashing-om for sticking with me til the end.

[/I]

---

### Post by Bashing-om on 2015-05-18
kindafunnylookin; Great ...

All's well that ends well .

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]many paths to an end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bapoumba on 2015-05-18
Glad to see you fixed the full /boot partition. Now you need to straighten up your sources.list.

---

