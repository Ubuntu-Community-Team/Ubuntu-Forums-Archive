---
title: "Ubuntu 22.04-LTS : can't reinstall Thunderbird."
date: 2023-08-26
forum: General Help
---

### Post by georgesgiralt on 2023-08-26
HEllo Guys,
I've a strange problem with thunderbird email client. So I decided to reinstall it in order to insure a proper thunderbird installation if I have to ask for help. 
```

~$ sudo apt install --reinstall thunderbird thunderbird-gnome-support thunderbird-locale-en thunderbird-locale-en-gb thunderbird-locale-en-us thunderbird-locale-fr
[sudo] password for georges: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Reinstallation of thunderbird is not possible, it cannot be downloaded.
Reinstallation of thunderbird-gnome-support is not possible, it cannot be downloaded.
Reinstallation of thunderbird-locale-en is not possible, it cannot be downloaded.
Reinstallation of thunderbird-locale-en-gb is not possible, it cannot be downloaded.
Reinstallation of thunderbird-locale-en-us is not possible, it cannot be downloaded.
Reinstallation of thunderbird-locale-fr is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
I do not understand what's happening and I've done the same on another computer running the same 22.04LTS version and it works....
```

menfin:~$ sudo apt install --reinstall thunderbird thunderbird-gnome-support thunderbird-locale-en thunderbird-locale-en-gb thunderbird-locale-en-us thunderbird-locale-fr
[sudo] password for georges: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following package was automatically installed and is no longer required:
  libbotan-2-12
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 6 reinstalled, 0 to remove and 0 not upgraded.
Need to get 64,1 MB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://fr.archive.ubuntu.com/ubuntu jammy-updates/main amd64 thunderbird amd64 1:102.13.0+build1-0ubuntu0.22.04.1 [62,4 MB]
Get:2 http://fr.archive.ubuntu.com/ubuntu jammy-updates/main amd64 thunderbird-gnome-support amd64 1:102.13.0+build1-0ubuntu0.22.04.1 [8&#8239;630 B]
Get:3 http://fr.archive.ubuntu.com/ubuntu jammy-updates/main amd64 thunderbird-locale-en amd64 1:102.13.0+build1-0ubuntu0.22.04.1 [952 kB]
Get:4 http://fr.archive.ubuntu.com/ubuntu jammy-updates/main amd64 thunderbird-locale-en-gb all 1:102.13.0+build1-0ubuntu0.22.04.1 [9&#8239;242 B]
Get:5 http://fr.archive.ubuntu.com/ubuntu jammy-updates/main amd64 thunderbird-locale-en-us all 1:102.13.0+build1-0ubuntu0.22.04.1 [9&#8239;250 B]
Get:6 http://fr.archive.ubuntu.com/ubuntu jammy-updates/main amd64 thunderbird-locale-fr amd64 1:102.13.0+build1-0ubuntu0.22.04.1 [656 kB]
Fetched 64,1 MB in 2s (31,4 MB/s)              
(Reading database ... 337180 files and directories currently installed.)
Preparing to unpack .../0-thunderbird_1%3a102.13.0+build1-0ubuntu0.22.04.1_amd64.deb ...
Unpacking thunderbird (1:102.13.0+build1-0ubuntu0.22.04.1) over (1:102.13.0+build1-0ubuntu0.22.04.1) ...
Preparing to unpack .../1-thunderbird-gnome-support_1%3a102.13.0+build1-0ubuntu0.22.04.1_amd64.deb ...
Unpacking thunderbird-gnome-support (1:102.13.0+build1-0ubuntu0.22.04.1) over (1:102.13.0+build1-0ubuntu0.22.04.1) ...
Preparing to unpack .../2-thunderbird-locale-en_1%3a102.13.0+build1-0ubuntu0.22.04.1_amd64.deb ...
Unpacking thunderbird-locale-en (1:102.13.0+build1-0ubuntu0.22.04.1) over (1:102.13.0+build1-0ubuntu0.22.04.1) ...
Preparing to unpack .../3-thunderbird-locale-en-gb_1%3a102.13.0+build1-0ubuntu0.22.04.1_all.deb ...
Unpacking thunderbird-locale-en-gb (1:102.13.0+build1-0ubuntu0.22.04.1) over (1:102.13.0+build1-0ubuntu0.22.04.1) ...
Preparing to unpack .../4-thunderbird-locale-en-us_1%3a102.13.0+build1-0ubuntu0.22.04.1_all.deb ...
Unpacking thunderbird-locale-en-us (1:102.13.0+build1-0ubuntu0.22.04.1) over (1:102.13.0+build1-0ubuntu0.22.04.1) ...
Preparing to unpack .../5-thunderbird-locale-fr_1%3a102.13.0+build1-0ubuntu0.22.04.1_amd64.deb ...
Unpacking thunderbird-locale-fr (1:102.13.0+build1-0ubuntu0.22.04.1) over (1:102.13.0+build1-0ubuntu0.22.04.1) ...
Setting up thunderbird (1:102.13.0+build1-0ubuntu0.22.04.1) ...
Setting up thunderbird-locale-fr (1:102.13.0+build1-0ubuntu0.22.04.1) ...
Setting up thunderbird-locale-en (1:102.13.0+build1-0ubuntu0.22.04.1) ...
Setting up thunderbird-locale-en-us (1:102.13.0+build1-0ubuntu0.22.04.1) ...
Setting up thunderbird-gnome-support (1:102.13.0+build1-0ubuntu0.22.04.1) ...
Setting up thunderbird-locale-en-gb (1:102.13.0+build1-0ubuntu0.22.04.1) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu3) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.6+22.04.20220217-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
georges@menfin:~$ 

```
Could you help, please ? 
Many thanks in advance for your help.
Have a nice day.

---

### Post by ian-weisser on 2023-08-26
Please show us the complete output of "sudo apt update" on the problem machine.

---

### Post by georgesgiralt on 2023-08-26
Yes Sir :
```

apt update
Hit:1 http://dl.google.com/linux/earth/deb stable InRelease
Hit:2 http://ppa.launchpad.net/apandada1/foliate/ubuntu jammy InRelease                                                                                                                                     
Hit:3 http://fr.archive.ubuntu.com/ubuntu jammy InRelease                                                                                                                                                   
Hit:4 https://dl.google.com/linux/chrome/deb stable InRelease                                                                                                                                               
Hit:5 http://fr.archive.ubuntu.com/ubuntu jammy-updates InRelease                                                                                                                                           
Hit:6 http://ppa.launchpad.net/atareao/atareao/ubuntu jammy InRelease                                                                                                                                       
Hit:7 https://ppa.launchpadcontent.net/dismine/valentina-dev/ubuntu jammy InRelease                                                                                                                         
Hit:8 http://fr.archive.ubuntu.com/ubuntu jammy-backports InRelease                                                                                                                                         
Hit:9 http://ppa.launchpad.net/audio-recorder/ppa/ubuntu jammy InRelease                                                                                                                                    
Get:10 https://mega.nz/linux/repo/xUbuntu_22.04 ./ InRelease [2&#8239;961 B]                                                                                                                                      
Hit:11 https://esm.ubuntu.com/apps/ubuntu jammy-apps-security InRelease                                                                                                                                     
Hit:12 https://esm.ubuntu.com/apps/ubuntu jammy-apps-updates InRelease                                                                                                                                      
Hit:13 https://repo.skype.com/deb stable InRelease                                                                                                                           
Hit:14 https://packages.microsoft.com/repos/edge stable InRelease                                                                                      
Hit:15 https://deb.opera.com/opera-stable stable InRelease                                                      
Hit:16 https://ppa.launchpadcontent.net/heyarje/makemkv-beta/ubuntu jammy InRelease       
Hit:17 https://esm.ubuntu.com/infra/ubuntu jammy-infra-security InRelease
Hit:18 http://security.ubuntu.com/ubuntu jammy-security InRelease
Hit:19 https://esm.ubuntu.com/infra/ubuntu jammy-infra-updates InRelease
Hit:20 https://download.virtualbox.org/virtualbox/debian jammy InRelease
Fetched 2&#8239;961 B in 3s (1&#8239;136 B/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.

```
Thank you !

---

### Post by ian-weisser on 2023-08-26
Withdrawn: My theory was not supported by the output.

---

### Post by georgesgiralt on 2023-08-27
Hello Ian, 
What source do I need ? Because I've checked both source.list files and the only difference is the "cdrom" line. On one computer is specifies "cdrom" but is disabled, and on the culprit the message is a bit different : 
```
# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.

```
And, of course, I used a live USB stick to make the install. 
The functioning machine has been upgraded from many previous versions of Ubuntu (can't remember how many because it's an "old" machine.). So can't find the reason why. 
thanks for your help.

Edit : Add-on : 
```
 
# apt-cache policy thunderbird
thunderbird:
  Installed: 1:102.14.0+build1-0ubuntu0.22.04.1~mt1
  Candidate: 1:102.14.0+build1-0ubuntu0.22.04.1~mt1
  Version table:
 *** 1:102.14.0+build1-0ubuntu0.22.04.1~mt1 100
        100 /var/lib/dpkg/status
     1:102.13.0+build1-0ubuntu0.22.04.1 500
        500 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu jammy-security/main amd64 Packages
     1:91.8.0+build2-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu jammy/main amd64 Packages
# 
```
The 500 error bothers me ... If I'm not mistaken it means that the download demand was misformed. 
So could it be some part of the apt software engine is broken ?
How could I check it and/or  reinstall all of it ? 
I4m more and more puzzled.

---

### Post by ajgreeny on 2023-08-27
Open up **Software and Updates** with command ***software-properties-gtk*** to double check what repos are currently enabled.

You could also try changing the repos to the Main server in the **Download from** box.

I wonder if the French local server may be disabled though it does all appear correctly, and the Main server may work for you.  You could also simply wait for a few minutes and try again without changing the download server locality.

---

### Post by georgesgiralt on 2023-08-27
Hi Ajgreeny,
Before you responded, I tried to start with a clean sources.list file. So removed it and used  software-properties-gtk to recreate it. It then completed to this : 
```

deb http://archive.ubuntu.com/ubuntu jammy         main universe restricted multiverse

deb http://archive.ubuntu.com/ubuntu jammy-updates main universe restricted multiverse


deb http://archive.ubuntu.com/ubuntu jammy-security main universe restricted


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu jammy-backports main restricted universe multiverse
# deb-src http://fr.archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse


# deb cdrom:[Ubuntu 22.04.2 LTS _Jammy Jellyfish_ - Release amd64 (20230223)]/ jammy main restricted

# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.


```
And, I already switched to the main server instead of the French one. 
Alas this changed nothing. 
```

# apt update
Hit:1 http://dl.google.com/linux/earth/deb stable InRelease
Hit:2 http://ppa.launchpad.net/apandada1/foliate/ubuntu jammy InRelease                                                                                                                                     
Hit:3 http://ppa.launchpad.net/atareao/atareao/ubuntu jammy InRelease                                                                                                                                       
Hit:4 https://dl.google.com/linux/chrome/deb stable InRelease                                                                                                                                               
Hit:5 https://download.virtualbox.org/virtualbox/debian jammy InRelease                                                                                                                                     
Hit:6 https://repo.skype.com/deb stable InRelease                                                                                                                                                           
Hit:7 https://deb.opera.com/opera-stable stable InRelease                                                                                                                                                   
Hit:8 http://ppa.launchpad.net/audio-recorder/ppa/ubuntu jammy InRelease                                                                                                                                    
Get:9 https://mega.nz/linux/repo/xUbuntu_22.04 ./ InRelease [2&#8239;961 B]                                                                                                                                       
Hit:10 https://ppa.launchpadcontent.net/dismine/valentina-dev/ubuntu jammy InRelease                                                                                                                 
Hit:11 http://archive.ubuntu.com/ubuntu jammy InRelease                                                                                                                        
Get:12 http://archive.ubuntu.com/ubuntu jammy-updates InRelease [119 kB]                                                                                                       
Hit:13 https://ppa.launchpadcontent.net/heyarje/makemkv-beta/ubuntu jammy InRelease                                                                                                        
Hit:14 https://esm.ubuntu.com/apps/ubuntu jammy-apps-security InRelease                                                                                                                    
Hit:15 https://esm.ubuntu.com/apps/ubuntu jammy-apps-updates InRelease                           
Get:16 http://archive.ubuntu.com/ubuntu jammy-security InRelease [110 kB]            
Hit:17 https://esm.ubuntu.com/infra/ubuntu jammy-infra-security InRelease                         
Hit:18 https://esm.ubuntu.com/infra/ubuntu jammy-infra-updates InRelease                          
Get:19 http://archive.ubuntu.com/ubuntu jammy-backports InRelease [109 kB]
Get:20 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages [894 kB]
Get:21 http://archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages [471 kB]      
Get:22 http://archive.ubuntu.com/ubuntu jammy-updates/main Translation-en [214 kB]
Get:23 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 DEP-11 Metadata [101 kB]              
Get:24 http://archive.ubuntu.com/ubuntu jammy-updates/main DEP-11 48x48 Icons [36,1 kB]                    
Get:25 http://archive.ubuntu.com/ubuntu jammy-updates/main DEP-11 64x64 Icons [55,1 kB]                      
Get:26 http://archive.ubuntu.com/ubuntu jammy-updates/main DEP-11 64x64@2 Icons [29 B]                  
Get:27 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 c-n-f Metadata [15,6 kB]    
Get:28 http://archive.ubuntu.com/ubuntu jammy-updates/universe i386 Packages [651 kB]                          
Get:29 http://archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages [973 kB]                
Get:30 http://archive.ubuntu.com/ubuntu jammy-updates/universe Translation-en [212 kB]            
Get:31 http://archive.ubuntu.com/ubuntu jammy-updates/universe amd64 DEP-11 Metadata [289 kB]           
Get:32 http://archive.ubuntu.com/ubuntu jammy-updates/universe DEP-11 48x48 Icons [196 kB]               
Get:33 http://archive.ubuntu.com/ubuntu jammy-updates/universe DEP-11 64x64 Icons [300 kB]                 
Get:34 http://archive.ubuntu.com/ubuntu jammy-updates/universe DEP-11 64x64@2 Icons [29 B]                
Get:35 http://archive.ubuntu.com/ubuntu jammy-updates/universe amd64 c-n-f Metadata [21,7 kB]
Get:36 http://archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 Packages [714 kB]
Get:37 http://archive.ubuntu.com/ubuntu jammy-updates/restricted i386 Packages [30,3 kB]               
Get:38 http://archive.ubuntu.com/ubuntu jammy-updates/restricted Translation-en [114 kB]             
Get:39 http://archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 c-n-f Metadata [536 B]           
Get:40 http://archive.ubuntu.com/ubuntu jammy-updates/multiverse i386 Packages [3&#8239;888 B]
Get:41 http://archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 Packages [41,6 kB]               
Get:42 http://archive.ubuntu.com/ubuntu jammy-updates/multiverse Translation-en [9&#8239;768 B]               
Get:43 http://archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 DEP-11 Metadata [940 B]                
Get:44 http://archive.ubuntu.com/ubuntu jammy-updates/multiverse DEP-11 48x48 Icons [1&#8239;867 B]           
Get:45 http://archive.ubuntu.com/ubuntu jammy-updates/multiverse DEP-11 64x64 Icons [2&#8239;497 B]
Get:46 http://archive.ubuntu.com/ubuntu jammy-updates/multiverse DEP-11 64x64@2 Icons [29 B]   
Get:47 http://archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 c-n-f Metadata [476 B]
Get:48 http://archive.ubuntu.com/ubuntu jammy-security/main i386 Packages [305 kB]
Get:49 http://archive.ubuntu.com/ubuntu jammy-security/main amd64 Packages [680 kB]                      
Get:50 http://archive.ubuntu.com/ubuntu jammy-security/main Translation-en [155 kB]                
Get:51 http://archive.ubuntu.com/ubuntu jammy-security/main amd64 DEP-11 Metadata [43,0 kB]             
Get:52 http://archive.ubuntu.com/ubuntu jammy-security/main DEP-11 48x48 Icons [16,9 kB]                    
Get:53 http://archive.ubuntu.com/ubuntu jammy-security/main DEP-11 64x64 Icons [26,5 kB]                
Get:54 http://archive.ubuntu.com/ubuntu jammy-security/main DEP-11 64x64@2 Icons [29 B]                
Get:55 http://archive.ubuntu.com/ubuntu jammy-security/main amd64 c-n-f Metadata [11,2 kB]         
Get:56 http://archive.ubuntu.com/ubuntu jammy-security/universe i386 Packages [555 kB]                    
Get:57 http://archive.ubuntu.com/ubuntu jammy-security/universe amd64 Packages [773 kB]          
Get:58 http://archive.ubuntu.com/ubuntu jammy-security/universe Translation-en [141 kB]                  
Get:59 http://archive.ubuntu.com/ubuntu jammy-security/universe amd64 DEP-11 Metadata [40,1 kB]         
Get:60 http://archive.ubuntu.com/ubuntu jammy-security/universe DEP-11 48x48 Icons [21,4 kB]               
Get:61 http://archive.ubuntu.com/ubuntu jammy-security/universe DEP-11 64x64 Icons [33,9 kB]          
Get:62 http://archive.ubuntu.com/ubuntu jammy-security/universe DEP-11 64x64@2 Icons [29 B]             
Get:63 http://archive.ubuntu.com/ubuntu jammy-security/universe amd64 c-n-f Metadata [16,5 kB]
Get:64 http://archive.ubuntu.com/ubuntu jammy-security/restricted i386 Packages [30,0 kB]                 
Get:65 http://archive.ubuntu.com/ubuntu jammy-security/restricted amd64 Packages [694 kB]                 
Get:66 http://archive.ubuntu.com/ubuntu jammy-security/restricted Translation-en [110 kB]                
Get:67 http://archive.ubuntu.com/ubuntu jammy-security/restricted amd64 c-n-f Metadata [536 B]          
Get:68 http://archive.ubuntu.com/ubuntu jammy-backports/main amd64 Packages [40,8 kB]  
Get:69 http://archive.ubuntu.com/ubuntu jammy-backports/main i386 Packages [33,6 kB]                
Get:70 http://archive.ubuntu.com/ubuntu jammy-backports/main Translation-en [10,2 kB]                
Get:71 http://archive.ubuntu.com/ubuntu jammy-backports/main amd64 DEP-11 Metadata [4&#8239;920 B]              
Get:72 http://archive.ubuntu.com/ubuntu jammy-backports/main DEP-11 48x48 Icons [16,1 kB]                       
Get:73 http://archive.ubuntu.com/ubuntu jammy-backports/main DEP-11 64x64 Icons [21,3 kB]                       
Get:74 http://archive.ubuntu.com/ubuntu jammy-backports/main DEP-11 64x64@2 Icons [29 B]               
Get:75 http://archive.ubuntu.com/ubuntu jammy-backports/main amd64 c-n-f Metadata [388 B]      
Get:76 http://archive.ubuntu.com/ubuntu jammy-backports/restricted amd64 c-n-f Metadata [116 B]
Get:77 http://archive.ubuntu.com/ubuntu jammy-backports/universe i386 Packages [12,8 kB]
Get:78 http://archive.ubuntu.com/ubuntu jammy-backports/universe amd64 Packages [22,3 kB]                  
Get:79 http://archive.ubuntu.com/ubuntu jammy-backports/universe Translation-en [15,4 kB]            
Get:80 http://archive.ubuntu.com/ubuntu jammy-backports/universe amd64 DEP-11 Metadata [15,5 kB]           
Get:81 http://archive.ubuntu.com/ubuntu jammy-backports/universe DEP-11 48x48 Icons [13,1 kB]                      
Get:82 http://archive.ubuntu.com/ubuntu jammy-backports/universe DEP-11 64x64 Icons [22,0 kB]
Get:83 http://archive.ubuntu.com/ubuntu jammy-backports/universe DEP-11 64x64@2 Icons [29 B]             
Get:84 http://archive.ubuntu.com/ubuntu jammy-backports/universe amd64 c-n-f Metadata [576 B]         
Get:85 http://archive.ubuntu.com/ubuntu jammy-backports/multiverse amd64 c-n-f Metadata [116 B]          
Hit:86 https://packages.microsoft.com/repos/edge stable InRelease             
Fetched 9&#8239;574 kB in 5s (1&#8239;763 kB/s)      
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.
root@espineux:/etc/apt# apt install --reinstall thunderbird thunderbird-gnome-support thunderbird-locale-en thunderbird-locale-en-gb thunderbird-locale-en-us thunderbird-locale-fr
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Reinstallation of thunderbird is not possible, it cannot be downloaded.
Reinstallation of thunderbird-gnome-support is not possible, it cannot be downloaded.
Reinstallation of thunderbird-locale-en is not possible, it cannot be downloaded.
Reinstallation of thunderbird-locale-en-gb is not possible, it cannot be downloaded.
Reinstallation of thunderbird-locale-en-us is not possible, it cannot be downloaded.
Reinstallation of thunderbird-locale-fr is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

```
As per waiting, I've got this problem for 3 days. I tried to solve it myself before asking for help.... It is only when it goes above my pay grade that I bother to trouble others...... 
And before that I ask Google which in this case was of no help ;-) 
Puzzled I am. 
Thanks for your help.

---

### Post by georgesgiralt on 2023-08-27
Hello,
I think that the problem lies in the fetching of the packages, as the apt-cache policy command returns a 500 error :
```
500 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
```
Do you know what mechanism is used to fetch the packages and what software is involved ? In order for me to check and compare between the working machine and the broken one ? 
My knowledge of the apt and dpkg mechanism does not extend to this kind of detail.
So an explanation or a lead to a pertinent documentation would be very very valuable.

---

### Post by #&amp;thj^% on 2023-08-27
> **georgesgiralt said:**
> 
The 500 error bothers me ... If I'm not mistaken it means that the download demand was misformed. 
So could it be some part of the apt software engine is broken ?
How could I check it and/or  reinstall all of it ? 
I4m more and more puzzled.
I see nothing wrong with the 500

> **georgesgiralt said:**
> Hello,
I think that the problem lies in the fetching of the packages, as the apt-cache policy command returns a 500 error :
```
500 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
```

I forgo the lengthy details, but all looks good on this much:
mine:
```
apt policy thunderbird
thunderbird:
  Installed: 1:102.15.0+build1-0ubuntu0.22.04.1~mt1
  Candidate: 1:102.15.0+build1-0ubuntu0.22.04.1~mt1
  Version table:
 *** 1:102.15.0+build1-0ubuntu0.22.04.1~mt1 1001
       1001 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status
     1:102.13.0+build1-0ubuntu0.23.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu lunar-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu lunar-security/main amd64 Packages
     1:102.10.0+build2-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 Packages

```
If you notice i using the PPA version of TB I'm allergic to snaps
"If you want" you can add the PPA and try it out to see if it helps.
```
sudo add-apt-repository ppa:mozillateam/ppa
sudo apt update
```
Now try again with your install.
And to remove if this was just an motion in practice;
```
sudo add-apt-repository --remove ppa:mozillateam
```
followed with:
```
sudo apt autoremove --purge thunderbird
```
Good luck
Forgot this one and you seem to need it:
```
apt policy thunderbird-gnome-support 
thunderbird-gnome-support:
  Installed: (none)
  Candidate: 1:102.15.0+build1-0ubuntu0.22.04.1~mt1
  Version table:
     1:102.15.0+build1-0ubuntu0.22.04.1~mt1 1001
       1001 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy/main amd64 Packages
     1:102.13.0+build1-0ubuntu0.23.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu lunar-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu lunar-security/main amd64 Packages
     1:102.10.0+build2-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 Packages

```
But Wait there's more ways:
```
flatpak search thunderbird
Name   Description               Application ID     Version       Branch Remotes
Thund&#8230; Thunderbird is a free an&#8230; &#8230;zilla.Thunderbird 115.1.1       stable flathub
Birdt&#8230; System tray new mail not&#8230; &#8230;lduzsoft.Birdtray 1.9.0         stable flathub
Bette&#8230; Betterbird is a soft for&#8230; &#8230;erbird.Betterbird 102.14.0-bb39 stable flathub
Proto&#8230; Seamlessly encrypts and &#8230; &#8230;protonmail-bridge 3.3.2         stable flathub

```

---

### Post by ian-weisser on 2023-08-27
> **georgesgiralt said:**
> 
The 500 error bothers me


In your apt policy output the "500" is not an http error code, nor ftp error code, nor any sort of error code at all.

It's an apt priority, and it's appropriate.

---

### Post by georgesgiralt on 2023-08-27
Hello, 1fallen
Something strange here : 
```
# snap list
Name                       Version           Rev    Tracking         Publisher       Notes
bare                       1.0               5      latest/stable    canonical**     base
canonical-livepatch        10.6.0            235    latest/stable    canonical**     -
chromium                   116.0.5845.110    2599   latest/stable    canonical**     -
core                       16-2.60.2         15925  latest/stable    canonical**     core
core20                     20230801          2015   latest/stable    canonical**     base
core22                     20230725          858    latest/stable    canonical**     base
cups                       2.4.6-4           980    latest/stable    openprinting**  -
firefox                    116.0.3-2         3026   latest/stable    mozilla**       -
gnome-3-38-2004            0+git.efb213a     143    latest/stable/&#8230;  canonical**     -
gnome-42-2204              0+git.ff35a85     126    latest/stable    canonical**     -
gtk-common-themes          0.1-81-g442e511   1535   latest/stable/&#8230;  canonical**     -
snap-store                 41.3-71-g709398e  959    latest/stable/&#8230;  canonical**     -
snapd                      2.60.2            19993  latest/stable    canonical**     snapd
snapd-desktop-integration  0.9               83     latest/stable/&#8230;  canonical**     -

```
Obviously, I'm not using a snap.... ;-)
But as I miss the PPA from MozillaTeam, where does come this ? 
```

# dpkg -l thunderbird
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version                                Architecture Description
+++-==============-======================================-============-===========================================================
ii  thunderbird    1:102.14.0+build1-0ubuntu0.22.04.1~mt1 amd64        Email, RSS and newsgroup client with integrated spam filter
# 
```
And as I installed from scratch (due to a failed disk) It is very strange. And I do not think I have messed with the PPAs in the meantime.
I'll try to add the Moz PPA and install/reinstall. 
I'll report back.

---

### Post by georgesgiralt on 2023-08-27
> **ian-weisser said:**
> In your apt policy output the "500" is not an http error code, nor any sort of error code at all.

It's an apt priority, and it's appropriate.

Ian, obviously, I'm not up to speed on the apt policy output. I've to do my homework.... I thought it was an FTP style error message (the RFC # escapes me now).....

---

### Post by #&amp;thj^% on 2023-08-27
Exactly the same on my end:
```
dpkg -l thunderbird
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version                                Architecture Descript>
+++-==============-======================================-============-========>
ii  thunderbird    1:102.15.0+build1-0ubuntu0.22.04.1~mt1 amd64        Email, R>

```
And launching it from the terminal I get:
```
thunderbird
[ImapModuleLoader] Using nsImapService.cpp
[NntpModuleLoader] Using NntpService.jsm
[Pop3ModuleLoader] Using Pop3Service.jsm
[calBackendLoader] Using Thunderbird's ical.js backend
console.debug: "mPlatform is: linux"
console.debug: "Checking for ical data"
console.warn: SearchSettings: "get: No settings file exists, new profile?" (new NotFoundError("Could not open the file at /home/me/.thunderbird/ouzkpg7r.default-release/search.json.mozlz4", (void 0)))
console.debug: "Found 0 public keys and 0 secret keys (0 protected, 0 unprotected)"
console.debug: "Successfully loaded optional OpenPGP library libgpgme.so.11 from system's standard library locations"
console.debug: "gpgme version: 1.18.0"
console.debug: "Trying to load /usr/lib/thunderbird/libotr.so"
console.debug: "Trying to load libotr.so from system's standard library locations"
console.debug: "Trying to load libotr.so.5 from system's standard library locations"
console.debug: "Trying to load libotr.so from system's standard library locations"
console.log: (new Error("Cannot load required OTR library", "resource:///modules/OTRLib.jsm", 109))


```
All is good on my end.

---

### Post by georgesgiralt on 2023-08-27
Hello Guys,
So I put the MozillaTeam PPA in place, and re-installed Thunderbird. 
I did not get the same version, though. 
```

# dpkg -l thunderbird
Souhait=inconnU/Installé/suppRimé/Purgé/H=à garder
| État=Non/Installé/fichier-Config/dépaqUeté/échec-conFig/H=semi-installé/W=attend-traitement-déclenchements
|/ Err?=(aucune)/besoin Réinstallation (État,Err: majuscule=mauvais)
||/ Nom            Version                                Architecture Description
+++-==============-======================================-============-===========================================================
ii  thunderbird    1:102.15.0+build1-0ubuntu0.22.04.1~mt1 amd64        Email, RSS and newsgroup client with integrated spam filter

```
Yesterday I used 1:102.14 ..... 
So I thought that my have solved my problem about Thunderbird .... 
Alas not. 
So now I've to found why I have a problem with Thunderbird and also with apt and it's downloads... 
The computer where I can get Thunderbird re-installed does not use the MozillaTeam PPA nor the snap for Thunderbird. Use the French repo server and works fine ... 
What is broken on my computer, and how to fix is a puzzle to me. 
And of course, put back the "standard" version of Thunderbird... 
Have a nice day.

---

### Post by georgesgiralt on 2023-08-31
Hello Guys,
I finally solved my issue, but did not find what was wrong. 
I spent days searching how to check, clean and heal my apt/dpkg subsystem and, of course Thunderbird.
And, then I had an epiphany. What was the version used when Ubuntu Jammy 22.04LTS went out ?  
If I'm not mistaken it was 1:102.12.0+build1-0ubuntu0.22.04
So I did :
```

sudo apt-get install thunderbird=1:102.12.0+build1-0ubuntu0.22.04

```
It forced a "downgrade" of Thunderbird package and removed all the related Thunderbird packages I had installed  ( thunderbird-gnome-support thunderbird-locale-ca thunderbird-locale-en-gb thunderbird-locale-en-us thunderbird-locale-en thunderbird-locale-fr).
I then installed the version Thunderbird should have on my exact Jammy .
```

apt-get install thunderbird=1:102.13.0+build1-0ubuntu0.22.04.1
```
And then I installed the suggested packages I had previously. 
```
apt install thunderbird-gnome-support thunderbird-locale-ca thunderbird-locale-en-gb thunderbird-locale-en-us thunderbird-locale-en thunderbird-locale-fr
```
Everything went fine , and now : 
```
$ sudo apt install --reinstall thunderbird
[sudo] Mot de passe de s*: 
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances... Fait
Lecture des informations d'état... Fait      
0 mis à jour, 0 nouvellement installés, 1 réinstallés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de prendre 0 o/62,4 Mo dans les archives.
Après cette opération, 0 o d'espace disque supplémentaires seront utilisés.
(Lecture de la base de données... 489453 fichiers et répertoires déjà installés.)
Préparation du dépaquetage de .../thunderbird_1%3a102.13.0+build1-0ubuntu0.22.04.1_amd64.deb ...
Dépaquetage de thunderbird (1:102.13.0+build1-0ubuntu0.22.04.1) sur (1:102.13.0+build1-0ubuntu0.22.04.1) ...
Paramétrage de thunderbird (1:102.13.0+build1-0ubuntu0.22.04.1) ...
Traitement des actions différées («*triggers*») pour bamfdaemon (0.5.6+22.04.20220217-0ubuntu1)*...
Rebuilding /usr/share/applications/bamf-2.index...
Traitement des actions différées («*triggers*») pour desktop-file-utils (0.26-1ubuntu3)*...
Traitement des actions différées («*triggers*») pour hicolor-icon-theme (0.17-2)*...
Traitement des actions différées («*triggers*») pour gnome-menus (3.36.0-1ubuntu3)*...
Traitement des actions différées («*triggers*») pour man-db (2.10.2-1)*...
Traitement des actions différées («*triggers*») pour mailcap (3.70+nmu1ubuntu1)*...
$
```
Et voila ! 
I'll never know what went wrong but, following my infructuous search of problems in apt, I bet the problem lied in the Thunderbird and associated packages dependencies and versions. 
Thanks all for your help !
Have a nice day.

---

