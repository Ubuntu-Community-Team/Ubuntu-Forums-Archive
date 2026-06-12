---
title: "Computer locked up during a normal apt-get update, now apt is broken!"
date: 2007-06-04
forum: General Help
---

### Post by Flecko on 2007-06-04
Hello,

Two days ago, I was updating my computer with the normal updates that come out for Feisty when I ran into a problem. My computer hard locked during the update process. No problem I thought, so I just rebooted the machine and everything went fine to the desktop. The problem appeared when I tried to run Synaptic to finish updating. It failed with a blank error message. 

To try to get to the bottom of the problem I ran apt from the commandline to see if it would tell me anything more meaningful. This is what I got:

```
root@flecko-desktop:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  firefox firefox-gnome-support gimp gimp-data gimp-python libfreetype6
  libgimp2.0 libnspr4 libnss3
9 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/16.3MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `
E: Sub-process /usr/bin/dpkg returned an error code (2)
root@flecko-desktop:~# 
```

I'm stuck! I don't want to have to nuke my Feisty install. Everything has been going so great. Any ideas? I tried to see if that file existed and what it might contain, but no go.

Please help!
Thankyou all,
-Flecko

---

### Post by Bohlio on 2007-06-04
Flecko, are you running as root? hence the  "root@flecko-desktop"?

Isnt that super unsafe unless your a crazy smart ubuntu expert?

---

### Post by taurus on 2007-06-04
What happens when you run

```
sudo aptitude update
```

---

### Post by Flecko on 2007-06-05
Bohlio: No, of course I'm not running as root. All I did was "sudo -i" so that I could stop typing sudo before every command...very handy when you're troubleshooting something like this.

Taurus: This is what happens when I do an aptitude update:

```
root@flecko-desktop:~# sudo aptitude update
Get:1 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US               
Get:2 http://archive.ubuntu.com feisty-updates Release.gpg [191B]    
Ign http://archive.ubuntu.com feisty-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US   
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:3 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B] 
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US       
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US 
Get:4 http://security.ubuntu.com feisty-security Release.gpg [191B]  
Ign http://security.ubuntu.com feisty-security/main Translation-en_US        
Ign http://archive.ubuntu.com feisty-updates/main Translation-en_US  
Ign http://archive.ubuntu.com feisty-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com feisty-updates/universe Translation-en_US
Get:5 http://archive.ubuntu.com feisty-backports Release.gpg [191B]  
Ign http://archive.ubuntu.com feisty-backports/restricted Translation-en_US  
Ign http://archive.ubuntu.com feisty-backports/main Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release                      
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US     
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com feisty-updates Release              
Ign http://archive.ubuntu.com feisty-backports/multiverse Translation-en_US     
Ign http://archive.ubuntu.com feisty-backports/universe Translation-en_US       
Hit http://archive.ubuntu.com feisty-updates Release                            
Hit http://archive.ubuntu.com feisty-backports Release                          
Hit http://security.ubuntu.com feisty-security Release               
Hit http://us.archive.ubuntu.com feisty/main Packages                
Hit http://us.archive.ubuntu.com feisty/restricted Packages          
Hit http://us.archive.ubuntu.com feisty/main Sources                 
Hit http://archive.ubuntu.com feisty-updates/restricted Packages     
Hit http://archive.ubuntu.com feisty-updates/main Packages
Hit http://archive.ubuntu.com feisty-updates/multiverse Packages
Hit http://security.ubuntu.com feisty-security/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/universe Sources             
Hit http://us.archive.ubuntu.com feisty/multiverse Packages          
Hit http://us.archive.ubuntu.com feisty/multiverse Sources           
Hit http://us.archive.ubuntu.com feisty-updates/main Packages        
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://archive.ubuntu.com feisty-updates/universe Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://archive.ubuntu.com feisty-backports/restricted Packages
Hit http://archive.ubuntu.com feisty-backports/main Packages
Hit http://archive.ubuntu.com feisty-backports/multiverse Packages
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://archive.ubuntu.com feisty-backports/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Fetched 5B in 1s (3B/s)
Reading package lists... Done
root@flecko-desktop:~# 
```

I went ahead and tried to do an 'upgrade' command after that, but no luck:
```

root@flecko-desktop:~# sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages will be upgraded:
  firefox firefox-gnome-support gimp gimp-data gimp-python libfreetype6 
  libgimp2.0 libnspr4 libnss3 
9 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/16.3MB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] Y
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `
root@flecko-desktop:~#
``` 

I can't find a command to repair apt anywhere on the internet. I think that file available is just corrupt or missing. It could have possibly been wiped when my computer hard locked. Anyone have any idea how to fix that?

Thanks again all,
-Flecko

---

### Post by Flecko on 2007-06-05
Sweet sassy molassy! I got it figured out after googling for over an hour.

The trick to fixing this problem is to move your /var/lib/available file to /var/lib/available.bak and then running "dselect update" as root.

Then all shall be fine.
Hope this helps someone else!
-Flecko

---

