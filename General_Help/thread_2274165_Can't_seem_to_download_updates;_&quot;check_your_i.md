---
title: "Can't seem to download updates; &quot;check your internet connection&quot;....(??)"
date: 2015-04-18
forum: General Help
---

### Post by Mike_Walsh on 2015-04-18
Morning, all.

I changed my main install from Ubuntu to Xubuntu a few weeks ago. Had some problems enabling PPA's, which was fixed, thanks to sandyd.

I now appear to be having problems downloading updates. Every time the Software Updater pops up, and I click on 'install', it starts to download, then a window appears saying:-

[ATTACH=CONFIG]261392[/ATTACH]

'Failed to download repository information. Check your internet connection'.

Well, I know there's nothing wrong with my internet connection; if there was, I wouldn't be able to post on here. I've had this problem before, at times, and have been able to 'fix' it, temporarily or otherwise, by choosing a different server. This time round, it doesn't appear to be working. No matter which server I choose, it comes back to 'Failed to download repository information.....'

There's also a mention in 'Details' about 'hash sum mismatches' upon trying to connect to the repositories.

Would anybody happen to know what might be causing this? Any insights, or suggestions, would be appreciated.


Regards,

Mike. :confused:

---

### Post by nerdtron on 2015-04-18
You can try the command line to see the errors:
```
 sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Mike_Walsh on 2015-04-18
Curiouser and curiouser. I've finally managed to get my repository mirror changed, to 'mirror.krystal.co.uk'. Having done so, it says the software is up-to-date. Yet the previous mirrors were insisting that software needed to be downloaded, yet also insisted that they couldn't connect!

What IS going on? Might this be something to do with the authentication keys themselves?


Regards,

Mike.

---

### Post by Mike_Walsh on 2015-04-18
Hallo, nerdtron.

Well, now. Having said I've got the mirror successfully changed, when I ran

```
sudo apt-get update && sudo apt-get upgrade
```

(I KEEP forgetting to do this!)
this is what I get:-

```
paul@mic-w:~$ sudo apt-get update && sudo apt-get upgrade[sudo] password for paul: 
Ign http://extras.ubuntu.com trusty InRelease
Hit http://extras.ubuntu.com trusty Release.gpg                                
Ign http://archive.canonical.com trusty InRelease                              
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://archive.canonical.com trusty Release.gpg                            
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com trusty Release                                
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty/main Sources                               
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Ign http://archive.canonical.com trusty/partner Translation-en                 
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://extras.ubuntu.com trusty/main Translation-en_GB                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                     
Hit http://ppa.launchpad.net trusty/main i386 Packages                      
Hit http://ppa.launchpad.net trusty/main amd64 Packages                     
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main amd64 Packages                     
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-en_GB                  
Ign http://ppa.launchpad.net trusty/main Translation-en                     
Ign http://ppa.launchpad.net trusty/main Translation-en_GB
Ign http://ppa.launchpad.net trusty/main Translation-en
Err http://mirror.krystal.co.uk trusty InRelease                               
  
Err http://mirror.krystal.co.uk trusty-updates InRelease
  
Err http://mirror.krystal.co.uk trusty-backports InRelease
  
Err http://mirror.krystal.co.uk trusty-security InRelease
  
Err http://mirror.krystal.co.uk trusty Release.gpg
  Unable to connect to mirror.krystal.co.uk:http:
Err http://mirror.krystal.co.uk trusty-updates Release.gpg
  Unable to connect to mirror.krystal.co.uk:http:
Err http://mirror.krystal.co.uk trusty-backports Release.gpg
  Unable to connect to mirror.krystal.co.uk:http:
Err http://mirror.krystal.co.uk trusty-security Release.gpg
  Unable to connect to mirror.krystal.co.uk:http:
Reading package lists... Done
W: Failed to fetch http://mirror.krystal.co.uk/ubuntu/dists/trusty/InRelease  


W: Failed to fetch http://mirror.krystal.co.uk/ubuntu/dists/trusty-updates/InRelease  


W: Failed to fetch http://mirror.krystal.co.uk/ubuntu/dists/trusty-backports/InRelease  


W: Failed to fetch http://mirror.krystal.co.uk/ubuntu/dists/trusty-security/InRelease  


W: Failed to fetch http://mirror.krystal.co.uk/ubuntu/dists/trusty/Release.gpg  Unable to connect to mirror.krystal.co.uk:http:


W: Failed to fetch http://mirror.krystal.co.uk/ubuntu/dists/trusty-updates/Release.gpg  Unable to connect to mirror.krystal.co.uk:http:


W: Failed to fetch http://mirror.krystal.co.uk/ubuntu/dists/trusty-backports/Release.gpg  Unable to connect to mirror.krystal.co.uk:http:


W: Failed to fetch http://mirror.krystal.co.uk/ubuntu/dists/trusty-security/Release.gpg  Unable to connect to mirror.krystal.co.uk:http:


W: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
paul@mic-w:~$
```

Any clues?


Regards,

Mike.

---

### Post by nerdtron on 2015-04-18
Not sure about your PPA's but are you sure that you need the "mirror.krystal.co.uk". You can't connect to that URL, first I'd try is to disable that

---

### Post by Mike_Walsh on 2015-04-18
> **nerdtron said:**
> Not sure about your PPA's but are you sure that you need the "mirror.krystal.co.uk". You can't connect to that URL, first I'd try is to disable that

Okay. When you say 'Disable', do you mean change it for another mirror? Because it's the only one in the entire list of UK mirrors that would actually install in the first place...


Regards,

Mike.

---

### Post by Mike_Walsh on 2015-04-19
UPDATE:-

Have just done a complete re-install, and the problem is no longer there. Therefore I am going to mark this as 'Solved', so that it doesn't use up further bandwidth and/or storage space.

Regards,

Mike.

---

