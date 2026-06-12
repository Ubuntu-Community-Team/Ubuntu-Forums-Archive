---
title: "Suddenly everyday massive updates"
date: 2018-02-07
forum: General Help
---

### Post by bulgin on 2018-02-07
So today is Wed. Feb. 7, 2018.

Everyday for the past week I've been receiving these massive updates to Ubuntu 16.04.

They would appear to be different in content.

Has there been a big push lately to upgrade Ubuntu like I've never seen before, or is my 'puter fritzing out?

Thank you.

---

### Post by coffeecat on 2018-02-07
I've moved this thread to ***General Help*** because "Upgrades" in the title of the Installation & Upgrades sub-forum properly refers to upgrading from one release to the next. Don't worry - "upgrades" is an ambiguous word in this context.

Running 16.04 here too. There have been quite a few updates recently, but nothing I would think of as out of the ordinary. Perhaps you have some 3rd party sources that have had a lot of updates recently. Run this terminal command and post the output:

```
sudo apt update
```

That will show us all your sources. Please post the output between BBCode [noparse]```
 and 
```[/noparse] tags for readability. There's a link in my sig if you are not sure how to do this.

---

### Post by TheFu on 2018-02-07
If you can please provide more facts, perhaps someone could help?

---

### Post by vasa1 on 2018-02-07
You could upload the contents of */var/log/apt/history.log* using pastebinit and post the link here:```
pastebinit /var/log/apt/history.log
```

---

### Post by bulgin on 2018-02-08
Thanks for help peeps!
Just and FYI I regularly run bleachbit upon shutdown.


```

sudo apt-get update
Get:1 http://archive.canonical.com/ubuntu xenial InRelease [11.5 kB]
Get:2 http://archive.ubuntu.com/ubuntu xenial InRelease [247 kB]                                                                                                                                             
Get:3 http://ppa.launchpad.net/gezakovacs/ppa/ubuntu xenial InRelease [17.5 kB]                                                                                                                              
Ign:5 http://dl.google.com/linux/chrome/deb stable InRelease                                                                                                                                                 
Get:6 http://packages.ivideon.com/ubuntu stable InRelease [4,047 B]                                                                                                                                          
Get:4 http://screenshots.getdeb.net xenial-getdeb InRelease [9,604 B]                                                                                                                                        
Get:7 http://dl.google.com/linux/chrome/deb stable Release [1,189 B]                                                                                                             
Get:8 http://ppa.launchpad.net/ondrej/php/ubuntu xenial InRelease [23.9 kB]                                                               
Get:9 http://archive.canonical.com/ubuntu xenial/partner Sources [2,384 B]                                                                                       
Get:10 http://dl.google.com/linux/chrome/deb stable Release.gpg [819 B]                                                                                                    
Get:11 http://archive.canonical.com/ubuntu xenial/partner amd64 Packages [3,128 B]                                                                               
Get:12 http://archive.canonical.com/ubuntu xenial/partner i386 Packages [3,124 B]                                                                      
Get:13 http://archive.canonical.com/ubuntu xenial/partner Translation-en [1,616 B]                                                                      
Get:14 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]                                                                               
Get:15 http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu xenial InRelease [17.6 kB]                                                            
Get:16 https://repo.skype.com/deb stable InRelease [4,486 B]                                                                                                          
Get:18 http://packages.ivideon.com/ubuntu stable/non-free amd64 Packages [1,660 B]                                                                                                                         
Get:17 http://screenshots.getdeb.net xenial-getdeb/apps amd64 Packages [66.7 kB]                                                                                                                             
Get:19 http://dl.google.com/linux/chrome/deb stable/main amd64 Packages [1,373 B]                                                                                                                            
Ign:20 http://repo.vivaldi.com/stable/deb stable InRelease                                                                                                                                                   
Get:21 http://repo.vivaldi.com/stable/deb stable Release [3,829 B]                                                                                                                                     
Get:22 http://archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]                                                                                                                                  
Get:24 http://repo.vivaldi.com/stable/deb stable Release.gpg [819 B]                                                                               
Get:25 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial InRelease [17.5 kB]                                                                    
Get:26 http://packages.ivideon.com/ubuntu stable/non-free i386 Packages [1,666 B]                                                              
Get:27 https://repo.skype.com/deb stable/main amd64 Packages [2,251 B]                                                                         
Get:23 http://screenshots.getdeb.net xenial-getdeb/apps i386 Packages [67.4 kB]                                                                                                   
Get:28 http://archive.ubuntu.com/ubuntu xenial-security InRelease [102 kB]                                                                      
Get:29 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages [1,201 kB]                                      
Get:30 http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu xenial InRelease [17.5 kB]                           
Get:31 http://repo.vivaldi.com/stable/deb stable/main amd64 Packages [3,479 B]                                         
Get:32 http://repo.vivaldi.com/stable/deb stable/main i386 Packages [3,490 B]                                                 
Get:33 http://ppa.launchpad.net/gezakovacs/ppa/ubuntu xenial/main amd64 Packages [796 B]                                       
Get:34 https://dl.ring.cx/ring-nightly/ubuntu_16.04 ring InRelease [2,177 B]                                                             
Get:35 http://ppa.launchpad.net/gezakovacs/ppa/ubuntu xenial/main i386 Packages [792 B] 
Get:36 http://ppa.launchpad.net/gezakovacs/ppa/ubuntu xenial/main Translation-en [436 B]                                                         
Get:37 https://dl.ring.cx/ring-nightly/ubuntu_16.04 ring/main amd64 Packages [1,343 B]                              
Get:38 http://ppa.launchpad.net/ondrej/php/ubuntu xenial/main amd64 Packages [45.5 kB]  
Get:39 http://archive.ubuntu.com/ubuntu xenial/main i386 Packages [1,196 kB]
Get:40 https://dl.ring.cx/ring-nightly/ubuntu_16.04 ring/main i386 Packages [1,345 B]                         
Get:41 http://ppa.launchpad.net/ondrej/php/ubuntu xenial/main i386 Packages [45.3 kB]                                                      
Get:42 http://ppa.launchpad.net/ondrej/php/ubuntu xenial/main Translation-en [26.3 kB]                        
Get:43 http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu xenial/main amd64 Packages [936 B]               
Get:44 http://archive.ubuntu.com/ubuntu xenial/main Translation-en [568 kB]                                     
Get:45 http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu xenial/main i386 Packages [952 B]
Get:46 http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu xenial/main Translation-en [460 B]              
Get:47 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial/main amd64 Packages [20.0 kB]                               
Get:48 http://archive.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata [733 kB]                                
Get:49 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial/main i386 Packages [20.0 kB]       
Get:50 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial/main Translation-en [5,796 B]                           
Get:51 http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu xenial/main amd64 Packages [26.0 kB]
Get:52 http://archive.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons [409 kB]                                     
Get:53 http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu xenial/main i386 Packages [26.0 kB]                      
Get:54 http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu xenial/main Translation-en [9,928 B]             
Get:55 http://archive.ubuntu.com/ubuntu xenial/restricted amd64 Packages [8,344 B]     
Get:56 http://archive.ubuntu.com/ubuntu xenial/restricted i386 Packages [8,684 B]
Get:57 http://archive.ubuntu.com/ubuntu xenial/restricted Translation-en [2,908 B]
Get:58 http://archive.ubuntu.com/ubuntu xenial/restricted amd64 DEP-11 Metadata [186 B]
Get:59 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages [7,532 kB]
Get:60 http://archive.ubuntu.com/ubuntu xenial/universe i386 Packages [7,512 kB]                                                                                                                             
Get:61 http://archive.ubuntu.com/ubuntu xenial/universe Translation-en [4,354 kB]                                                                                                                            
Get:62 http://archive.ubuntu.com/ubuntu xenial/universe amd64 DEP-11 Metadata [3,410 kB]                                                                                                                     
Get:63 http://archive.ubuntu.com/ubuntu xenial/universe DEP-11 64x64 Icons [7,448 kB]                                                                                                                        
Get:64 http://archive.ubuntu.com/ubuntu xenial/multiverse amd64 Packages [144 kB]                                                                                                                            
Get:65 http://archive.ubuntu.com/ubuntu xenial/multiverse i386 Packages [140 kB]                                                                                                                             
Get:66 http://archive.ubuntu.com/ubuntu xenial/multiverse Translation-en [106 kB]                                                                                                                            
Get:67 http://archive.ubuntu.com/ubuntu xenial/multiverse amd64 DEP-11 Metadata [63.8 kB]                                                                                                                    
Get:68 http://archive.ubuntu.com/ubuntu xenial/multiverse DEP-11 64x64 Icons [230 kB]                                                                                                                        
Get:69 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [715 kB]                                                                                                                          
Get:70 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [664 kB]                                                                                                                           
Get:71 http://archive.ubuntu.com/ubuntu xenial-updates/main Translation-en [297 kB]                                                                                                                          
Get:72 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [307 kB]                                                                                                                   
Get:73 http://archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [222 kB]                                                                                                                      
Get:74 http://archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 Packages [7,560 B]                                                                                                                   
Get:75 http://archive.ubuntu.com/ubuntu xenial-updates/restricted i386 Packages [7,524 B]                                                                                                                    
Get:76 http://archive.ubuntu.com/ubuntu xenial-updates/restricted Translation-en [2,272 B]                                                                                                                   
Get:77 http://archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 DEP-11 Metadata [157 B]                                                                                                              
Get:78 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [582 kB]                                                                                                                      
Get:79 http://archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [539 kB]                                                                                                                       
Get:80 http://archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en [235 kB]                                                                                                                      
Get:81 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [191 kB]                                                                                                               
Get:82 http://archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [272 kB]                                                                                                                  
Get:83 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 Packages [16.2 kB]                                                                                                                   
Get:84 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse i386 Packages [15.3 kB]                                                                                                                    
Get:85 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse Translation-en [8,052 B]                                                                                                                   
Get:86 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [5,892 B]                                                                                                            
Get:87 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse DEP-11 64x64 Icons [14.3 kB]                                                                                                               
Get:88 http://archive.ubuntu.com/ubuntu xenial-backports/main amd64 Packages [4,836 B]                                                                                                                       
Get:89 http://archive.ubuntu.com/ubuntu xenial-backports/main i386 Packages [4,840 B]                                                                                                                        
Get:90 http://archive.ubuntu.com/ubuntu xenial-backports/main Translation-en [3,220 B]                                                                                                                       
Get:91 http://archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3,328 B]                                                                                                                
Get:92 http://archive.ubuntu.com/ubuntu xenial-backports/main DEP-11 64x64 Icons [29 B]                                                                                                                      
Get:93 http://archive.ubuntu.com/ubuntu xenial-backports/restricted amd64 DEP-11 Metadata [194 B]                                                                                                            
Get:94 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64 DEP-11 Metadata [216 B]                                                                                                            
Get:95 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse DEP-11 64x64 Icons [29 B]                                                                                                                
Get:96 http://archive.ubuntu.com/ubuntu xenial-backports/universe amd64 Packages [6,628 B]                                                                                                                   
Get:97 http://archive.ubuntu.com/ubuntu xenial-backports/universe i386 Packages [6,612 B]                                                                                                                    
Get:98 http://archive.ubuntu.com/ubuntu xenial-backports/universe Translation-en [3,768 B]                                                                                                                   
Get:99 http://archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [4,700 B]                                                                                                            
Get:100 http://archive.ubuntu.com/ubuntu xenial-backports/universe DEP-11 64x64 Icons [2,717 B]                                                                                                              
Get:101 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 Packages [436 kB]                                                                                                                        
Get:102 http://archive.ubuntu.com/ubuntu xenial-security/main i386 Packages [392 kB]                                                                                                                         
Get:103 http://archive.ubuntu.com/ubuntu xenial-security/main Translation-en [189 kB]                                                                                                                        
Get:104 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [62.7 kB]                                                                                                                
Get:105 http://archive.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [68.6 kB]                                                                                                                   
Get:106 http://archive.ubuntu.com/ubuntu xenial-security/restricted amd64 Packages [7,224 B]                                                                                                                 
Get:107 http://archive.ubuntu.com/ubuntu xenial-security/restricted i386 Packages [7,224 B]                                                                                                                  
Get:108 http://archive.ubuntu.com/ubuntu xenial-security/restricted Translation-en [2,152 B]                                                                                                                 
Get:109 http://archive.ubuntu.com/ubuntu xenial-security/restricted amd64 DEP-11 Metadata [200 B]                                                                                                            
Get:110 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 Packages [201 kB]                                                                                                                    
Get:111 http://archive.ubuntu.com/ubuntu xenial-security/universe i386 Packages [162 kB]                                                                                                                     
Get:112 http://archive.ubuntu.com/ubuntu xenial-security/universe Translation-en [102 kB]                                                                                                                    
Get:113 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [51.4 kB]                                                                                                            
Get:114 http://archive.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [85.1 kB]                                                                                                               
Get:115 http://archive.ubuntu.com/ubuntu xenial-security/multiverse amd64 Packages [3,208 B]                                                                                                                 
Get:116 http://archive.ubuntu.com/ubuntu xenial-security/multiverse i386 Packages [3,376 B]                                                                                                                  
Get:117 http://archive.ubuntu.com/ubuntu xenial-security/multiverse Translation-en [1,408 B]                                                                                                                 
Get:118 http://archive.ubuntu.com/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata [212 B]                                                                                                            
Get:119 http://archive.ubuntu.com/ubuntu xenial-security/multiverse DEP-11 64x64 Icons [29 B]                                                                                                                
Fetched 42.1 MB in 49s (854 kB/s)                                                                                                                                                                            
Reading package lists... Done

```

link to pastebin from [COLOR=#000000][FONT=&quot]/var/log/apt/history.log[/FONT][/COLOR]

[https://pastebin.com/J1yp0zyW](https://pastebin.com/J1yp0zyW)

---

### Post by TheFu on 2018-02-08
Those downloads are just getting the new repo files. Doesn't mean everything in there will be updated at all.  You have to run **sudo apt upgrade** to see what will be upgraded.

edit: fixed update/upgrade in bold. Sorry.

---

### Post by bulgin on 2018-02-08
it is synaptic that everyday does massive updates.  Here is sudo apt udpate:

```
sudo apt update
[sudo] password for xx: 
Hit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease
Hit:2 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease                              
Ign:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:4 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Hit:5 [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) xenial InRelease          
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]       
Hit:7 [https://dl.ring.cx/ring-nightly/ubuntu_16.04](https://dl.ring.cx/ring-nightly/ubuntu_16.04) ring InRelease              
Ign:9 [http://repo.vivaldi.com/stable/deb](http://repo.vivaldi.com/stable/deb) stable InRelease                      
Get:10 [http://packages.ivideon.com/ubuntu](http://packages.ivideon.com/ubuntu) stable InRelease [4,047 B]           
Hit:11 [http://repo.vivaldi.com/stable/deb](http://repo.vivaldi.com/stable/deb) stable Release                       
Hit:12 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                    
Hit:13 [http://ppa.launchpad.net/ondrej/php/ubuntu](http://ppa.launchpad.net/ondrej/php/ubuntu) xenial InRelease             
Hit:8 [http://screenshots.getdeb.net](http://screenshots.getdeb.net) xenial-getdeb InRelease                    
Hit:14 [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) xenial InRelease
Get:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]
Get:18 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]     
Get:19 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [307 kB]
Get:20 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [222 kB]
Get:21 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [190 kB]
Get:22 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [270 kB]
Get:23 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata [5,892 B]
Get:24 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata [3,328 B]
Get:25 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 DEP-11 Metadata [4,696 B]
Get:26 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [62.7 kB]
Get:27 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [71.2 kB]
Get:28 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [51.4 kB]
Get:29 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [80.2 kB]
Hit:30 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) xenial InRelease          
Hit:31 [http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu](http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu) xenial InRelease 
Fetched 1,579 kB in 2s (762 kB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
6 packages can be upgraded. Run 'apt list --upgradable' to see them.
```

---

### Post by QIII on 2018-02-08
Synaptic is a front-end for apt. 

In the terminal, "update" does not make changes to your system beyond updating the database of the "table of contents" of what's available in the repo(s).  That is entirely different from downloading and replacing/upgrading the packages themselves.

"dist-upgrade" does that.

You have a lot of third-party repos there.  Canonical does not control, nor are they responsible for, their contents.

By what metric have you determined that the work being done by synaptic is any more "massive" than what happens in the terminal?

---

### Post by bulgin on 2018-02-08
Hello and thanks.  Understood.

I don't really know that they are different, but every morning when I turn on the machine the GUI updater (package updater? Synaptic updater?  What exactly would you call that?) comes up and asks if I want to download a bunch of files for updating.  This all started about 10 days ago and every single morning the updates continue.

I understand that Canonical does not control these updates - but I'm just surprised that a LOT of updates have started recently whereas in the past maybe only every couple of weeks.

I thought that maybe there was some major upgrade to Ubuntu but I've heard that is NOT the case. 

So I just don't know. . . I once read somewhere not to do a distribution upgrade as it could break some third party addons.


As a side noteFYI: I've asked for updates to this thread in my settings but I never get them. I need to check in frequently to see if there are any responses.
So what is the exact difference between sudo apt-get upgrade vs. dist-upgrade"?

---

### Post by deadflowr on 2018-02-08
With all the 3rd party repos and PPAs you have I'd be more surprised that this is a new thing. I would have thought you'd have been getting a lot of updates all the time.
Also it seems you have both the xbmc and xbmc-nightly-build PPAs, question: Why? Seems moot to have the xbmc ppa if you also have the nightly build ppa.
> So what is the exact difference between sudo apt-get upgrade vs. dist-upgrade"?

apt-get upgrade only installs updates for packages already on the machine, and will not install any new packages.
apt-get dist-upgrade will install new packages, if the new packages are require to satisfy the needs of a package that will be upgraded.

---

### Post by TheFu on 2018-02-09
The difference between upgrade and dist-upgrade is clearly spelled out in the manpage for apt-get.  Very worth reading to gain an understanding.

I don't patch daily. Getting updates that often disrupts my workflow.  Weekly is when I do it.

As deadflowr noticed, having both nightly and stable PPA for the same project is a bad idea.  Nightly is just that - nightly.  That alone would be why you see updates all the time.  If you aren't on that project team or a tester for them, I wouldn't use any nightly packages.  With Kodi, I find that being at least a few weeks behind their updates helps with having a more stable system.

---

### Post by bulgin on 2018-02-09
Great!  This is very helpful and informative.  Thanks all!

How do I get rid of the nightly builds - I think you may have hit upon something.

Thanks again for the excellent support.

Again, why am I not being notified of posts to this thread even though I have subscribed to it?

Further note if this helps:

apt-cache policy xbmc
xbmc:
  Installed: (none)
  Candidate: 2:16.1~git20160425.1001-final-0xenial
  Version table:
     2:16.1~git20160425.1001-final-0xenial 500
        500 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) xenial/main amd64 Packages
        500 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) xenial/main i386 Packages

---

### Post by TheFu on 2018-02-09
Notification settings are in your profile.

Look in /etc/apt/sources.d/ for the PPA file that grabs nightly stuff.  They are safe to view.  Remove it. Then do an apt update ; apt upgrade (or dist-upgrade) as you like.

Why use xbmc anymore.  Kodi replaced it over 2 yrs ago.  On a 16.04 system:

```
$ apt-cache policy kodi
kodi:
  Installed: 15.2+dfsg1-3ubuntu1.1
  Candidate: 15.2+dfsg1-3ubuntu1.1
  Version table:
 *** 15.2+dfsg1-3ubuntu1.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
        100 /var/lib/dpkg/status
     15.2+dfsg1-3ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages

```

There definitely are newer versions of Kodi ... I use them on raspberry pis daily, but there I use a distro specific to the r-pi called OSMC.  Works well with v2 and v3 Pi hardware.  Due to an addon issue, I've had to drop back to a Kodi/OSMC version from last fall. On an x86 system, running v17 should be relatively safe.

---

### Post by bulgin on 2018-02-09
I would like to totally remove xmbc as I do have kodi installed and it is working.  

My profile shows I am subscribed to this topic, but again, not receiving notifications.

Further to this thread:```

sudo apt-get purge xbmc xbmc-standalone
[sudo] password for xx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'kodi' instead of 'xbmc-standalone'
Package 'xbmc' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
```

---

### Post by QIII on 2018-02-09
@bulgin --

Please start a thread in Forum Feedback and Help for your issue with notifications.

Thanks.

---

### Post by deadflowr on 2018-02-09
> **bulgin said:**
> Further to this thread:```

sudo apt-get purge xbmc xbmc-standalone
[sudo] password for xx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'kodi' instead of 'xbmc-standalone'
Package 'xbmc' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
```

What's the new 13 listed for upgrading:
```
 apt list --upgradable
```

---

