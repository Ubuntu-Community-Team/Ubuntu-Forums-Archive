---
title: "software-properties-common not found"
date: 2015-09-20
forum: General Help
---

### Post by Madhuvan on 2015-09-20
Hello, I have been using Ubuntu or Ubuntu Gnome for around one and half year now, but I would still say I am a novice. Right now I am using a Ubuntu Gnome on HP G6 Pavilion. A few days back I added Linux Mint Rafaela's repositories in order to install Mintstick. I had done that several times and it had always worked flawlessly. But this time after doing that the computer stopped letting me add more repositories. I checked several forums but could not find a way out. Then I used the command sudo apt-get remove mintsources. Since then the terminal is not accepting any command and says "apt-get not found". I saw on a thread that the way out was entering sudo apt-get install *software*-properties-*common* python-*software*-properties. This command gives me an error like "no installation client for software-properties-common is found". Now I am desperate, I know that reinstalling the OS is a way out, but I have 178 GB of DATA there which I do not have space to back up to. Please help and tell me if something can be done. Thank you.

---

### Post by QDR06VV9 on 2015-09-20
Mixing Repos from one distro to another is a good recipe for Breakage!
Can you get to /etc/apt/sources.list?
Post back the results of
```
gksudo gedit /etc/apt/sources.list
```
Using the code tags.

---

### Post by ajgreeny on 2015-09-20
Is terminal totally useless or is it just apt-get that is the problem?

I seem to remember reading somewhere that Mint now uses ```
sudo apt install
``` and ```
sudo apt remove
``` as commands instead of ```
sudo apt-get
``` so perhaps you could try that to see if things start to work again.

I haven't used Mint for a long time so I may be dreaming and speaking out of turn here, but if using **apt** alone instead of **apt-get** does not work I am sure it will tell you why with an error message and I don't think it will cause any problems.

---

### Post by Madhuvan on 2015-09-21
Hello, Thank you for the answers. @Runrickus: I am at work, once I return home I will do that. Thank you.
@ ajgreeny: The rest seems to be working fine. Just apt-get has a problem.

---

### Post by ajgreeny on 2015-09-21
So, can you use the command ```
sudo apt-get update
```
Show the output from that; copy it by highlighting with the mouse, right clicking and choosing "copy", then paste it into the reply box here in code tags by using the # icon in the toolbar or by typing the following:-
[noparse]```
your copied text
```[/noparse]

---

### Post by Madhuvan on 2015-09-21
```
rishiraj@rishiraj-HP-Pavilion-g6-notebook:~$ sudo apt-get update
[sudo] password for rishiraj: 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease                                 
Get:1 [http://deb.opera.com](http://deb.opera.com) stable InRelease [2,590 B]                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg                               
Get:2 [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages [1,749 B]            
Ign [http://download.videolan.org](http://download.videolan.org)  InRelease                                    
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) qiana InRelease                              
Get:3 [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages [1,448 B]             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release                                   
Ign [http://mega.nz](http://mega.nz) ./ InRelease                                                
Hit [http://download.videolan.org](http://download.videolan.org)  Release.gpg                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:4 [http://packages.linuxmint.com](http://packages.linuxmint.com) qiana Release.gpg [198 B]                  
Get:5 [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb InRelease [8,143 B]              
Hit [http://download.videolan.org](http://download.videolan.org)  Release                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe amd64 Packages                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:6 [http://mega.nz](http://mega.nz) ./ Release.gpg [189 B]                                    
Hit [http://download.videolan.org](http://download.videolan.org)  Sources                                      
Get:7 [http://packages.linuxmint.com](http://packages.linuxmint.com) qiana Release [24.2 kB]                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe i386 Packages                    
Get:8 [http://mega.nz](http://mega.nz) ./ Release [967 B]                                        
Hit [http://download.videolan.org](http://download.videolan.org)  Packages                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:9 [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb/apps amd64 Packages [68.9 kB]    
Get:10 [http://mega.nz](http://mega.nz) ./ Packages [1,436 B]                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:11 [http://packages.linuxmint.com](http://packages.linuxmint.com) qiana/main amd64 Packages [31.0 kB]       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_IN                     
Get:12 [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb/games amd64 Packages [90.9 kB]  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:13 [http://packages.linuxmint.com](http://packages.linuxmint.com) qiana/main i386 Packages [30.4 kB]        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en_IN                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://download.videolan.org](http://download.videolan.org)  Translation-en_IN                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Ign [http://download.videolan.org](http://download.videolan.org)  Translation-en                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Get:14 [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb/apps i386 Packages [69.8 kB]    
Get:15 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Get:16 [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb/games i386 Packages [93.3 kB]   
Get:17 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Ign [http://mega.nz](http://mega.nz) ./ Translation-en_IN                                        
Get:18 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Ign [http://mega.nz](http://mega.nz) ./ Translation-en                                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Get:19 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release [15.1 kB]                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Get:20 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release [15.1 kB]                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Get:21 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release [15.1 kB]                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Ign [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb/apps Translation-en_IN             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Ign [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb/apps Translation-en                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Ign [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb/games Translation-en_IN            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Ign [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb/games Translation-en               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:22 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages [44.6 kB]           
Get:23 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [44.6 kB]            
Get:24 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en [25.8 kB]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:25 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages [20.1 kB]           
Get:26 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [19.9 kB]            
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) qiana/main Translation-en_IN                 
Get:27 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en [10.6 kB]           
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) qiana/main Translation-en                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:28 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages [14.2 kB]           
Get:29 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [14.2 kB]            
Get:30 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en [4,946 B]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_IN                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_IN                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Fetched 670 kB in 20s (32.4 kB/s)                                              
Reading package lists... Done
```

---

### Post by Madhuvan on 2015-09-21
Hello, this was the only output to 
gksudo gedit /etc/apt/sources.list



deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe

---

### Post by Madhuvan on 2015-09-21
Moreover, all commands are working except for the ones to add repositories. For example: 


rishiraj@rishiraj-HP-Pavilion-g6-notebook:~$ sudo add-apt-repository ppa:ricotz/docky
[sudo] password for rishiraj: 
sudo: add-apt-repository: command not found
rishiraj@rishiraj-HP-Pavilion-g6-notebook:~$

---

### Post by QDR06VV9 on 2015-09-21
It looks like Apt is Foobared(Corupt).
I have .gz a New Apt for you.
So download the attachment I gave you and then open your file manger as root.
```
gksudo nautlius
```
if you are using a different file manager then insert that into the command above IE: caja, nemo, dolphin. hope this clear enough.
I would before doing the below
While you are in root with your file manager navigate to /etc
and Delete the apt folder 
Then navigate to the downloaed apt.tar.gz I gave you and extract it to /etc.
Then run 
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

[B]Be Aware though there is no PPAs In that file just Stock as in a fresh install. 
[/B]

Let us know how this gose.
Regards

---

### Post by Madhuvan on 2015-09-21
Thank you so much Runrickus, I did these things all went well, but after that once again I got:

rishiraj@rishiraj-HP-Pavilion-g6-notebook:~$ sudo add-apt-repository ppa:ricotz/docky
sudo: add-apt-repository: command not found

---

### Post by QDR06VV9 on 2015-09-21
Have you rebooted yet?
And you should be able to add that PPA to your [COLOR=#000000] /etc/apt/sources.list
By way of 
[/COLOR]```
[COLOR=#000000]gksudo gedit /etc/apt/sources.list[/COLOR]

```[COLOR=#000000] 
Copy and Paste the below.
[/COLOR]> deb [http://ppa.launchpad.net/ricotz/docky/ubuntu](http://ppa.launchpad.net/ricotz/docky/ubuntu) trusty main 
deb-src [http://ppa.launchpad.net/ricotz/docky/ubuntu](http://ppa.launchpad.net/ricotz/docky/ubuntu) trusty main
Then to avoid no keys found warning
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEY_ID
```
Where KEY_ID will be the key needed for that PPA which will be shown in the terminal.
I will hang in here for bit to see how you are doing.

---

### Post by Madhuvan on 2015-09-21
Well Runrickus, this worked! I can't believe it. After rebooting all returned to normal. You are my hero. THANK YOU SO MUCH!

---

### Post by QDR06VV9 on 2015-09-21
Very Nice! Good Job.
Glad i could help.
Kind Regards
Please Mark this Thread as Solved to help others.

---

### Post by Madhuvan on 2015-09-21
How do I marked this "solved"? Thanks again. I am so happy! All thanks to you.

---

### Post by slickymaster on 2015-09-21
> **Madhuvan said:**
> How do I marked this "solved"? Thanks again. I am so happy! All thanks to you.

Here you go: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Madhuvan on 2015-09-21
Thank you.

---

