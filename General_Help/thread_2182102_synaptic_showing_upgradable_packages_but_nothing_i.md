---
title: "synaptic showing upgradable packages but nothing in software updater"
date: 2013-10-20
forum: General Help
---

### Post by medior on 2013-10-20
Hi,

A few days ago I did a fresh install of Ubuntu 13.10 (64-bit). When I open synaptic I get a list of 9 upgradable packages (see screenshot), but when checking with Software Updater it tells me the software on this computer is up to date. Does anyone know why the two applications don't agree? Is it save to install upgrades through Synaptic?

[ATTACH=CONFIG]247086[/ATTACH]

Thanks in advance,

medior

---

### Post by howefield on 2013-10-20
Synaptic or the terminal is all I use for updating. Just checked mine and the same installed packages are at the newer version.

What does the terminal say ?

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by medior on 2013-10-20
Thanks for the quick reply. apt-get upgrade shows the same 9 packages as upgradable:

```
medior@hp-g6-laptop:~$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy InRelease                        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy InRelease                     
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy InRelease                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release.gpg            
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates InRelease             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release.gpg                       
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy Release.gpg                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release                                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy Release                                              
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports InRelease                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Sources                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy Release.gpg                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Sources                      
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy/partner amd64 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Sources     
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates Release.gpg [933 B] 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main amd64 Packages                                                
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy/partner i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Sources       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports Release.gpg         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main i386 Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Sources     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main amd64 Packages                                                 
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates Release [49.6 kB]                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted amd64 Packages                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe amd64 Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse amd64 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main i386 Packages                                                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports Release                                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted i386 Packages                                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/main Sources                                                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe i386 Packages                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/restricted Sources             
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy/partner Translation-en_GB      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/universe Sources               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en_GB             
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy/partner Translation-en         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/multiverse Sources             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/main amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/restricted amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/universe amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/multiverse amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/universe Translation-en
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/main Sources [2,496 B]
Get:4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/restricted Sources [14 B]
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/universe Sources [14 B]
Get:6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/multiverse Sources [14 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en_GB  
Get:7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/main amd64 Packages [5,493 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en_GB
Get:8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/restricted amd64 Packages [14 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en_GB
Get:9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/universe amd64 Packages [1,293 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en_GB
Get:10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/multiverse amd64 Packages [14 B]
Get:11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/main i386 Packages [5,477 B]
Get:12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/restricted i386 Packages [14 B]
Get:13 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/universe i386 Packages [1,301 B]
Get:14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/multiverse i386 Packages [14 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/main amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/restricted amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/universe amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/multiverse amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/universe Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/universe Translation-en_GB
Fetched 66.7 kB in 3s (18.9 kB/s)
Reading package lists... Done

medior@hp-g6-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  gir1.2-gudev-1.0 libgudev-1.0-0 libpam-systemd libsystemd-daemon0 libsystemd-journal0 libsystemd-login0 libudev1 systemd-services udev
9 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,554 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
medior@hp-g6-laptop:~$
```

---

### Post by fantab on 2013-10-20
Check the update-manager settings... see the set duration to check for updates.

Update using Synaptic or Terminal, what difference does it make how upgrade, as long as you upgrade.

---

### Post by medior on 2013-10-20
> **fantab said:**
> Check the update-manager settings... see the set duration to check for updates.

Update using Synaptic or Terminal, what difference does it make how upgrade, as long as you upgrade.

The update-manager settings are set to check daily, and to display immediately for security and other update, and I have this problem now for a couple of days.

The reason why I am not upgrading (yet) via Synaptic or Terminal is because I am trying to find out what is going on. Many of my friends and family use Ubuntu and not all of them are computer experts. They rely on the automatic updates via update-manager.

---

### Post by ibjsb4 on 2013-10-20
[Update_Manager]("https://bugs.launchpad.net/ubuntu/+source/update-manager") has it quirts, I don't see that changing anytime soon.

If you must use update manager, it will be necessary to give it a kick-start.  I have found this to work in the pass with the update command.  So maybe a cron job would work.

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by philinux on 2013-10-21
I got exactly same thing and the same updates. Update manager only shows a very small ubuntu-base update, I did that it checked again and said nothing. 

Update-manager says up to date but terminal shows these outstanding updates. Anyway I used the terminal to upgrade these.

---

### Post by philinux on 2013-10-21
Happened on another machine now so I took some screenshots.

First two are what updater shows compared to terminal. I let the updater do it's thing then rechecked in terminal after it showed machine was up to date.

[http://imagebin.org/274296](http://imagebin.org/274296)

[http://imagebin.org/274295](http://imagebin.org/274295)

Ok so now updater says up to date but as you'll see below it's not.

[http://imagebin.org/274297](http://imagebin.org/274297)

Bug report raised. Please could someone confirm it by clicking on the "This bug affects you" button.

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1242749](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1242749)

---

### Post by Hewjr100 on 2013-10-22
Is it normal for Ubuntu Software Updater and apt-upgrade to have different results?  In my case one say all software is up to date, and the other shows 9 upgrades.  I know this is normal in Mint, but do not believe it happens in Ubuntu.

Henry

---

### Post by philinux on 2013-10-22
Threads merged please see post 8. Go to bug report and click on affects you.

---

### Post by Hewjr100 on 2013-10-23
Ok I checked "Affects me too" in bug report.  It is now confirmed.

Henry

---

### Post by mc4man on 2013-10-23
The bug report explains why atm software-updater will not update these packages , the behavior is intentional

---

### Post by medior on 2013-10-24
Thank you setting up a bug report. So it turns out it's not a bug it's a feature called Phased updates:
[http://www.murraytwins.com/blog/?p=127](http://www.murraytwins.com/blog/?p=127)
So if I understand it right sooner or later the packages would have got installed (in the meantime I used apt-get).

A quote from the link above:
One can opt out of the Phased Update process by adding ‘Update-Manager::Never-Include-Phased-Updates “True”;’ to the configuration file “/etc/apt/apt.conf”.

I can't find that option in the man pages, so I am not entirely sure what it does. Wait until the phasing process is over and then install the package?

---

### Post by philinux on 2013-10-24
> **medior said:**
> Thank you setting up a bug report. So it turns out it's not a bug it's a feature called Phased updates:
[http://www.murraytwins.com/blog/?p=127](http://www.murraytwins.com/blog/?p=127)
So if I understand it right sooner or later the packages would have got installed (in the meantime I used apt-get).

A quote from the link above:
One can opt out of the Phased Update process by adding &#8216;Update-Manager::Never-Include-Phased-Updates &#8220;True&#8221;;&#8217; to the configuration file &#8220;/etc/apt/apt.conf&#8221;.

I can't find that option in the man pages, so I am not entirely sure what it does. Wait until the phasing process is over and then install the package?

That file does not exist you have to create it first then add the option to it. I'm guessing that a reboot would be needed for it to take effect.

```
pkexec gedit /etc/apt/apt.conf
```

---

