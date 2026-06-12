---
title: "Dosbox install, broken package..7.10"
date: 2007-11-18
forum: General Help
---

### Post by scottsee on 2007-11-18
I went into Packet Manager and updated the Universal to give me Dosbox, when I tried intalling it I recieved the following

```
scott@laptop:~/Files/games$ sudo apt-get install dosbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  dosbox: Depends: libsdl-sound1.2 but it is not going to be installed
E: Broken packages

```

---

### Post by erfahren on 2007-11-18
check your /etc/apt/sources.list
see: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method)

have Software Sources and Synaptic Package Manager closed when you do the apt-get update

after updating try installing dosbox again

---

### Post by scottsee on 2007-11-21
I ran the update described in that how-to and recieved the following.. Should I be concerned??

```
root@laptop:/home/scott# apt-get update
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/main Translation-en_CA           
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_CA     
Get:2 http://us.archive.ubuntu.com gutsy Release.gpg [191B]                    
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_CA                  
Get:3 http://archive.canonical.com gutsy Release.gpg [191B]                    
Ign http://archive.canonical.com gutsy/partner Translation-en_CA               
Get:4 http://packages.medibuntu.org gutsy Release.gpg [189B]                   
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_CA       
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_CA     
Hit http://security.ubuntu.com gutsy-security Release                          
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_CA            
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_CA    
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_CA  
Get:5 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]  
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_CA
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_CA
Hit http://archive.canonical.com gutsy Release                                 
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_CA      
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_CA
Get:6 http://us.archive.ubuntu.com gutsy-backports Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy-backports/main Translation-en_CA
Hit http://security.ubuntu.com gutsy-security/main Packages          
Ign http://us.archive.ubuntu.com gutsy-backports/restricted Translation-en_CA
Ign http://archive.canonical.com gutsy/partner Packages                        
Ign http://packages.medibuntu.org gutsy/free Translation-en_CA                 
Ign http://us.archive.ubuntu.com gutsy-backports/universe Translation-en_CA    
Ign http://us.archive.ubuntu.com gutsy-backports/multiverse Translation-en_CA  
Hit http://us.archive.ubuntu.com gutsy Release                                 
Hit http://us.archive.ubuntu.com gutsy-updates Release                         
Hit http://us.archive.ubuntu.com gutsy-backports Release                       
Hit http://security.ubuntu.com gutsy-security/restricted Packages              
Hit http://security.ubuntu.com gutsy-security/main Sources                     
Hit http://security.ubuntu.com gutsy-security/restricted Sources               
Ign http://archive.canonical.com gutsy/partner Sources                         
Ign http://packages.medibuntu.org gutsy/non-free Translation-en_CA             
Hit http://us.archive.ubuntu.com gutsy/main Packages                           
Hit http://us.archive.ubuntu.com gutsy/restricted Packages                     
Hit http://us.archive.ubuntu.com gutsy/main Sources                            
Hit http://us.archive.ubuntu.com gutsy/restricted Sources                      
Hit http://security.ubuntu.com gutsy-security/universe Packages                
Hit http://security.ubuntu.com gutsy-security/universe Sources                 
Hit http://security.ubuntu.com gutsy-security/multiverse Packages              
Hit http://security.ubuntu.com gutsy-security/multiverse Sources               
Hit http://archive.canonical.com gutsy/partner Packages                        
Hit http://packages.medibuntu.org gutsy Release                      
Err http://packages.medibuntu.org gutsy Release                    
  
Hit http://us.archive.ubuntu.com gutsy/universe Packages           
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://archive.canonical.com gutsy/partner Sources               
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources          
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Get:7 http://packages.medibuntu.org gutsy Release [2723B]
Ign http://packages.medibuntu.org gutsy Release          
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-backports/main Packages
Hit http://us.archive.ubuntu.com gutsy-backports/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-backports/universe Packages
Hit http://us.archive.ubuntu.com gutsy-backports/multiverse Packages
Ign http://packages.medibuntu.org gutsy/free Packages
Hit http://us.archive.ubuntu.com gutsy-backports/main Sources
Hit http://us.archive.ubuntu.com gutsy-backports/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-backports/universe Sources
Hit http://us.archive.ubuntu.com gutsy-backports/multiverse Sources
Ign http://packages.medibuntu.org gutsy/non-free Packages
Hit http://packages.medibuntu.org gutsy/free Packages
Hit http://packages.medibuntu.org gutsy/non-free Packages
Fetched 2917B in 2s (1186B/s)
Reading package lists... Done
W: GPG error: http://packages.medibuntu.org gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
root@laptop:/home/scott#
```

---

### Post by zvacet on 2007-11-21
[B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -[/B]


So,in your case 

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 2EBC26B60C5A2783
 gpg --export --armor 2EBC26B60C5A2783  | sudo apt-key add -

---

### Post by scottsee on 2007-11-23
Thank-you sir.  The more i lear about Ubuntu the harder it gets..

---

### Post by erfahren on 2007-11-23
> **scottsee said:**
> Thank-you sir.  The more i lear about Ubuntu the harder it gets..
> **zvacet said:**
> [B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -[/B]

So,in your case 

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 2EBC26B60C5A2783
 gpg --export --armor 2EBC26B60C5A2783  | sudo apt-key add -
What that does is get the authentication key for the Mediubuntu repository (see: "Managing Authentication Keys" here: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) )

Before geting the update you must've not done the line in the wiki guide where it said:
```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -

```
Hopefully that'll make things seem a little less complicated (or this part at least).

anyway, I just wanted to say that although there is a pretty good "learning curve" to Linux the difficulty of it does level off some. 

You can mark this thread as "Solved" by going to the "Thread Tools" above the first post.

good luck! :)

---

