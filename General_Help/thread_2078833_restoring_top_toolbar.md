---
title: "restoring top toolbar"
date: 2012-10-31
forum: General Help
---

### Post by mk631219 on 2012-10-31
Hi everybody,
I have accidentally deleted my top tool bar on my Ubuntu 10.04 sometime ago and would like to restore it back to were it was before. I tried different things but I am unable to get it back.
One of the things i did was to goto couple of websites and they said to do certain things. one of them mentioned to put in sudo add-apt-repository ppa:clicompanion-devs/clicompanion-nightlies and i did and this is what i got but no tool bar just a full background.
 owner@ubuntu:~$ sudo add-apt-repository ppa:clicompanion-devs/clicompanion-nightlies
[sudo] password for owner: 
Sorry, try again.
[sudo] password for owner: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 1970E5148200CA418348886341FDF8A2B455BEF0
gpg: requesting key B455BEF0 from hkp server keyserver.ubuntu.com
sgpg: key B455BEF0: public key "Launchpad clicompanion-nightlies" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
and then the following but no tool bar yet
owner@ubuntu:~$ sudo apt-get update
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [198B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]           
Ign [http://ppa.launchpad.net/clicompanion-devs/clicompanion-nightlies/ubuntu/](http://ppa.launchpad.net/clicompanion-devs/clicompanion-nightlies/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                    
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [58.3kB] 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) lucid/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [14.0kB]             
Get:8 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,241B]          
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                    
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [57.3kB]  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources           
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources         
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [654kB]
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [675B]        
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                  
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [459kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [4,630B]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [230kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources [2,196B]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [279kB]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [103kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [11.5kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources [5,818B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [2,867B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [131kB]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [1,267B]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [135kB]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [41.9kB]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [5,362B]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [2,343B]
Fetched 2,204kB in 12s (175kB/s)                                  
Reading package lists... Done
and then i put in this
owner@ubuntu:~$ sudo apt-get install clicompanion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  most
The following NEW packages will be installed:
  clicompanion most
0 upgraded, 2 newly installed, 0 to remove and 511 not upgraded.
Need to get 70.2kB of archives.
After this operation, 381kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe most 5.0.0a-1 [48.1kB]
Get:2 [http://ppa.launchpad.net/clicompanion-devs/clicompanion-nightlies/ubuntu/](http://ppa.launchpad.net/clicompanion-devs/clicompanion-nightlies/ubuntu/) lucid/main clicompanion 1.0-6~bzr83+p12~lucid1 [22.1kB]
Fetched 70.2kB in 0s (93.6kB/s)                                  
Selecting previously deselected package most.
(Reading database ... 143018 files and directories currently installed.)
Unpacking most (from .../most_5.0.0a-1_i386.deb) ...
Selecting previously deselected package clicompanion.
Unpacking clicompanion (from .../clicompanion_1.0-6~bzr83+p12~lucid1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Setting up most (5.0.0a-1) ...

Setting up clicompanion (1.0-6~bzr83+p12~lucid1) ...
CLI Companion uses a new format to store its commands. If you stored
commands in the old format you will need to migrate them to the new
format in order to use your commands with this and future versions of
CLI Companion. The new format uses ? as a place holder for User Input
required at command run time -- i.e. command 'ls <directory>' would now be
added to the Command List as ls ?. If you have questions additional information
can be found by going to Help --> Help in the application. You can also file
a Launchpad Question at [https://answers.launchpad.net/clicompanion](https://answers.launchpad.net/clicompanion)

Processing triggers for python-support ...
owner@ubuntu:~$ 
owner@ubuntu:~$ 
what should i do about this?
as i said on the top i went to many websites and the first one told me to use my Ubuntu disk to get my tool bar back up. that sounds creepy plus i have windows xp on another partition and also an unfinished installed version of  OpenSUSE Linux.
what am i to do?
please let me know were to go.
;)

---

### Post by Ace..... on 2012-10-31
Consider re-installing, ubuntu, whilst keeping your data and settings.

Whenever I happen to see a post like yours, I'll always drop a quick response. Primarily cos I remember the heartache, and the brain cells destroyed trying to find a solution with the community.

We worked on this, and the best minds put their thoughts to it...
.... and I lost days of productivity trying to work it out.

In the end, yannbuntu pointed me in the re-install direction.

Obv you can continue to try to find the solution.... but.... the re-install is so simple..... so why not?

That (to me) is what is great about ubuntu.

When the shlit hits the fan..... re-install is a click away.

Nice!

The guide and all the resources are in the sig. :wink:

---

### Post by Karlchen on 2012-10-31
Hello, mk631219.

The desktop design is part of the user specific settings.
Re-installing the system from the scratch will have the desired effect, because you will create your account from the scratch as well. Yet, I have my doubts whether this is the most efficient approach.

In your particular case, Gnome panels messed up, I tend to assume you can achieve your goal pretty quickly and efficiently by following the steps given in this Howto article carefully: [**Restore the Default Gnome Panels in Ubuntu**]("http://www.starryhope.com/restore-the-default-panels-in-ubuntu/")

Kind regards,
Karl

---

### Post by Keith65rider on 2012-11-23
Just managed to do the same silly thing and lose my toolbar in 10.10.

After a couple of hours of hassle, and typing in syntax commands that would not work, I found PanelRestor  [http://www.starryhope.com/restore-the-default-panels-in-ubuntu/](http://www.starryhope.com/restore-the-default-panels-in-ubuntu/)

It did the job great.

keith65rider

---

