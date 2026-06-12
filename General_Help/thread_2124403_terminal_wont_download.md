---
title: "terminal wont download"
date: 2013-03-10
forum: General Help
---

### Post by Isaacmarritt on 2013-03-10
Hi i've been having ploblems with my terminal for the last week it wont download anything this is a problem because this is the only way I know to install things on ubuntu I need to fix this so I can install programs to my computer thanks any help aprecated

---

### Post by ManamiVixen on 2013-03-10
What are you trying to download? Updates? Upgrades? individual files?

---

### Post by Isaacmarritt on 2013-03-10
all of the above

---

### Post by ManamiVixen on 2013-03-10
What happens when you "sudo apt-get update"? Post the result here.

---

### Post by ibjsb4 on 2013-03-10
Post the output of an update, let us see some errors.

---

### Post by Isaacmarritt on 2013-03-10
isaac@isaac-MacBookPro:~$ sudo apt-get update[sudo] password for isaac: 
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal InRelease
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal Release.gpg
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal Release
Err cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal/main Translation-en_CA
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal/main Translation-en
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal/restricted Translation-en_CA
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal/restricted Translation-en
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal InRelease                
  
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-updates InRelease        
  
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-proposed InRelease       
  
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-backports InRelease      
  
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal Release.gpg              
  Unable to connect to 24.117.225.141:3128:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-updates Release.gpg      
  Unable to connect to 24.117.225.141:3128:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-proposed Release.gpg     
  Unable to connect to 24.117.225.141:3128:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-backports Release.gpg    
  Unable to connect to 24.117.225.141:3128:
Err [http://archive.canonical.com](http://archive.canonical.com) quantal InRelease                
  
Err [http://archive.canonical.com](http://archive.canonical.com) quantal Release.gpg              
  Unable to connect to 24.117.225.141:3128:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal InRelease                    
  
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease         
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                    
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                    
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                    
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                    
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                    
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                    
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                    
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                    
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                    
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                    
  
Err [http://dl.google.com](http://dl.google.com) stable InRelease                         
  
Err [http://download.skype.com](http://download.skype.com) stable InRelease                    
  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg                  
  Unable to connect to 24.117.225.141:3128:
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg
  Unable to connect to 24.117.225.141:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg
  Unable to connect to 24.117.225.141:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg
  Unable to connect to 24.117.225.141:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg
  Unable to connect to 24.117.225.141:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg
  Unable to connect to 24.117.225.141:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg
  Unable to connect to 24.117.225.141:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg
  Unable to connect to 24.117.225.141:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg
  Unable to connect to 24.117.225.141:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg
  Unable to connect to 24.117.225.141:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg
  Unable to connect to 24.117.225.141:3128:
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg
  Unable to connect to 24.117.225.141:3128:
Err [http://download.skype.com](http://download.skype.com) stable Release.gpg
  Unable to connect to 24.117.225.141:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg
  Unable to connect to 24.117.225.141:3128:
Reading package lists... Done
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal/InRelease](http://ca.archive.ubuntu.com/ubuntu/dists/quantal/InRelease)  


W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/quantal/InRelease](http://archive.canonical.com/ubuntu/dists/quantal/InRelease)  


W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/quantal/InRelease](http://extras.ubuntu.com/ubuntu/dists/quantal/InRelease)  


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/InRelease](http://security.ubuntu.com/ubuntu/dists/quantal-security/InRelease)  


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal-updates/InRelease](http://ca.archive.ubuntu.com/ubuntu/dists/quantal-updates/InRelease)  


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal-proposed/InRelease](http://ca.archive.ubuntu.com/ubuntu/dists/quantal-proposed/InRelease)  


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal-backports/InRelease](http://ca.archive.ubuntu.com/ubuntu/dists/quantal-backports/InRelease)  


W: Failed to fetch [http://ppa.launchpad.net/a-v-shkop/chromium/ubuntu/dists/quantal/InRelease](http://ppa.launchpad.net/a-v-shkop/chromium/ubuntu/dists/quantal/InRelease)  


W: Failed to fetch [http://ppa.launchpad.net/ehoover/compholio/ubuntu/dists/quantal/InRelease](http://ppa.launchpad.net/ehoover/compholio/ubuntu/dists/quantal/InRelease)  


W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/InRelease](http://dl.google.com/linux/chrome/deb/dists/stable/InRelease)  


W: Failed to fetch [http://ppa.launchpad.net/loneowais/gmailwatcher.dev/ubuntu/dists/quantal/InRelease](http://ppa.launchpad.net/loneowais/gmailwatcher.dev/ubuntu/dists/quantal/InRelease)  


W: Failed to fetch [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/quantal/InRelease](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/quantal/InRelease)  


W: Failed to fetch [http://ppa.launchpad.net/scopes-packagers/ppa/ubuntu/dists/quantal/InRelease](http://ppa.launchpad.net/scopes-packagers/ppa/ubuntu/dists/quantal/InRelease)  


W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/InRelease](http://download.skype.com/linux/repos/debian/dists/stable/InRelease)  


W: Failed to fetch [http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/quantal/InRelease](http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/quantal/InRelease)  


W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/quantal/InRelease](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/quantal/InRelease)  


W: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/quantal/InRelease](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/quantal/InRelease)  


W: Failed to fetch [http://ppa.launchpad.net/upubuntu-com/conky/ubuntu/dists/quantal/InRelease](http://ppa.launchpad.net/upubuntu-com/conky/ubuntu/dists/quantal/InRelease)  


W: Failed to fetch [http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/quantal/InRelease](http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/quantal/InRelease)  


W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)/dists/quantal/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)/dists/quantal/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/quantal/Release.gpg)  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal-updates/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/quantal-updates/Release.gpg)  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal-proposed/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/quantal-proposed/Release.gpg)  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal-backports/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/quantal-backports/Release.gpg)  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/quantal/Release.gpg](http://archive.canonical.com/ubuntu/dists/quantal/Release.gpg)  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/quantal/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/quantal/Release.gpg)  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/quantal-security/Release.gpg)  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://ppa.launchpad.net/a-v-shkop/chromium/ubuntu/dists/quantal/Release.gpg](http://ppa.launchpad.net/a-v-shkop/chromium/ubuntu/dists/quantal/Release.gpg)  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://ppa.launchpad.net/ehoover/compholio/ubuntu/dists/quantal/Release.gpg](http://ppa.launchpad.net/ehoover/compholio/ubuntu/dists/quantal/Release.gpg)  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://ppa.launchpad.net/loneowais/gmailwatcher.dev/ubuntu/dists/quantal/Release.gpg](http://ppa.launchpad.net/loneowais/gmailwatcher.dev/ubuntu/dists/quantal/Release.gpg)  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/quantal/Release.gpg](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/quantal/Release.gpg)  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://ppa.launchpad.net/scopes-packagers/ppa/ubuntu/dists/quantal/Release.gpg](http://ppa.launchpad.net/scopes-packagers/ppa/ubuntu/dists/quantal/Release.gpg)  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/quantal/Release.gpg](http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/quantal/Release.gpg)  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/quantal/Release.gpg](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/quantal/Release.gpg)  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/quantal/Release.gpg](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/quantal/Release.gpg)  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://ppa.launchpad.net/upubuntu-com/conky/ubuntu/dists/quantal/Release.gpg](http://ppa.launchpad.net/upubuntu-com/conky/ubuntu/dists/quantal/Release.gpg)  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/quantal/Release.gpg](http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/quantal/Release.gpg)  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg)  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/Release.gpg](http://download.skype.com/linux/repos/debian/dists/stable/Release.gpg)  Unable to connect to 24.117.225.141:3128:


W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by ibjsb4 on 2013-03-10
For a start you need to comment (#) out the **cdrom** in your sources list.

```
gksudo gedit /etc/apt/sources.list
```

Then do another update.

And when you post it again, please use code tags.

[ATTACH=CONFIG]240038[/ATTACH]

And it will look like this.

```
isaac@isaac-MacBookPro:~$ sudo apt-get update[sudo] password for isaac: 
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal InRelease
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal Release.gpg
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal Release
Err cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal/main Translation-en_CA
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal/main Translation-en
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal/restricted Translation-en_CA
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal/restricted Translation-en
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal InRelease                
  
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-updates InRelease        
  
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-proposed InRelease       
  
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-backports InRelease      
  
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal Release.gpg              
  Unable to connect to 24.117.225.141:3128:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-updates Release.gpg      
  Unable to connect to 24.117.225.141:3128:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-proposed Release.gpg     
  Unable to connect to 24.117.225.141:3128:
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) quantal-backports Release.gpg    
  Unable to connect to 24.117.225.141:3128:
Err [http://archive.canonical.com](http://archive.canonical.com) quantal InRelease                
  
Err [http://archive.canonical.com](http://archive.canonical.com) quantal Release.gpg              
  Unable to connect to 24.117.225.141:3128:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal InRelease                    
  
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease         
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                    
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                    
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                    
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                    
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                    
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                    
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                    
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                    
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                    
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                    
  
Err [http://dl.google.com](http://dl.google.com) stable InRelease                         
  
Err [http://download.skype.com](http://download.skype.com) stable InRelease                    
  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg                  
  Unable to connect to 24.117.225.141:3128:
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg
  Unable to connect to 24.117.225.141:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg
  Unable to connect to 24.117.225.141:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg
  Unable to connect to 24.117.225.141:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg
  Unable to connect to 24.117.225.141:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg
  Unable to connect to 24.117.225.141:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg
  Unable to connect to 24.117.225.141:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg
  Unable to connect to 24.117.225.141:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg
  Unable to connect to 24.117.225.141:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg
  Unable to connect to 24.117.225.141:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg
  Unable to connect to 24.117.225.141:3128:
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg
  Unable to connect to 24.117.225.141:3128:
Err [http://download.skype.com](http://download.skype.com) stable Release.gpg
  Unable to connect to 24.117.225.141:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg
  Unable to connect to 24.117.225.141:3128:
Reading package lists... Done
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/...ntal/InRelease]("http://ca.archive.ubuntu.com/ubuntu/dists/quantal/InRelease")  


W: Failed to fetch [http://archive.canonical.com/ubuntu/...ntal/InRelease]("http://archive.canonical.com/ubuntu/dists/quantal/InRelease")  


W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/quantal/InRelease](http://extras.ubuntu.com/ubuntu/dists/quantal/InRelease)  


W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...rity/InRelease]("http://security.ubuntu.com/ubuntu/dists/quantal-security/InRelease")  


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/...ates/InRelease]("http://ca.archive.ubuntu.com/ubuntu/dists/quantal-updates/InRelease")  


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/...osed/InRelease]("http://ca.archive.ubuntu.com/ubuntu/dists/quantal-proposed/InRelease")  


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/...orts/InRelease]("http://ca.archive.ubuntu.com/ubuntu/dists/quantal-backports/InRelease")  


W: Failed to fetch [http://ppa.launchpad.net/a-v-shkop/c...ntal/InRelease]("http://ppa.launchpad.net/a-v-shkop/chromium/ubuntu/dists/quantal/InRelease")  


W: Failed to fetch [http://ppa.launchpad.net/ehoover/com...ntal/InRelease]("http://ppa.launchpad.net/ehoover/compholio/ubuntu/dists/quantal/InRelease")  


W: Failed to fetch [http://dl.google.com/linux/chrome/de...able/InRelease]("http://dl.google.com/linux/chrome/deb/dists/stable/InRelease")  


W: Failed to fetch [http://ppa.launchpad.net/loneowais/g...ntal/InRelease]("http://ppa.launchpad.net/loneowais/gmailwatcher.dev/ubuntu/dists/quantal/InRelease")  


W: Failed to fetch [http://ppa.launchpad.net/nilarimogar...ntal/InRelease]("http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/quantal/InRelease")  


W: Failed to fetch [http://ppa.launchpad.net/scopes-pack...ntal/InRelease]("http://ppa.launchpad.net/scopes-packagers/ppa/ubuntu/dists/quantal/InRelease")  


W: Failed to fetch [http://download.skype.com/linux/repo...able/InRelease]("http://download.skype.com/linux/repos/debian/dists/stable/InRelease")  


W: Failed to fetch [http://ppa.launchpad.net/tiheum/equi...ntal/InRelease]("http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/quantal/InRelease")  


W: Failed to fetch [http://ppa.launchpad.net/tualatrix/p...ntal/InRelease]("http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/quantal/InRelease")  


W: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine...ntal/InRelease]("http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/quantal/InRelease")  


W: Failed to fetch [http://ppa.launchpad.net/upubuntu-co...ntal/InRelease]("http://ppa.launchpad.net/upubuntu-com/conky/ubuntu/dists/quantal/InRelease")  


W: Failed to fetch [http://ppa.launchpad.net/webupd8team...ntal/InRelease]("http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/quantal/InRelease")  


W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386  (20121017.2)/dists/quantal/main/binary-i386/Packages  Please use  apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot  be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386  (20121017.2)/dists/quantal/restricted/binary-i386/Packages  Please use  apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot  be used to add new CD-ROMs


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/...al/Release.gpg]("http://ca.archive.ubuntu.com/ubuntu/dists/quantal/Release.gpg")  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/...es/Release.gpg]("http://ca.archive.ubuntu.com/ubuntu/dists/quantal-updates/Release.gpg")  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/...ed/Release.gpg]("http://ca.archive.ubuntu.com/ubuntu/dists/quantal-proposed/Release.gpg")  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/...ts/Release.gpg]("http://ca.archive.ubuntu.com/ubuntu/dists/quantal-backports/Release.gpg")  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://archive.canonical.com/ubuntu/...al/Release.gpg]("http://archive.canonical.com/ubuntu/dists/quantal/Release.gpg")  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dist...al/Release.gpg]("http://extras.ubuntu.com/ubuntu/dists/quantal/Release.gpg")  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...ty/Release.gpg]("http://security.ubuntu.com/ubuntu/dists/quantal-security/Release.gpg")  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://ppa.launchpad.net/a-v-shkop/c...al/Release.gpg]("http://ppa.launchpad.net/a-v-shkop/chromium/ubuntu/dists/quantal/Release.gpg")  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://ppa.launchpad.net/ehoover/com...al/Release.gpg]("http://ppa.launchpad.net/ehoover/compholio/ubuntu/dists/quantal/Release.gpg")  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://ppa.launchpad.net/loneowais/g...al/Release.gpg]("http://ppa.launchpad.net/loneowais/gmailwatcher.dev/ubuntu/dists/quantal/Release.gpg")  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://ppa.launchpad.net/nilarimogar...al/Release.gpg]("http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/quantal/Release.gpg")  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://ppa.launchpad.net/scopes-pack...al/Release.gpg]("http://ppa.launchpad.net/scopes-packagers/ppa/ubuntu/dists/quantal/Release.gpg")  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://ppa.launchpad.net/tiheum/equi...al/Release.gpg]("http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/quantal/Release.gpg")  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://ppa.launchpad.net/tualatrix/p...al/Release.gpg]("http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/quantal/Release.gpg")  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine...al/Release.gpg]("http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/quantal/Release.gpg")  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://ppa.launchpad.net/upubuntu-co...al/Release.gpg]("http://ppa.launchpad.net/upubuntu-com/conky/ubuntu/dists/quantal/Release.gpg")  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://ppa.launchpad.net/webupd8team...al/Release.gpg]("http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/quantal/Release.gpg")  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://dl.google.com/linux/chrome/de...le/Release.gpg]("http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg")  Unable to connect to 24.117.225.141:3128:


W: Failed to fetch [http://download.skype.com/linux/repo...le/Release.gpg]("http://download.skype.com/linux/repos/debian/dists/stable/Release.gpg")  Unable to connect to 24.117.225.141:3128:


W: Some index files failed to download. They have been ignored, or old ones used instead. 						
```

---

### Post by Captain Wicker on 2013-03-10
Hi.

I am new here, but I think this could be the solution you are wanting. ;-)

```
sudo apt-get install -f
```

---

### Post by ibjsb4 on 2013-03-10
> **Captain Wicker said:**
> Hi.

I am new here, but I think this could be the solution you are wanting. ;-)

```
sudo apt-get install -f
```

Hi Captian

The command "-f install" is used to fix broken packages and will not help in this case.  The OP has a problem with the sources.list. (number 5).

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

---

### Post by Isaacmarritt on 2013-03-10
my sources program wont open

---

### Post by prodigy_ on 2013-03-10
> **Isaacmarritt said:**
> Unable to connect to 24.117.225.141:3128
Looks like an open proxy. Unless it's yours or your ISPs, I wouldn't use it.

---

### Post by ibjsb4 on 2013-03-10
How bout just using the GUI and unchecking the cdrom.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

---

### Post by Isaacmarritt on 2013-03-10
i was running a open proxy thanks man i tried everything

---

