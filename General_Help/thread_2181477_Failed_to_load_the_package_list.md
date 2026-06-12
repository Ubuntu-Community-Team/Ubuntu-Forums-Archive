---
title: "Failed to load the package list"
date: 2013-10-18
forum: General Help
---

### Post by maxxmenon on 2013-10-18
Hello 

I have been having a problem on updates as I get a red icon on the title bar to the right with the message as given in the title for this post. A window pops up with the following message in it 

[I]This is a serious problem. Try again later. If this problem appears again, please report an error to the developers.

E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_raring_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.[/I]


I tried the sudo apt-get update command in the terminal and I got this as the output. What must I do please?

[I]```
sudo apt-get update
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring Release.gpg [933 B]                  
Get:5 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release.gpg [933 B]           
Get:7 [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg [72 B]                       
Get:8 [http://archive.canonical.com](http://archive.canonical.com) raring Release.gpg [933 B]                  
Get:9 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [1,206 B]                
Get:10 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates Release.gpg [933 B]         
Get:11 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,227 B]                
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release [40.8 kB]            
Get:13 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports Release.gpg [933 B]       
Get:14 [http://archive.canonical.com](http://archive.canonical.com) raring Release [5,919 B]                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release                                    
Get:15 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-proposed Release.gpg [933 B]        
Get:16 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [764 B]                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main amd64 Packages                        
Get:17 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [762 B]                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring Release                                
Get:18 [http://archive.canonical.com](http://archive.canonical.com) raring/partner amd64 Packages [3,098 B]    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages                         
Get:19 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates Release [40.8 kB]           
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main amd64 Packages [123 kB] 
Get:21 [http://archive.canonical.com](http://archive.canonical.com) raring/partner i386 Packages [4,279 B]     
Get:22 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports Release [40.8 kB]         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IN                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IN                         
Get:23 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-proposed Release [40.8 kB]          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                         
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted amd64 Packages [14 B]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe amd64 Packages [39.3 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en_IN                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/main amd64 Packages                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/restricted amd64 Packages              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/universe amd64 Packages                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en_GB                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/multiverse amd64 Packages              
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en_IN              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/main i386 Packages            
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse amd64 Packages [3,715 B]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/restricted i386 Packages               
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en                 
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main i386 Packages [122 kB]  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/universe i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en_GB              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/multiverse i386 Packages               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/main Translation-en                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/main Translation-en_GB                 
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted i386 Packages [14 B]
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe i386 Packages [39.8 kB]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/multiverse Translation-en              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/multiverse Translation-en_GB           
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse i386 Packages [3,864 B]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/restricted Translation-en              
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en [63.3 kB]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/restricted Translation-en_GB           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/universe Translation-en                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/universe Translation-en_GB             
Get:32 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/main amd64 Packages [193 kB]
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en [1,826 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en       
Get:34 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/restricted amd64 Packages [14 B]
Get:35 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en [24.4 kB]
Get:36 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/universe amd64 Packages [150 kB]
Get:37 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/multiverse amd64 Packages [3,715 B]
Get:38 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/main i386 Packages [191 kB] 
Get:39 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/restricted i386 Packages [14 B]
Get:40 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/universe i386 Packages [151 kB]
Get:41 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/multiverse i386 Packages [3,864 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en_IN          
Get:42 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/main Translation-en [90.8 kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en_GB          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en_IN    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en_IN    
Get:43 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/multiverse Translation-en [1,826 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en_IN      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en_GB      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/restricted Translation-en      
Get:44 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/universe Translation-en [77.4 kB]
Get:45 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/main amd64 Packages [565 B]
Get:46 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/restricted amd64 Packages [14 B]
Get:47 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/universe amd64 Packages [6,946 B]
Get:48 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/multiverse amd64 Packages [1,357 B]
Get:49 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/main i386 Packages [565 B]
Get:50 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/restricted i386 Packages [14 B]
Get:51 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/universe i386 Packages [6,929 B]
Get:52 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/multiverse i386 Packages [1,345 B]
Get:53 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/main Translation-en [269 B]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/multiverse Translation-en    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/restricted Translation-en    
Get:54 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/universe Translation-en [5,313 B]
Get:55 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-proposed/restricted amd64 Packages [14 B]
Get:56 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-proposed/main amd64 Packages [69.2 kB]
Get:57 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-proposed/multiverse amd64 Packages [14 B]
Get:58 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-proposed/universe amd64 Packages [39.1 kB]
Get:59 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-proposed/restricted i386 Packages [14 B]
Get:60 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-proposed/main i386 Packages [67.6 kB]
Get:61 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-proposed/multiverse i386 Packages [14 B]
Get:62 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-proposed/universe i386 Packages [39.4 kB]
Get:63 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-proposed/main Translation-en [31.7 kB]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-proposed/main Translation-en_GB        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-proposed/multiverse Translation-en     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-proposed/multiverse Translation-en_GB  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-proposed/restricted Translation-en     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-proposed/restricted Translation-en_GB  
Get:64 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-proposed/universe Translation-en [16.8 kB]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-proposed/universe Translation-en_GB    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/main Translation-en_IN                 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/main Translation-en_GB
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/multiverse Translation-en_GB
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/restricted Translation-en_GB
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/universe Translation-en_GB
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/main Translation-en_GB
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/multiverse Translation-en_GB
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/restricted Translation-en_GB
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/universe Translation-en_GB
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-proposed/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-proposed/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-proposed/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-proposed/universe Translation-en_IN
Fetched 1,759 kB in 1min 21s (21.5 kB/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_raring_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.[/I]
```

Since I am a novice to this operating system I appreciate if you could guide me step by step. Thank you in advance for your time.

---

### Post by maxxmenon on 2013-10-18
Is there anyone who could help please? I am unable to update anything for now.  I did read similar threads by other members but could not understand what need to be done. 

The only command I knew was the sudo apt-get update....but I am guessing that is not helping. 

I thought this forum had helpful people :shock:

---

### Post by markbl on 2013-10-18
Try this. It won't hurt anything:
```

sudo rm -rf /var/cache/apt/archives /var/lib/apt/lists
sudo apt-get update

```
Be careful to type or copy/paste that first command exactly.

---

### Post by maxxmenon on 2013-10-18
> **markbl said:**
> Try this. It won't hurt anything:
```

sudo rm -rf /var/cache/apt/archives /var/lib/apt/lists
sudo apt-get update

```
Be careful to type or copy/paste that first command exactly.

Thank you markbl for your kind reply. 

When I hit the first command in the terminal I did not get any thing on the $ prompt. And on hitting the second command I got a list of update that automatically took place (I am assuming). 

It did not send any "Failed" status though. Does that mean its all successful as I do not any longer see the red round icon with a minus sign (which probably indicated there are errors) to the right of my window?

If it means all successful then Yay! Glad to have your assistance. :) Thank you.

---

### Post by markbl on 2013-10-18
Yes, it seems all ok now. Run the software updater manually to see and install any pending updates.

---

### Post by maxxmenon on 2013-10-18
> **markbl said:**
> Yes, it seems all ok now. Run the software updater manually to see and install and pending updates.

This is awesome Sir. All seems good now. The updater has automatically suggested updates and I am right now having my Ubuntu updated. Is there a way to give you a 'Karma' point for this? :)

---

### Post by Jack Yan on 2013-12-20
I think my problem is related and I’m in a similar boat to Maxxmenon in being a novice.

The error is the same:

[IMG]https://31.media.tumblr.com/941206b574ec65f808418f356026e16a/tumblr_my4jh2d6Xb1qz7fwgo1_1280.png[/IMG]

and here is what appears in the update window after I try Markbl’s kind suggestion:

```
jackyan@ubuntu:~$ sudo rm -rf /var/cache/apt/archives /var/lib/apt/lists
[sudo] password for jackyan: 
jackyan@ubuntu:~$ sudo apt-get update
Get:1 http://us.archive.ubuntu.com raring Release.gpg [933 B]
Get:2 http://security.ubuntu.com raring-security Release.gpg [933 B]           
Get:3 http://archive.canonical.com raring Release.gpg [933 B]                  
Get:4 http://us.archive.ubuntu.com raring-updates Release.gpg [933 B]          
Get:5 http://security.ubuntu.com raring-security Release [40.8 kB]             
Get:6 http://us.archive.ubuntu.com raring Release [40.8 kB]                   
Get:7 http://archive.canonical.com raring Release [5,919 B]                    
Get:8 http://security.ubuntu.com raring-security/main Sources [55.1 kB]        
Get:9 http://us.archive.ubuntu.com raring-updates Release [40.8 kB]           
Get:10 http://archive.canonical.com raring/partner amd64 Packages [3,105 B]    
Get:11 http://us.archive.ubuntu.com raring/main Sources [963 kB]               
Get:12 http://archive.canonical.com raring/partner i386 Packages [4,256 B]     
Get:13 http://security.ubuntu.com raring-security/restricted Sources [14 B]    
Get:14 http://security.ubuntu.com raring-security/universe Sources [12.9 kB]   
Get:15 http://security.ubuntu.com raring-security/multiverse Sources [2,272 B] 
Get:16 http://security.ubuntu.com raring-security/main amd64 Packages [149 kB] 
Get:17 http://us.archive.ubuntu.com raring/restricted Sources [5,987 B]        
Get:18 http://us.archive.ubuntu.com raring/universe Sources [5,838 kB]         
Get:19 http://security.ubuntu.com raring-security/restricted amd64 Packages [14 B]
Get:20 http://security.ubuntu.com raring-security/universe amd64 Packages [48.6 kB]
Get:21 http://security.ubuntu.com raring-security/multiverse amd64 Packages [3,701 B]
Get:22 http://security.ubuntu.com raring-security/main i386 Packages [148 kB]  
Ign http://archive.canonical.com raring/partner Translation-en_US              
Ign http://archive.canonical.com raring/partner Translation-en                 
Get:23 http://security.ubuntu.com raring-security/restricted i386 Packages [14 B]
Get:24 http://security.ubuntu.com raring-security/universe i386 Packages [49.3 kB]
Get:25 http://security.ubuntu.com raring-security/multiverse i386 Packages [3,862 B]
Get:26 http://us.archive.ubuntu.com raring/multiverse Sources [171 kB]         
Get:27 http://us.archive.ubuntu.com raring/main amd64 Packages [1,170 kB]      
Get:28 http://security.ubuntu.com raring-security/main Translation-en [74.6 kB]
Get:29 http://us.archive.ubuntu.com raring/restricted amd64 Packages [9,636 B] 
Get:30 http://security.ubuntu.com raring-security/multiverse Translation-en [1,826 B]
Get:31 http://us.archive.ubuntu.com raring/universe amd64 Packages [5,396 kB]  
Get:32 http://security.ubuntu.com raring-security/restricted Translation-en [14 B]
Get:33 http://security.ubuntu.com raring-security/universe Translation-en [30.1 kB]
Get:34 http://us.archive.ubuntu.com raring/multiverse amd64 Packages [130 kB]  
Get:35 http://us.archive.ubuntu.com raring/main i386 Packages [1,168 kB]       
Ign http://security.ubuntu.com raring-security/main Translation-en_US          
Get:36 http://us.archive.ubuntu.com raring/restricted i386 Packages [9,623 B]  
Ign http://security.ubuntu.com raring-security/multiverse Translation-en_US    
Ign http://security.ubuntu.com raring-security/restricted Translation-en_US    
Get:37 http://us.archive.ubuntu.com raring/universe i386 Packages [5,405 kB]   
Ign http://security.ubuntu.com raring-security/universe Translation-en_US      
Get:38 http://us.archive.ubuntu.com raring/multiverse i386 Packages [131 kB]   
Get:39 http://us.archive.ubuntu.com raring/main Translation-en [673 kB]        
Get:40 http://us.archive.ubuntu.com raring/multiverse Translation-en [98.4 kB] 
Get:41 http://us.archive.ubuntu.com raring/restricted Translation-en [2,767 B] 
Get:42 http://us.archive.ubuntu.com raring/universe Translation-en [3,736 kB]  
Get:43 http://us.archive.ubuntu.com raring-updates/main Sources [85.1 kB]      
Get:44 http://us.archive.ubuntu.com raring-updates/restricted Sources [14 B]   
Get:45 http://us.archive.ubuntu.com raring-updates/universe Sources [81.2 kB]  
Get:46 http://us.archive.ubuntu.com raring-updates/multiverse Sources [2,791 B]
Get:47 http://us.archive.ubuntu.com raring-updates/main amd64 Packages [213 kB]
Get:48 http://us.archive.ubuntu.com raring-updates/restricted amd64 Packages [14 B]
Get:49 http://us.archive.ubuntu.com raring-updates/universe amd64 Packages [164 kB]
Get:50 http://us.archive.ubuntu.com raring-updates/multiverse amd64 Packages [4,616 B]
Get:51 http://us.archive.ubuntu.com raring-updates/main i386 Packages [211 kB] 
Get:52 http://us.archive.ubuntu.com raring-updates/restricted i386 Packages [14 B]
Get:53 http://us.archive.ubuntu.com raring-updates/universe i386 Packages [165 kB]
Get:54 http://us.archive.ubuntu.com raring-updates/multiverse i386 Packages [4,796 B]
Get:55 http://us.archive.ubuntu.com raring-updates/main Translation-en [102 kB]
Get:56 http://us.archive.ubuntu.com raring-updates/multiverse Translation-en [2,212 B]
Get:57 http://us.archive.ubuntu.com raring-updates/restricted Translation-en [14 B]
Get:58 http://us.archive.ubuntu.com raring-updates/universe Translation-en [83.7 kB]
Ign http://us.archive.ubuntu.com raring/main Translation-en_US                 
Ign http://us.archive.ubuntu.com raring/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com raring/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com raring/universe Translation-en_US             
Ign http://us.archive.ubuntu.com raring-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com raring-updates/multiverse Translation-en_US   
Ign http://us.archive.ubuntu.com raring-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com raring-updates/universe Translation-en_US     
Fetched 26.7 MB in 34s (784 kB/s)                                              
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_raring_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
jackyan@ubuntu:~$ 


```

Can anyone assist, please? I’m happy to start a new thread if it’s considered a different enough error.

---

### Post by Jack Yan on 2013-12-20
An update: I went to [http://askubuntu.com/questions/30072/how-do-i-fix-a-problem-with-mergelist-or-status-file-could-not-be-parsed-err](http://askubuntu.com/questions/30072/how-do-i-fix-a-problem-with-mergelist-or-status-file-could-not-be-parsed-err) and tried the last suggestion on the page by [Braiam]("http://askubuntu.com/users/169736/braiam"). That seems to have removed the error.

---

### Post by cdoebbler on 2014-01-26
I get the same error message, but the fix you suggested does not seem to work. Instead the result of the apt-get update command is:

E: Malformed line 38 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.

Also when I open sources.lst in gedit it is blank?

Any suggestions very welcome? Thanks in advance.

---

### Post by jeanjd63 on 2014-01-26
Hello

**sudo  gedit  /etc/apt/sources.list**

---

### Post by deadflowr on 2014-01-26
> **cdoebbler said:**
> 
Also when I open sources.lst in gedit it is blank?

Any suggestions very welcome? Thanks in advance.


Follow this to the letter
```
gksu gedit /etc/apt/sources.list
```
your out put should look like this
```
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


deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main



```

Good luck

Edit: Chances are if using a newer version of Ubuntu, then gksu isn't installed and/or needs to be set as sudo authentication.
If not installed try
```
sudo apt-get install gksu
```
if authentication isn't set right, run
```
gksu-properties
```
and set the authentication to sudo.

Or run sudo with the terminal editor
```
sudo nano /etc/apt/sources.list
```

---

