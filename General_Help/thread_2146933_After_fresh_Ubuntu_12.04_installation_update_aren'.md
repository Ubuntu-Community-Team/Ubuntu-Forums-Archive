---
title: "After fresh Ubuntu 12.04 installation update aren't being installed"
date: 2013-05-20
forum: General Help
---

### Post by uzumakifahim on 2013-05-20
I've installed Ubuntu 12.04 on a computer. Everything is fine without  update. Just after the installation, it was showing about 200 MB updates  to download. Since then I'm trying to install all the updates. Now it's  partially completed, some of the software (firefox,VLC) is updated.  Still it's showing 39.3 MB updates to download and it's failing again  and again. Every time I tried to install these 39.3 MB updates, it shows  that, it can't connect to internet, but there is no problem with my  connection (Network indicator shows it's connected and I can browse and  download anything). It's giving me the following message:

```
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.2.0-43-generic-pae_3.2.0-43.68_i386.deb Size mismatch 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.2.0-43-generic-pae_3.2.0-43.68_i386.deb Size mismatch
```

I thought this is a problem with sources list. So I've given the following command

```

sudo rm -vf /var/lib/apt/lists/partial/*
```

Previously, I've faced similar type of problem with a different  computer. At that time, this solution worked for me, but now I'm still  facing this problem. Anyone please help me to solve this problem.

---

### Post by fantab on 2013-05-20
Post the output of *sudo apt-get update*.

---

### Post by uzumakifahim on 2013-05-20
Thanks for your prompt reply. Here is the output of ```
sudo apt-get update
```

```
Hit http://dl.google.com stable Release.gpg                                    
Hit http://archive.canonical.com precise Release.gpg                           
Get:1 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Hit http://dl.google.com stable Release                                        
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Hit http://archive.canonical.com precise Release                     
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://extras.ubuntu.com precise Release                                   
Ign http://dl.google.com stable/main TranslationIndex                          
Get:2 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]
Hit http://archive.canonical.com precise/partner i386 Packages                 
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Hit http://us.archive.ubuntu.com precise-security Release.gpg                  
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://us.archive.ubuntu.com precise Release                               
Ign http://dl.google.com stable/main Translation-en_US                         
Get:3 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Ign http://dl.google.com stable/main Translation-en                            
Get:4 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://archive.canonical.com precise/partner Translation-en                
Hit http://us.archive.ubuntu.com precise-backports Release                     
Hit http://us.archive.ubuntu.com precise-security Release                      
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Hit http://us.archive.ubuntu.com precise/main Sources                          
Ign http://extras.ubuntu.com precise/main Translation-en                       
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex
Get:5 http://us.archive.ubuntu.com precise-updates/main Sources [383 kB]
Get:6 http://us.archive.ubuntu.com precise-updates/main Sources [383 kB]       
Get:7 http://us.archive.ubuntu.com precise-updates/restricted Sources [5,467 B]
Get:8 http://us.archive.ubuntu.com precise-updates/universe Sources [87.1 kB]  
Get:9 http://us.archive.ubuntu.com precise-updates/universe Sources [87.1 kB]  
Get:10 http://us.archive.ubuntu.com precise-updates/universe Sources [87.1 kB] 
Get:11 http://us.archive.ubuntu.com precise-updates/multiverse Sources [6,582 B]
Get:12 http://us.archive.ubuntu.com precise-updates/main i386 Packages [625 kB]
Get:13 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [10.0 kB]
Get:14 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [203 kB]
Get:15 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [13.8 kB]
Get:16 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [13.8 kB]
100% [16 Packages bzip2 0 B] [Connecting to us.archive.ubuntu.com (91.189.91.14
bzip2: Compressed file ends unexpectedly;
    perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://us.archive.ubuntu.com precise-backports/main Sources                
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://us.archive.ubuntu.com precise-backports/universe Sources
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise-security/main Sources
Hit http://us.archive.ubuntu.com precise-security/restricted Sources
Hit http://us.archive.ubuntu.com precise-security/universe Sources
Hit http://us.archive.ubuntu.com precise-security/multiverse Sources
Hit http://us.archive.ubuntu.com precise-security/main i386 Packages
Hit http://us.archive.ubuntu.com precise-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-security/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-security/multiverse i386 Packages
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
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Hit http://us.archive.ubuntu.com precise-security/main Translation-en
Hit http://us.archive.ubuntu.com precise-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-security/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-security/universe Translation-en
Fetched 935 kB in 3min 39s (4,261 B/s)
W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.


```

---

### Post by fantab on 2013-05-20
Try this:
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by uzumakifahim on 2013-05-20
> **fantab said:**
> Try this:
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade

Thanks, I'll try these and post the output here, but actually I want to stick with 12.04. Are you suggesting to upgrade to 13.04? Why?

---

### Post by fantab on 2013-05-21
No. I am not suggesting you to upgrade to 13.04. 

The command "*apt-get dist-upgrade*" doesn't do that, its just does 'smart' upgrade as opposed to "*apt-get get upgrade*" which does 'normal' upgrade as done by "Software updater" or Update-manager.

---

### Post by uzumakifahim on 2013-05-21
Here is the output

```
audity@auditypc:~$ sudo rm /var/lib/apt/lists/* -vf
[sudo] password for audity: 
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_Release'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_Release.gpg'
removed `/var/lib/apt/lists/dl.google.com_linux_talkplugin_deb_dists_stable_main_binary-i386_Packages'
removed `/var/lib/apt/lists/dl.google.com_linux_talkplugin_deb_dists_stable_Release'
removed `/var/lib/apt/lists/dl.google.com_linux_talkplugin_deb_dists_stable_Release.gpg'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_source_Sources'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_Release'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_Release.gpg'
removed `/var/lib/apt/lists/lock'
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_main_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_main_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_main_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_main_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_Release'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_Release.gpg'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_Release'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_Release.gpg'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_restricted_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_restricted_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-security_main_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-security_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-security_multiverse_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-security_Release'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-security_Release.gpg'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-security_restricted_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-security_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-security_universe_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_Release'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_Release.gpg'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_source_Sources'
audity@auditypc:~$ sudo apt-get clean
[sudo] password for audity: 
audity@auditypc:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
audity@auditypc:~$ sudo apt-get update
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Get:2 http://us.archive.ubuntu.com precise Release.gpg [198 B]                 
Get:3 http://dl.google.com stable Release [1,347 B]                            
Get:4 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Get:5 http://archive.canonical.com precise Release.gpg [198 B]                 
Get:6 http://dl.google.com stable/main i386 Packages [763 B]                   
Get:7 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Get:8 http://extras.ubuntu.com precise Release [11.9 kB]                       
Ign http://dl.google.com stable/main TranslationIndex                          
Get:9 http://archive.canonical.com precise Release [7,078 B]                   
Get:10 http://extras.ubuntu.com precise/main Sources [8,130 B]                 
Get:11 http://us.archive.ubuntu.com precise-backports Release.gpg [198 B]      
Get:12 http://archive.canonical.com precise/partner i386 Packages [8,261 B]    
Get:13 http://extras.ubuntu.com precise/main i386 Packages [10.8 kB]           
Ign http://archive.canonical.com precise/partner TranslationIndex              
Get:14 http://us.archive.ubuntu.com precise-security Release.gpg [198 B]       
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:15 http://us.archive.ubuntu.com precise Release [49.6 kB]                  
Ign http://dl.google.com stable/main Translation-en_US                         
Get:16 http://us.archive.ubuntu.com precise Release [49.6 kB]                  
Ign http://dl.google.com stable/main Translation-en                            
Get:17 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]          
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://archive.canonical.com precise/partner Translation-en_US             
Get:18 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]          
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://archive.canonical.com precise/partner Translation-en                
Get:19 http://us.archive.ubuntu.com precise-backports Release [49.6 kB]        
Get:20 http://us.archive.ubuntu.com precise-backports Release [49.6 kB]        
Get:21 http://us.archive.ubuntu.com precise-backports Release [49.6 kB]        
Ign http://us.archive.ubuntu.com precise-backports Release                     
E: GPG error: http://us.archive.ubuntu.com precise-backports Release: The following signatures were invalid: NODATA 2
audity@auditypc:~$ 


```

I'll post here *sudo apt-get dist-upgrade* output ASAP.

---

### Post by fantab on 2013-05-21
To resolve the GPG error Try:

```
$ sudo -i
# apt-get clean
# cd /var/lib/apt
# mv lists lists.old
# mkdir -p lists/partial
# apt-get clean
# apt-get update
# exit

```

if this doesn't help and you still get errors then post the output of "sudo apt-get update".

---

### Post by uzumakifahim on 2013-05-21
```
audity@auditypc:~$ sudo apt-get dist-upgrade
[sudo] password for audity: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
audity@auditypc:~$ 

```

I'll post the output of your latest command ASAP. Thanks.

---

### Post by uzumakifahim on 2013-05-22
Unfortunately, I'm still facing the same problem. So, here is the **sudo apt-get update** output as you wanted.

```
audity@auditypc:~$ sudo apt-get update
[sudo] password for audity: 
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Hit http://dl.google.com stable Release.gpg                                    
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://dl.google.com stable Release                                        
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://archive.canonical.com precise Release                     
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://archive.canonical.com precise/partner i386 Packages                 
Hit http://extras.ubuntu.com precise Release                         
Get:2 http://us.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://extras.ubuntu.com precise/main Sources                              
Get:3 http://us.archive.ubuntu.com precise-security Release.gpg [198 B]
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Get:4 http://us.archive.ubuntu.com precise-security Release.gpg [198 B]        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://us.archive.ubuntu.com precise Release                               
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Get:5 http://us.archive.ubuntu.com precise-updates Release [49.6 kB] 
Get:6 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://archive.canonical.com precise/partner Translation-en                
Get:7 http://us.archive.ubuntu.com precise-backports Release [49.6 kB]         
Get:8 http://us.archive.ubuntu.com precise-backports Release [49.6 kB]         
Get:9 http://us.archive.ubuntu.com precise-backports Release [49.6 kB]         
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Get:10 http://us.archive.ubuntu.com precise-security Release [49.6 kB]         
Get:11 http://us.archive.ubuntu.com precise-security Release [49.6 kB]         
Get:12 http://us.archive.ubuntu.com precise-security Release [49.6 kB]         
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/main Sources
Hit http://us.archive.ubuntu.com precise-updates/restricted Sources
Hit http://us.archive.ubuntu.com precise-updates/universe Sources
Hit http://us.archive.ubuntu.com precise-updates/multiverse Sources
Hit http://us.archive.ubuntu.com precise-updates/main i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/main Sources
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources
Hit http://us.archive.ubuntu.com precise-backports/universe Sources
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex
Get:13 http://us.archive.ubuntu.com precise-backports/universe TranslationIndex [73 B]
Hit http://us.archive.ubuntu.com precise-security/main Sources
Hit http://us.archive.ubuntu.com precise-security/restricted Sources
Hit http://us.archive.ubuntu.com precise-security/universe Sources
Hit http://us.archive.ubuntu.com precise-security/multiverse Sources
Hit http://us.archive.ubuntu.com precise-security/main i386 Packages           
Hit http://us.archive.ubuntu.com precise-security/restricted i386 Packages     
Hit http://us.archive.ubuntu.com precise-security/universe i386 Packages       
Hit http://us.archive.ubuntu.com precise-security/multiverse i386 Packages     
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
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Get:14 http://us.archive.ubuntu.com precise-backports/universe Translation-en [22.4 kB]
Hit http://us.archive.ubuntu.com precise-security/main Translation-en          
Hit http://us.archive.ubuntu.com precise-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-security/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-security/universe Translation-en
Fetched 68.6 kB in 1min 7s (1,009 B/s)
Reading package lists... Done
audity@auditypc:~$ 


```

---

### Post by HiImTye on 2013-05-22
do the dist upgrade after the update, i.e.
```
sudo apt-get update; sudo apt-get dist-upgrade -y
```

---

### Post by fantab on 2013-05-22
> **uzumakifahim said:**
> Unfortunately, I'm still facing the same problem. So, here is the **sudo apt-get update** output as you wanted.

I don't see any errors. You are fine. Probably there are no updates to install at the moment.
What do you get with, *sudo apt-get upgrade* ?

---

### Post by uzumakifahim on 2013-05-23
> **fantab said:**
> I don't see any errors. You are fine. Probably there are no updates to install at the moment.
What do you get with, *sudo apt-get upgrade* ?

Yes, you are right, I also found that, there is no error in the *sudo apt-get update* output, but I'm still facing same problem.

 *sudo apt-get upgrade* output is here. 

```
audity@auditypc:~$ sudo apt-get upgrade
[sudo] password for audity: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic-pae linux-headers-generic-pae linux-image-generic-pae
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
audity@auditypc:~$ 


```

Point to be noted here that, three packages kept back here and I'm  facing problem just with these 3 packages. So, is it somehow related  with the problem?

---

### Post by fantab on 2013-05-23
Run:
```
sudo apt-get dist-upgrade
```

If you still see that the packages are held back:
```
sudo apt-get install linux
```

If the problem continues:
```
sudo apt-get install linux-generic-pae linux-headers-generic-pae linux-image-generic-pae.

```
Install 'Synaptic' Package Manager, if you haven't already. It makes things easier with GUI.

EDIT: If you still have the problem after doing all the above then change the 'server' to MAIN in "Software Center" -> EDIT -> Software Sources.

---

### Post by uzumakifahim on 2013-05-26
> **fantab said:**
> Run:
```
sudo apt-get dist-upgrade
```

If you still see that the packages are held back:
```
sudo apt-get install linux
```

If the problem continues:
```
sudo apt-get install linux-generic-pae linux-headers-generic-pae linux-image-generic-pae.

```
Install 'Synaptic' Package Manager, if you haven't already. It makes things easier with GUI.

EDIT: If you still have the problem after doing all the above then change the 'server' to MAIN in "Software Center" -> EDIT -> Software Sources.

WOW!!! **sudo apt-get install linux** worked for me. It's perfect now. Really thanks to fantab for your continuous A to Z support. Could you please explain here that, what was the problem and how this solution worked for that? 

Good luck.

---

