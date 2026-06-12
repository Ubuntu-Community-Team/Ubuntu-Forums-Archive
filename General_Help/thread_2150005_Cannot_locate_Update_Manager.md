---
title: "Cannot locate Update Manager"
date: 2013-05-30
forum: General Help
---

### Post by sahrs on 2013-05-30
I want to upgrade to ubuntu 13.04... but I cannot locate the update manager anywhere. The only thing that's similar that I've found is the software updater, which does not provide an update to 13.04. I have no idea what to do here. Is this a common issue?

---

### Post by deadflowr on 2013-05-30
There is no update manager in 12.10.
Only software updater.

You'll have to go to system settings > software sources > updates and make sure that the new version selection is set to any new version, and not long term or none.

Then simply run the software updater and the new version should be listed as 'upgrade' at the top.

---

### Post by sahrs on 2013-05-30
It was already set to 'any new version'. Now what? I switched it back and forth for good measure. No difference.

---

### Post by deadflowr on 2013-05-30
It's been a while since I've used this method but try opening a terminal and run
```
update-manager -d
```

The software updater will probably run and then it should list upgrade somewhere.

---

### Post by sahrs on 2013-05-30
No change.

---

### Post by deadflowr on 2013-05-30
Post
```
cat /etc/lsb-release
```

To see what version you're actually running now.

---

### Post by sahrs on 2013-05-30
Ok, did that. I don't think it was mistaken ever, it's on 12.10 right now.

---

### Post by sahrs on 2013-05-30
Can you possibly provide a command that would do what I'm attempting to make the software updater do? It'd very appreciated!

---

### Post by deadflowr on 2013-05-30
What happens when you run the software updater?

It should start  running the checking for updates when it launches.

You could try
```
sudo apt-get clean && sudo apt-get update
```

Then try launching the software updater.

---

### Post by sahrs on 2013-05-30
The updater checks and presents updates, but not an OS update. I will try that command.

---

### Post by sahrs on 2013-05-30
Result:
```
Hit http://ppa.launchpad.net quantal Release.gpg                               
Get:1 http://security.ubuntu.com quantal-security Release.gpg [933 B]          
Get:2 http://security.ubuntu.com quantal-security Release [49.6 kB]            
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://ppa.launchpad.net quantal/main Sources                              
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit http://repo.steampowered.com precise Release.gpg                           
Hit http://repo.steampowered.com precise Release                               
Get:3 http://security.ubuntu.com quantal-security/main Sources [41.3 kB]       
Hit http://extras.ubuntu.com quantal Release.gpg                               
Hit http://repo.steampowered.com precise/steam Sources                         
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Hit http://extras.ubuntu.com quantal Release                                   
Hit http://repo.steampowered.com precise/steam amd64 Packages                  
Get:4 http://security.ubuntu.com quantal-security/restricted Sources [1,833 B] 
Get:5 http://security.ubuntu.com quantal-security/universe Sources [17.5 kB]   
Hit http://repo.steampowered.com precise/steam i386 Packages                   
Get:6 http://security.ubuntu.com quantal-security/multiverse Sources [690 B]   
Get:7 http://security.ubuntu.com quantal-security/main amd64 Packages [118 kB] 
Hit http://extras.ubuntu.com quantal/main Sources                              
Get:8 http://security.ubuntu.com quantal-security/restricted amd64 Packages [3,469 B]
Hit http://extras.ubuntu.com quantal/main amd64 Packages                       
Get:9 http://security.ubuntu.com quantal-security/universe amd64 Packages [50.8 kB]
Hit http://extras.ubuntu.com quantal/main i386 Packages                        
Ign http://repo.steampowered.com precise/steam Translation-en_US               
Ign http://repo.steampowered.com precise/steam Translation-en                  
Get:10 http://security.ubuntu.com quantal-security/multiverse amd64 Packages [1,152 B]
Get:11 http://security.ubuntu.com quantal-security/main i386 Packages [117 kB] 
Get:12 http://security.ubuntu.com quantal-security/restricted i386 Packages [3,531 B]
Get:13 http://security.ubuntu.com quantal-security/universe i386 Packages [51.4 kB]
Ign http://ppa.launchpad.net quantal/main Translation-en_US                    
Get:14 http://security.ubuntu.com quantal-security/multiverse i386 Packages [1,393 B]
Ign http://extras.ubuntu.com quantal/main Translation-en_US                    
Ign http://extras.ubuntu.com quantal/main Translation-en                       
Get:15 http://security.ubuntu.com quantal-security/main Translation-en [62.6 kB]
Ign http://ppa.launchpad.net quantal/main Translation-en                       
Err http://us.archive.ubuntu.com quantal Release.gpg                           
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Hit http://security.ubuntu.com quantal-security/multiverse Translation-en      
Get:16 http://us.archive.ubuntu.com quantal-updates Release.gpg [933 B]        
Get:17 http://us.archive.ubuntu.com quantal-backports Release.gpg [933 B]      
Hit http://security.ubuntu.com quantal-security/restricted Translation-en      
Hit http://us.archive.ubuntu.com quantal Release                               
Get:18 http://us.archive.ubuntu.com quantal-updates Release [49.6 kB]          
Get:19 http://security.ubuntu.com quantal-security/universe Translation-en [31.3 kB]
Get:20 http://us.archive.ubuntu.com quantal-backports Release [49.6 kB]        
Ign http://us.archive.ubuntu.com quantal/main Sources/DiffIndex                
Ign http://us.archive.ubuntu.com quantal/restricted Sources/DiffIndex          
Ign http://us.archive.ubuntu.com quantal/universe Sources/DiffIndex            
Ign http://us.archive.ubuntu.com quantal/multiverse Sources/DiffIndex          
Ign http://us.archive.ubuntu.com quantal/main amd64 Packages/DiffIndex         
Ign http://us.archive.ubuntu.com quantal/restricted amd64 Packages/DiffIndex   
Ign http://us.archive.ubuntu.com quantal/universe amd64 Packages/DiffIndex     
Ign http://us.archive.ubuntu.com quantal/multiverse amd64 Packages/DiffIndex   
Ign http://us.archive.ubuntu.com quantal/main i386 Packages/DiffIndex          
Ign http://us.archive.ubuntu.com quantal/restricted i386 Packages/DiffIndex    
Ign http://us.archive.ubuntu.com quantal/universe i386 Packages/DiffIndex      
Ign http://us.archive.ubuntu.com quantal/multiverse i386 Packages/DiffIndex    
Hit http://us.archive.ubuntu.com quantal/main Translation-en                   
Hit http://us.archive.ubuntu.com quantal/multiverse Translation-en             
Ign http://security.ubuntu.com quantal-security/main Translation-en_US         
Hit http://us.archive.ubuntu.com quantal/restricted Translation-en             
Ign http://security.ubuntu.com quantal-security/multiverse Translation-en_US   
Ign http://security.ubuntu.com quantal-security/restricted Translation-en_US   
Ign http://security.ubuntu.com quantal-security/universe Translation-en_US     
Hit http://us.archive.ubuntu.com quantal/universe Translation-en               
Get:21 http://us.archive.ubuntu.com quantal-updates/main Sources [92.9 kB]     
Get:22 http://us.archive.ubuntu.com quantal-updates/restricted Sources [2,564 B]
Get:23 http://us.archive.ubuntu.com quantal-updates/universe Sources [87.0 kB] 
Get:24 http://us.archive.ubuntu.com quantal-updates/multiverse Sources [3,655 B]
Get:25 http://us.archive.ubuntu.com quantal-updates/main amd64 Packages [239 kB]
Get:26 http://us.archive.ubuntu.com quantal-updates/restricted amd64 Packages [4,804 B]
Get:27 http://us.archive.ubuntu.com quantal-updates/universe amd64 Packages [190 kB]
Get:28 http://us.archive.ubuntu.com quantal-updates/multiverse amd64 Packages [10.6 kB]
Get:29 http://us.archive.ubuntu.com quantal-updates/main i386 Packages [238 kB]
Get:30 http://us.archive.ubuntu.com quantal-updates/restricted i386 Packages [4,841 B]
Get:31 http://us.archive.ubuntu.com quantal-updates/universe i386 Packages [191 kB]
Get:32 http://us.archive.ubuntu.com quantal-updates/multiverse i386 Packages [10.8 kB]
Get:33 http://us.archive.ubuntu.com quantal-updates/main Translation-en [114 kB]
Hit http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com quantal-updates/restricted Translation-en     
Get:34 http://us.archive.ubuntu.com quantal-updates/universe Translation-en [100 kB]
Get:35 http://us.archive.ubuntu.com quantal-backports/main Sources [14 B]      
Get:36 http://us.archive.ubuntu.com quantal-backports/restricted Sources [14 B]
Get:37 http://us.archive.ubuntu.com quantal-backports/universe Sources [15.6 kB]
Get:38 http://us.archive.ubuntu.com quantal-backports/multiverse Sources [1,879 B]
Get:39 http://us.archive.ubuntu.com quantal-backports/main amd64 Packages [14 B]
Get:40 http://us.archive.ubuntu.com quantal-backports/restricted amd64 Packages [14 B]
Get:41 http://us.archive.ubuntu.com quantal-backports/universe amd64 Packages [19.9 kB]
Get:42 http://us.archive.ubuntu.com quantal-backports/multiverse amd64 Packages [2,201 B]
Get:43 http://us.archive.ubuntu.com quantal-backports/main i386 Packages [14 B]
Get:44 http://us.archive.ubuntu.com quantal-backports/restricted i386 Packages [14 B]
Get:45 http://us.archive.ubuntu.com quantal-backports/universe i386 Packages [20.6 kB]
Get:46 http://us.archive.ubuntu.com quantal-backports/multiverse i386 Packages [2,184 B]
Hit http://us.archive.ubuntu.com quantal-backports/main Translation-en         
Hit http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com quantal-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com quantal-backports/universe Translation-en     
Hit http://us.archive.ubuntu.com quantal/main Sources                          
Hit http://us.archive.ubuntu.com quantal/restricted Sources                    
Hit http://us.archive.ubuntu.com quantal/universe Sources                      
Hit http://us.archive.ubuntu.com quantal/multiverse Sources                    
Hit http://us.archive.ubuntu.com quantal/main amd64 Packages                   
Hit http://us.archive.ubuntu.com quantal/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com quantal/universe amd64 Packages               
Hit http://us.archive.ubuntu.com quantal/multiverse amd64 Packages             
Hit http://us.archive.ubuntu.com quantal/main i386 Packages                    
Hit http://us.archive.ubuntu.com quantal/restricted i386 Packages              
Hit http://us.archive.ubuntu.com quantal/universe i386 Packages                
Hit http://us.archive.ubuntu.com quantal/multiverse i386 Packages              
Ign http://us.archive.ubuntu.com quantal/main Translation-en_US                
Ign http://us.archive.ubuntu.com quantal/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal/universe Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/universe Translation-en_US
Fetched 2,005 kB in 49s (40.6 kB/s)
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/Release.gpg  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.


```

What would you advise I proceed to do?

---

### Post by sahrs on 2013-06-07
bump?

---

### Post by matt_symes on 2013-06-07
Hi

```
sudo do-release-upgrade
```

Post back any errors or output if it does not upgrade.

Make a backup before you run the command.

Kind regards

---

### Post by deadflowr on 2013-06-07
See if this helps

```
[COLOR=#000000]*cd /var/lib/apt*[/COLOR]
[COLOR=#000000]*sudo mv lists lists.old*[/COLOR]
[COLOR=#000000]*sudo mkdir -p lists/partial*[/COLOR]
[COLOR=#000000]*sudo apt-get update*[/COLOR]

```

---

