---
title: "Update failure 404"
date: 2014-06-19
forum: General Help
---

### Post by Yitzach on 2014-06-19
I'm getting the red security triangle indicating that some part of my system is not getting updated. I thought it was substituting armhf for amd64 but it lists calls to amd64 repositories. Here's the output from apt-get update:
```
Hit http://dl.google.com stable Release.gpg
Hit http://dl.google.com stable Release                                        
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                 
Get:2 http://us.archive.ubuntu.com precise-security Release.gpg [198 B]        
Hit http://us.archive.ubuntu.com precise Release                               
Get:3 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Hit http://developer.download.nvidia.com  Release.gpg                          
Hit http://developer.download.nvidia.com  Release                              
Hit http://developer.download.nvidia.com  Packages                            
Get:4 http://extras.ubuntu.com precise Release.gpg [72 B]
Hit http://us.archive.ubuntu.com precise-backports Release                     
Get:5 http://us.archive.ubuntu.com precise-security Release [49.6 kB]
Hit http://extras.ubuntu.com precise Release                                   
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://extras.ubuntu.com precise/main amd64 Packages 
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages     
Hit http://us.archive.ubuntu.com precise/universe i386 Packages       
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com precise/main TranslationIndex        
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex  
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex  
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex    
Get:6 http://us.archive.ubuntu.com precise-updates/main Sources [461 kB]
Err http://extras.ubuntu.com precise/main armhf Packages                     
  404  Not Found
Ign http://extras.ubuntu.com precise/main Translation-en_US                  
Ign http://extras.ubuntu.com precise/main Translation-en                     
Ign http://developer.download.nvidia.com  Translation-en_US
Ign http://developer.download.nvidia.com  Translation-en
Get:7 http://us.archive.ubuntu.com precise-updates/restricted Sources [8,056 B]
Get:8 http://us.archive.ubuntu.com precise-updates/universe Sources [108 kB]
Get:9 http://us.archive.ubuntu.com precise-updates/multiverse Sources [8,890 B]
Get:10 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [791 kB]
Get:11 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [13.7 kB]
Get:12 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [242 kB]
Get:13 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [15.3 kB]
Get:14 http://us.archive.ubuntu.com precise-updates/main i386 Packages [824 kB]
Get:15 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [13.7 kB]
Get:16 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [248 kB]
Get:17 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]
Get:18 http://us.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:19 http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:20 http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:21 http://us.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Hit http://us.archive.ubuntu.com precise-backports/main Sources                
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://us.archive.ubuntu.com precise-backports/universe Sources            
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages         
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages   
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages     
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages   
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex   
Get:22 http://us.archive.ubuntu.com precise-security/main Sources [106 kB]     
Get:23 http://us.archive.ubuntu.com precise-security/restricted Sources [2,494 B]
Get:24 http://us.archive.ubuntu.com precise-security/universe Sources [30.7 kB]
Get:25 http://us.archive.ubuntu.com precise-security/multiverse Sources [1,795 B]
Get:26 http://us.archive.ubuntu.com precise-security/main amd64 Packages [401 kB]
Get:27 http://us.archive.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]
Get:28 http://us.archive.ubuntu.com precise-security/universe amd64 Packages [93.6 kB]
Get:29 http://us.archive.ubuntu.com precise-security/multiverse amd64 Packages [2,434 B]
Get:30 http://us.archive.ubuntu.com precise-security/main i386 Packages [427 kB]
Get:31 http://us.archive.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:32 http://us.archive.ubuntu.com precise-security/universe i386 Packages [98.7 kB]
Get:33 http://us.archive.ubuntu.com precise-security/multiverse i386 Packages [2,647 B]
Hit http://us.archive.ubuntu.com precise-security/main TranslationIndex        
Hit http://us.archive.ubuntu.com precise-security/multiverse TranslationIndex  
Hit http://us.archive.ubuntu.com precise-security/restricted TranslationIndex  
Hit http://us.archive.ubuntu.com precise-security/universe TranslationIndex    
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Get:34 http://us.archive.ubuntu.com precise-updates/universe Translation-en [141 kB]
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en     
Err http://us.archive.ubuntu.com precise/main armhf Packages                   
  404  Not Found [IP: 91.189.91.14 80]
Hit http://us.archive.ubuntu.com precise-security/main Translation-en          
Hit http://us.archive.ubuntu.com precise-security/multiverse Translation-en    
Hit http://us.archive.ubuntu.com precise-security/restricted Translation-en    
Hit http://us.archive.ubuntu.com precise-security/universe Translation-en      
Err http://us.archive.ubuntu.com precise/restricted armhf Packages             
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com precise/universe armhf Packages               
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com precise/multiverse armhf Packages             
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com precise-updates/main armhf Packages           
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com precise-updates/restricted armhf Packages     
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com precise-updates/universe armhf Packages       
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com precise-updates/multiverse armhf Packages     
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com precise-backports/main armhf Packages         
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com precise-backports/restricted armhf Packages   
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com precise-backports/universe armhf Packages     
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com precise-backports/multiverse armhf Packages   
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com precise-security/main armhf Packages          
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com precise-security/restricted armhf Packages    
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com precise-security/universe armhf Packages      
  404  Not Found [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com precise-security/multiverse armhf Packages    
  404  Not Found [IP: 91.189.91.14 80]
Fetched 4,176 kB in 44s (92.8 kB/s)                                            
W: Failed to fetch http://dl.google.com/linux/talkplugin/deb/dists/stable/Release  Unable to find expected entry 'main/binary-armhf/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-armhf/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-armhf/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-armhf/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-armhf/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-armhf/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-armhf/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-armhf/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-armhf/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-armhf/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-armhf/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-armhf/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-armhf/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-armhf/Packages  404  Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-security/main/binary-armhf/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-armhf/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-security/universe/binary-armhf/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-armhf/Packages  404  Not Found [IP: 91.189.91.14 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

I did recently (8 days ago) install NVIDIA's nvcc. It looks like the those repositories got listed in the correct spot. The update manger says I haven't updated in 7 days. I'm not sure if I believe it as I have applied updates to the computer. I don't recall missing an update for this computer that I didn't get for another computer with the same distribution and version. I'm think something is lying to something else.
I really don't have time to be plumbing the depths of my OS any more than is necessary.

---

### Post by deadflowr on 2014-06-20
Post the output for 
```
cat /etc/apt/sources.list
```
I don't think you should have any armhf listings.
( I think the armhf repos are somewhere completely different)

---

### Post by Yitzach on 2014-06-22
```
cat /etc/apt/sources.list | grep armhf
```
did not return anything.
Your original request returned this, which I believe is unmodified from the day it was written:
```
 
# 

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ precise-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-security universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main


```

---

### Post by deadflowr on 2014-06-22
Try this
first run
```
sudo apt-get clean
```
and then rerun the update command again.
If that doesn't clean it, maybe try
```
sudo rm -rf /var/lib/apt/lists
```
and rerun the update command again.
(The lists folder will regenerate, but because it's starting over from scratch it'll be slow)

If you, for whatever reason, fear that the lists folder won't regenerate because of the existing problems, you can always save a quick backup 
```
sudo cp -R /var/lib/apt/lists/ /var/lib/apt/lists-backup
```
(Note, you can save that backup where ever you'd like)

See if either of the two things help.

---

### Post by Yitzach on 2014-06-24
No good. I cleaned it, updated it, removed the lists, GUI updated it, updated it, GUI updated it, cleaned it, and updated it again. I was waiting for a very long time at the GUI updates and cancelled and restarted it a few times. I never completed them. They said "waiting" or "waiting on other manager."
Where ever the problem is, it isn't in the lists or what ever is cleans. There were no mentions of armhf in the names of the lists.
I'm pretty sure it is looking extra and incorrect locations as it picked up the 3 ssl security updates that my laptop picked up earlier.

---

### Post by deadflowr on 2014-06-24
I guess the next step would be to backtrack and review the method to which you added the nvidia repos/nvcc.
(I'm clueless in that regard, so any info about the howto's is helpful)

In regards to the "waiting", that means you have another instance of apt running. Either a package manager/update manager, or through the terminal.

---

### Post by Yitzach on 2014-06-27
I thought the waiting thing was about another instance of apt-get or similar. But I don't recall any others were running at the time. But I might have messed that up with an &.
Here's the documentation for installing NVIDIA nvcc and related stuff: [http://docs.nvidia.com/cuda/cuda-getting-started-guide-for-linux/index.html](http://docs.nvidia.com/cuda/cuda-getting-started-guide-for-linux/index.html). I thought I followed the directions correctly enough as the thing is running correctly as best as I can determine. Like I said, I don't currently have time to go plumbing the depths of my OS for the cause. Since I'm still getting updates, whatever my OS may think, I can suffer through to my next reload.

---

