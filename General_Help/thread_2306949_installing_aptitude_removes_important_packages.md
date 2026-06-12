---
title: "installing aptitude removes important packages"
date: 2015-12-20
forum: General Help
---

### Post by Spency on 2015-12-20
```
[COLOR=#333333][FONT=Consolas]:~$ sudo apt-get install aptitude
[/FONT][/COLOR]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-image-3.19.0-25-generic linux-image-extra-3.19.0-25-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  aptitude-common libboost-iostreams1.54.0 libcwidget3 libept1.4.12
Suggested packages:
  aptitude-doc-en aptitude-doc tasksel debtags libcwidget-dev
The following NEW packages will be installed:
  aptitude aptitude-common libboost-iostreams1.54.0 libcwidget3 libept1.4.12
0 upgraded, 5 newly installed, 0 to remove and 1 not upgraded.
Need to get 2,549 kB of archives.
After this operation, 10.7 MB of additional disk space will be used.
Do you want to continue? [Y/n] 

open: 208; closed: 1535; defer: 67; conflict: 92                               
The following actions will resolve these dependencies:

      Remove the following packages:                                            
1)      account-plugin-aim                                                      
2)      account-plugin-facebook                                                 
3)      account-plugin-flickr                                                   
4)      account-plugin-google                                                   
5)      account-plugin-jabber                                                   
6)      account-plugin-salut                                                    
7)      account-plugin-twitter                                                  
8)      account-plugin-yahoo                                                    
9)      appmenu-qt5                                                             
10)     checkbox-gui                                                            
11)     cheese                                                                  
12)     chrome-token-signing                                                    
13)     empathy                                                                 
14)     estonianidcard                                                          
15)     friends-facebook                                                        
16)     friends-twitter                                                         
17)     gir1.2-totem-1.0                                                        
18)     gnome-contacts                                                          
19)     gstreamer1.0-clutter                                                    
20)     hud                                                                     
21)     indicator-bluetooth                                                     
22)     libaccount-plugin-generic-oauth                                         
23)     libaccount-plugin-google                                                
24)     libcheese-gtk23                                                         
25)     libcheese7                                                              
26)     libclutter-1.0-0                                                        
27)     libclutter-gst-2.0-0                                                    
28)     libclutter-gtk-1.0-0                                                    
29)     libcogl-pango15                                                         
30)     libcogl15                                                               
31)     libgbm1                                                                 
32)     liboxideqt-qmlplugin                                                    
33)     liboxideqtcore0                                                         
34)     liboxideqtquick0                                                        
35)     libqt5feedback5                                                         
36)     libqt5gui5                                                              
37)     libqt5multimedia5                                                       
38)     libqt5opengl5                                                           
39)     libqt5printsupport5                                                     
40)     libqt5quick5                                                            
41)     libqt5svg5                                                              
42)     libqt5webkit5                                                           
43)     libqt5webkit5-qmlwebkitplugin                                           
44)     libqt5widgets5                                                          
45)     libtotem0                                                               
46)     libunity-webapps0                                                       
47)     mcp-account-manager-uoa                                                 
48)     nautilus-sendto-empathy                                                 
49)     qdigidoc                                                                
50)     qesteidutil                                                             
51)     qtdeclarative5-accounts-plugin                                          
52)     qtdeclarative5-dialogs-plugin                                           
53)     qtdeclarative5-privatewidgets-plugin                                    
54)     qtdeclarative5-qtfeedback-plugin                                        
55)     qtdeclarative5-qtquick2-plugin                                          
56)     qtdeclarative5-ubuntu-ui-extras-browser-plugin                          
57)     qtdeclarative5-ubuntu-ui-toolkit-plugin                                 
58)     qtdeclarative5-window-plugin                                            
59)     signon-plugin-oauth2                                                    
60)     signon-ui                                                               
61)     totem                                                                   
62)     totem-mozilla                                                           
63)     totem-plugins                                                           
64)     ubuntu-desktop                                                          
65)     **unity-control-center **                                                   
66)     **unity-control-center-signon**                                             
67)     unity-scope-gdrive                                                      
68)     unity-webapps-common                                                    
69)     unity-webapps-qml                                                       
70)     unity-webapps-service                                                   
71)     webaccounts-extension-common                                            
72)     webapp-container                                                        
73)     webbrowser-app                                                          
74)     xul-ext-unity                                                           
75)     xul-ext-webaccounts                                                     
76)     xul-ext-websites-integration                                            

      Keep the following packages at their current version:                     
77)     libegl1-mesa:i386 [Not Installed]                                       
78)     libgbm1:i386 [Not Installed]                                            
79)     libgl1-mesa-dri [Not Installed]                                         
80)     libgl1-mesa-dri:i386 [Not Installed]                                    
81)     libglapi-mesa [Not Installed]                                           
82)     libglapi-mesa:i386 [Not Installed]                                      
83)     libosmesa6 [Not Installed]                                              
84)     libosmesa6:i386 [Not Installed]                                         
85)     wine1.7 [Not Installed]                                                 
86)     wine1.7-amd64 [Not Installed]                                           
87)     wine1.7-i386:i386 [Not Installed]                                       

      Leave the following dependencies unresolved:                              
88)     friends-dispatcher recommends friends-facebook                          
89)     friends-dispatcher recommends friends-twitter                           
90)     indicator-appmenu recommends appmenu-qt5                                
91)     indicator-datetime recommends unity-control-center (>= 14.04.3) | ubuntu
92)     indicator-power recommends unity-control-center | gnome-control-center (
93)     indicator-sound recommends unity-control-center | gnome-control-center |
94)     libaccount-plugin-1.0-0 recommends unity-control-center-signon          
95)     signond recommends signon-ui                                            
96)     ubuntu-desktop recommends cheese                                        
97)     ubuntu-desktop recommends empathy                                       
98)     ubuntu-desktop recommends totem                                         
99)     ubuntu-desktop recommends totem-mozilla                                 
100     unity-lens-files recommends unity-scope-gdrive                          
101     unity-lens-photos recommends account-plugin-flickr                      
102     unity-lens-photos recommends account-plugin-google                      
103     unity-lens-photos recommends account-plugin-facebook                    
104     winetricks recommends wine                                              
105     empathy recommends gnome-contacts                                       
106     gnome-bluetooth recommends unity-control-center | gnome-control-center  
107     indicator-session recommends unity-control-center | gnome-control-center
108     indicator-session recommends unity-control-center-signon | gnome-control
109     libhud2 recommends hud (= 14.04+14.04.20140604-0ubuntu1)                
110     mcp-account-manager-uoa recommends account-plugin-aim                   
111     mcp-account-manager-uoa recommends account-plugin-jabber                
112     mcp-account-manager-uoa recommends account-plugin-google                
113     mcp-account-manager-uoa recommends account-plugin-yahoo                 
114     mcp-account-manager-uoa recommends account-plugin-salut                 
115     unity recommends unity-control-center                                   
116     unity recommends unity-scope-gdrive                                     
117     unity recommends indicator-bluetooth                                    
118     unity recommends hud                                                    
119     gnome-panel recommends unity-control-center                             


Accept this solution? [Y/n/q/?] 
```

I'm running 14.04 off of an 11,2 iMac. How do I install aptitude without it removing things like the unity-control-center and other software I've installed?

---

### Post by CantankRus on 2015-12-20
Aptitude installs fine here.
What is your output from ...
```
sudo apt-get update
```

What ppas are you using...
```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
```

---

### Post by Spency on 2015-12-25
I apologize, I edited out a key piece of information I didn't think was relevant.
The command I ran to produce those results was
```
sudo apt-get install aptitude && sudo aptitude install wine1.7
```


Aptitude installs fine, but when I try to install wine1.7 (more info [here]("https://wiki.ixit.cz/d3d9_tutorial")) using aptitude, aptitude seems to think the install conflicts with many components of ubuntu.

---

### Post by Spency on 2015-12-25
apt-get update output:
```

Ign http://us.archive.ubuntu.com trusty InRelease
Ign http://dl.google.com stable InRelease                                      
Hit http://repository.spotify.com stable InRelease                             
Hit http://dl.google.com stable Release.gpg                                    
Hit http://us.archive.ubuntu.com trusty-updates InRelease                      
Hit http://security.ubuntu.com trusty-security InRelease                       
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://dl.google.com stable Release                                        
Hit http://repository.spotify.com stable/non-free amd64 Packages               
Hit http://us.archive.ubuntu.com trusty-backports InRelease                    
Hit http://security.ubuntu.com trusty-security/main Sources                    
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://repository.spotify.com stable/non-free i386 Packages                
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://installer.id.ee trusty InRelease                                    
Hit http://security.ubuntu.com trusty-security/universe Sources                
Hit http://us.archive.ubuntu.com trusty-updates/main Sources                   
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Hit http://us.archive.ubuntu.com trusty-updates/restricted Sources             
Hit http://installer.id.ee trusty/main amd64 Packages                          
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://us.archive.ubuntu.com trusty-updates/universe Sources               
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Sources             
Hit http://installer.id.ee trusty/main i386 Packages                           
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://us.archive.ubuntu.com trusty-updates/main amd64 Packages            
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Hit http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages      
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages        
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages      
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Hit http://us.archive.ubuntu.com trusty-updates/main i386 Packages             
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://repository.spotify.com stable/non-free Translation-en_US            
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Hit http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages       
Ign http://dl.google.com stable/main Translation-en                            
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Ign http://repository.spotify.com stable/non-free Translation-en               
Hit http://us.archive.ubuntu.com trusty-updates/universe i386 Packages         
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages       
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en        
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Ign http://installer.id.ee trusty/main Translation-en_US                       
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Ign http://installer.id.ee trusty/main Translation-en                          
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Hit http://us.archive.ubuntu.com trusty Release                                
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
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Reading package lists... Done 

```

PPAs
```

/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu trusty-security main restricted
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu trusty-security universe
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu trusty-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu trusty-security multiverse
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
/etc/apt/sources.list:deb http://extras.ubuntu.com/ubuntu trusty main
/etc/apt/sources.list:deb-src http://extras.ubuntu.com/ubuntu trusty main
/etc/apt/sources.list.d/commendsarnex-ixitmaster-trusty.list:deb http://ppa.launchpad.net/commendsarnex/ixitmaster/ubuntu trusty main
/etc/apt/sources.list.d/commendsarnex-winedri3-trusty.list:deb http://ppa.launchpad.net/commendsarnex/winedri3/ubuntu trusty main
/etc/apt/sources.list.d/google-chrome.list:deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/oibaf-graphics-drivers-trusty.list:deb http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu trusty main
/etc/apt/sources.list.d/ria-repository.list:deb http://installer.id.ee/media/ubuntu/ trusty main
/etc/apt/sources.list.d/spotify.list:deb http://repository.spotify.com stable non-free

```

---

### Post by ian-weisser on 2015-12-25
Do you realize that are you volunteering to test an experimental, unsupported software?
Those PPAs are supported *only* by the author, and have nothing to do with the Ubuntu project.

There are easier ways to install wine 1.7. Indeed, the Ubuntu Wine Team has packaged and PPAd 1.8 already for testing.

---

### Post by Spency on 2015-12-25
Yes I do - albeit this is sort of a [well known tweak.]("http://www.webupd8.org/2014/09/how-to-install-world-of-warcraft-in.html")
The authors provide an altered version of wine that takes advantage of their driver tweaking - I'm not interested in the latest version of wine but rather the one that produces the best results.
Strange to say, I've had great success with these drivers using 15.04 and 15.10, but 14.04 seems to cause issues. That said, the issue I'm having [ doesn't seem to be reproducible.]("https://github.com/iXit/Mesa-3D/issues/150") I'm unsure whether this is a hardware issue or whether there is a software solution.

---

### Post by mc4man on 2015-12-26
Did you install  with a 14.04 or 14.04.1 image? (vs. 14.04.2 or 14.04.3 image

---

### Post by Spency on 2015-12-26
Fresh install of 14.04.

---

### Post by mc4man on 2015-12-26
Hard to say without trying on 14.04 with Oibaf ppa enabled which only can be used with 14.04 & 14.04.1 which I don't currently have
Maybe start with most likely blocking package, what's this report?
```
apt-cache policy libgbdm1
```

---

### Post by Spency on 2015-12-27
If I understand you correctly: actually the Oibaf enabled PPA should work with ubuntu 14.04 through 15.10. However, I'm only experiencing this problem on 14.04.
Output:
```
N: Unable to locate package libgbdm1
```

---

### Post by mc4man on 2015-12-27
[SUP][/SUP]> **Spency said:**
> If I understand you correctly: actually the Oibaf enabled PPA should work with ubuntu 14.04 through 15.10. However, I'm only experiencing this problem on 14.04.
Output:
```
N: Unable to locate package libgbdm1
```
Well that makes sense,  don't know how that d snuck in there,  use libgbm1
As far as Oibaf &  trusty,  only 14.04 & 14.04.1 image installs can be used

---

### Post by Spency on 2015-12-27
> **mc4man said:**
> 
Well that makes sense,  don't know how that d snuck in there,  use libgbm1
```
libgbm1:  Installed: 10.1.3-0ubuntu0.5
  Candidate: 11.2+gallium-nine+dri3~git1512240730.41c791~gd~tubuntu1
  Version table:
     11.2+gallium-nine+dri3~git1512240730.41c791~gd~tubuntu1 0
        500 http://ppa.launchpad.net/commendsarnex/ixitmaster/ubuntu/ trusty/main amd64 Packages
     11.2~git1512240730.41c791~gd~t 0
        500 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu/ trusty/main amd64 Packages
 *** 10.1.3-0ubuntu0.5 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     10.1.0-4ubuntu5 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
```

> **mc4man said:**
> 
As far as Oibaf & trusty, only 14.04 & 14.04.1 image installs can be used
Why do you say this?

---

### Post by mc4man on 2015-12-27
> **Spency said:**
> ```
libgbm1:  Installed: 10.1.3-0ubuntu0.5
  Candidate: 11.2+gallium-nine+dri3~git1512240730.41c791~gd~tubuntu1
  Version table:
     11.2+gallium-nine+dri3~git1512240730.41c791~gd~tubuntu1 0
        500 http://ppa.launchpad.net/commendsarnex/ixitmaster/ubuntu/ trusty/main amd64 Packages
     11.2~git1512240730.41c791~gd~t 0
        500 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu/ trusty/main amd64 Packages
 *** 10.1.3-0ubuntu0.5 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     10.1.0-4ubuntu5 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
```


Why do you say this?
Couple of reasons -
It's a fact, 14.04.2 & 14.04.3 use the mesa lts stack, (lts-utopic, lts-vivid, upcoming is lts-wily). These mesa packages do not play well with the ppa.
After giving the ppa maintainer the heads up he added to the page some time ago that warning, if you haven't read the page you should do so before using or try using the ppa.
(- There are more than a few ppa's that one should read that page first before using, this is one, page here - 
[https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

Only the 14.04 & 14.04.1  images from here are usable for oibaf ppa
[http://old-releases.ubuntu.com/releases/14.04.1/](http://old-releases.ubuntu.com/releases/14.04.1/)

---

### Post by Spency on 2015-12-28
I have actually skimmed that same page many times, but never noticed that part on which versions of trusty will and will not work. Thank you for your patience and pointing that out to me!

---

### Post by Spency on 2015-12-28
So you're saying a fresh download of the 14.04 install image is in fact 14.04.3? 
Wouldn't downloading an older image version, and then updating, change the system from 14.04 -> 14.04.3 system?
If yes, it seems impossible to install gallium 9 + wine1.7 under 14.04 without somehow navigating around specific system updates.

---

