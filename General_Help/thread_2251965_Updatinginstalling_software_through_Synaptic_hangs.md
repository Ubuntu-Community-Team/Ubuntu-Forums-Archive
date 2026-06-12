---
title: "Updating/installing software through Synaptic hangs"
date: 2014-11-08
forum: General Help
---

### Post by maslowk on 2014-11-08
I just recently installed Lubuntu 14.04 and I'm having issues using  Synaptic (both from command line and GUI. When using either "apt-get  update" or the Reload button on the GUI it hangs for about 15 minutes  before finishing the process. Here's a screenshot of how far it gets  before hanging; [http://i.imgur.com/pQ1ML0f.png](http://i.imgur.com/pQ1ML0f.png)

I also have this issue when installing anything through synaptic; it hangs for about 15-20 minutes before doing anything at all. Here's a screenshot of that as well; [http://i.imgur.com/Ee7TAc6.png](http://i.imgur.com/Ee7TAc6.png)

I should note that I've had this exact same issue with Lubuntu 14.10 and Xubuntu 14.10 as well. Anyone have any idea what might cause this?

EDIT: I accidentally posted the first screenshot twice, the second one is correct now.

---

### Post by claracc on 2014-11-08
It would be good to know about your sources.list file which is in /etc/apt/ directory, to see if there is any malformed line or inexixtent repository.

Please copy and paste it to here using code tags.

Meanwhile you can try to change the server where the repositories are downloaded from.

---

### Post by maslowk on 2014-11-08
They should still be the default, here's the list though;

```

#deb cdrom:[Lubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main

```

---

### Post by ajgreeny on 2014-11-08
You will get much more info from running the command ```
sudo apt-get update
``` in terminal. 
That will show you in more detail the errors at the bottom of the output and may help us resolve this for you.

---

### Post by maslowk on 2014-11-08
Sorry for the late response. Here's how far the output gets before hanging for the majority of the process time;

```

maslowk@jenkinsgo:~$ sudo apt-get update
[sudo] password for maslowk: 
Ign http://extras.ubuntu.com trusty InRelease
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
62% [Connecting to us.archive.ubuntu.com (2001:67c:1562::14)] [Connecting to se

```

The "[Connecting to se" bit isn't a pasting error; that's just what it shows, and it consistently hangs there. Here's the full output from after it finished;

```

maslowk@jenkinsgo:~$ sudo apt-get update
[sudo] password for maslowk: 
Ign http://extras.ubuntu.com trusty InRelease
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://us.archive.ubuntu.com trusty InRelease                              
Ign http://us.archive.ubuntu.com trusty-updates InRelease                      
Ign http://us.archive.ubuntu.com trusty-backports InRelease     
Hit http://us.archive.ubuntu.com trusty Release.gpg             
Get:1 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg                  
Hit http://us.archive.ubuntu.com trusty Release                                
Get:2 http://us.archive.ubuntu.com trusty-updates Release [62.0 kB]            
Hit http://us.archive.ubuntu.com trusty-backports Release                      
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Get:3 http://us.archive.ubuntu.com trusty-updates/main Sources [136 kB]        
Get:4 http://us.archive.ubuntu.com trusty-updates/restricted Sources [1,408 B] 
Get:5 http://us.archive.ubuntu.com trusty-updates/universe Sources [89.3 kB]   
Get:6 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [3,517 B] 
Get:7 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [356 kB] 
Get:8 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [5,820 B]
Get:9 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [217 kB]
Get:10 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [9,365 B]
Get:11 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [349 kB] 
Get:12 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [5,820 B]
Get:13 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [217 kB]
Get:14 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [9,546 B]
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
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Ign http://security.ubuntu.com trusty-security InRelease                       
Hit http://security.ubuntu.com trusty-security Release.gpg  
Hit http://security.ubuntu.com trusty-security Release
Hit http://security.ubuntu.com trusty-security/main Sources
Hit http://security.ubuntu.com trusty-security/restricted Sources
Hit http://security.ubuntu.com trusty-security/universe Sources
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Fetched 1,463 kB in 14min 3s (1,733 B/s)                                       
Reading package lists... Done

```

Scanning through that I don't see any errors, though as you can see at the bottom it took about 14 minutes to retrieve about 1.4mB of data, which seems rather unusual. I should also mention that it only seems to be Ubuntu-based distros that have this issue on my machine; all other distros using Synaptic work fine in this regard.

EDIT: Just removed an installed program using "apt-get remove --purge" and that didn't have any hanging issues; seems it's just when it has to download data. 
EDIT2: I just added a repository for Google Chrome (after getting the coded logs above), and while installing the app it hung here for a while (but not as long as before) before finishing;

```

The following NEW packages will be installed:
  google-chrome-stable libappindicator1
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 47.7 MB of archives.
After this operation, 182 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
0% [Connecting to us.archive.ubuntu.com (2001:67c:1562::17)] [Connecting to dl.

```

---

### Post by claracc on 2014-11-09
Have you tried to change the server from which you download the software in repositories?, you can do it with update manager, clicking on settings and in the software sources windows selecting other server to download software from, see ikmage attached:

---

### Post by maslowk on 2014-11-09
I'd never noticed that option before, I was able to fix my problem using it though :) thanks for all the help!

In case other users with the same issue happen upon this post, what I did was go "Software Center > Preferences > Open Software Properties > Download from: (Other...) > Select Canada and hit Select Best Server.

Now I'm not too familiar with these forums yet, do I do something to mark the post "solved" or do mods/admins do that?

---

### Post by claracc on 2014-11-10
Glad, you got your problem solved.

Please, mark the thread as solved selecting "thread solved" in the "thread tools" menu in the right upper part of the webpage.

Thanks.

---

