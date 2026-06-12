---
title: "Failed to download updates"
date: 2013-10-14
forum: General Help
---

### Post by david98 on 2013-10-14
Am using ubuntu 13.04 and trying to install updates through software updates every time i click check for updates it say's failed to check for updates check your internet connection. There's nothing wrong with my internet connection as am using the same system to post this now what could the problem be any advice would be appreciated. 

Thank you in advance

Dave

---

### Post by Bashing-om on 2013-10-14
david98; Hi !

A starting point for trouble shooting is to insure the package management system is in a consistent state.
Post back the output of terminal codes:
```

sudo apt-get update
sudo apt-get upgrade

```

[INDENT][INDENT]make a solid foundation and shoot straight
 [/INDENT][/INDENT]

---

### Post by whitesmith on 2013-10-14
Is Update Manager set to install all updates or maybe just important ones? Let me know, please.

---

### Post by david98 on 2013-10-14
```
dave@dave-300E5EV-300E4EV-270E5EV-270E4EV:~$  sudo apt-get update
[sudo] password for dave: 
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring Release.gpg
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring Release
Err cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/main amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/restricted amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/main Translation-en_GB
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/main Translation-en
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/restricted Translation-en_GB
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release.gpg                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring Release.gpg                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates Release.gpg           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports Release.gpg         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Sources
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-proposed Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Sources
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main amd64 Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Sources                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main amd64 Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-proposed Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted amd64 Packages       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/main Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/multiverse Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/main amd64 Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/restricted amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/universe amd64 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/multiverse amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/main amd64 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/restricted amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/universe amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/multiverse amd64 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/main i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/restricted i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/main amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/restricted amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/universe amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/multiverse amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-proposed/main amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-proposed/restricted amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-proposed/multiverse amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-proposed/universe amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-proposed/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-proposed/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-proposed/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-proposed/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-proposed/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-proposed/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-proposed/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-proposed/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-proposed/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-proposed/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-proposed/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-proposed/universe Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/universe Translation-en_GB
W: Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)/dists/raring/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)/dists/raring/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)/dists/raring/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)/dists/raring/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by david98 on 2013-10-14
@[COLOR=#000000]whitesmith it's set to install all updates

[/COLOR]

---

### Post by ibjsb4 on 2013-10-14
Uncheck Cdrom

[https://help.ubuntu.com/community/Repositories/Ubuntu#CD-ROM.2BAC8-DVD](https://help.ubuntu.com/community/Repositories/Ubuntu#CD-ROM.2BAC8-DVD)

---

### Post by david98 on 2013-10-14
Problem solved cheer's

---

### Post by Sam_Christianson on 2014-03-18
what happens when you have this issue and the cdrom is already unchecked?

---

### Post by Bashing-om on 2014-03-18
Sam_Christianson: Hi !


> 
what happens when you have this issue and the cdrom is already unchecked?

Then you do step 1:
Post back the out puts - between code tags - of the terminal commands:
```

sudo apt-get update
sudo apt-get upgrade

```
These outputs will indicate where the error is.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

step 1
[INDENT][INDENT]a good place to start
[/INDENT][/INDENT]

---

