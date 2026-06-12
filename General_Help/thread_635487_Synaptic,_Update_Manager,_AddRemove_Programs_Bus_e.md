---
title: "Synaptic, Update Manager, Add/Remove Programs Bus error (core dumped)"
date: 2007-12-08
forum: General Help
---

### Post by CFBauer on 2007-12-08
All three of them open for a minute, then crash.  I am on Ubuntu Gutsy on an AMD dual core processor.  I've been a convert about 11 months now, so I am still learning. 

I've searched other help threads, and seen some suggestions.  Here is what I have tried:

```
chris@chris-desktop:~$ sudo apt-get install synaptic
[sudo] password for chris:
Bus error (core dumped). 0%
```

```
chris@chris-desktop:~$ sudo apt-get update
Ign http://download.skype.com stable Release.gpg
Ign http://download.skype.com stable/non-free Translation-en_US                
Ign http://download.skype.com stable Release                                   
Get:1 http://packages.medibuntu.org gutsy Release.gpg [189B]                   
Hit http://download.skype.com stable/non-free Packages                         
Get:2 http://us.archive.ubuntu.com gutsy Release.gpg [191B]                    
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US                  
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US
Get:3 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US
Get:4 http://us.archive.ubuntu.com gutsy-security Release.gpg [191B]           
Ign http://us.archive.ubuntu.com gutsy-security/main Translation-en_US         
Ign http://us.archive.ubuntu.com gutsy-security/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com gutsy-security/universe Translation-en_US     
Ign http://us.archive.ubuntu.com gutsy-security/multiverse Translation-en_US   
Hit http://us.archive.ubuntu.com gutsy Release                                 
Hit http://us.archive.ubuntu.com gutsy-updates Release                         
Hit http://us.archive.ubuntu.com gutsy-security Release                        
Ign http://packages.medibuntu.org gutsy/free Translation-en_US                 
Hit http://us.archive.ubuntu.com gutsy/main Packages                           
Hit http://us.archive.ubuntu.com gutsy/restricted Packages                     
Hit http://us.archive.ubuntu.com gutsy/universe Packages                       
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages                     
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages             
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages                   
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages             
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages               
Hit http://us.archive.ubuntu.com gutsy-security/main Packages                  
Hit http://us.archive.ubuntu.com gutsy-security/restricted Packages            
Hit http://us.archive.ubuntu.com gutsy-security/universe Packages              
Hit http://us.archive.ubuntu.com gutsy-security/multiverse Packages            
Get:5 http://download.tuxfamily.org gutsy Release.gpg [189B]                   
Ign http://download.tuxfamily.org gutsy/avant-window-navigator Translation-en_US
Ign http://packages.medibuntu.org gutsy/non-free Translation-en_US
Hit http://download.tuxfamily.org gutsy Release
Hit http://download.tuxfamily.org gutsy/avant-window-navigator Packages
Hit http://download.tuxfamily.org gutsy/avant-window-navigator Sources
Hit http://packages.medibuntu.org gutsy Release
Ign http://packages.medibuntu.org gutsy/free Packages
Ign http://packages.medibuntu.org gutsy/non-free Packages
Hit http://packages.medibuntu.org gutsy/free Packages
Hit http://packages.medibuntu.org gutsy/non-free Packages
Fetched 5B in 5s (1B/s)  
Bus error (core dumped). 0%

```

```
chris@chris-desktop:~$ sudo dpkg --configure -a 
chris@chris-desktop:~$ cat /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-security universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-security multiverse

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs

deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
# deb http://archive.ubuntustudio.org/ubuntustudio gutsy main
# deb-src http://archive.ubuntustudio.org/ubuntustudio gutsy main
deb http://download.skype.com/linux/repos/debian/ stable non-free

```

```
chris@chris-desktop:~$ sudo synaptic
Bus error (core dumped)

```

As you can see I've added some additional sources, although I didn't change anything since this problem began.

I'd just like to say that I really appreciate those who spend time helping users like myself.  Even if my issue doesn't get resolved, thank you for reading!  I hope I didn't ask a question that has been answered a lot, I would hate to waste anyone's time.

-Chris

---

### Post by CFBauer on 2007-12-10
If anyone has any suggestions for additional avenues to research this myself, I would certainly be interested.  Thanks!



Ok, ok, this is a shameless bump.

---

### Post by CFBauer on 2007-12-17
Not sure what the issue was, so I re-installed and everything is neat.

---

### Post by RichardCookson on 2008-01-19
Hi, I have exactly the same problem. How did the re-install go? Did you have to backup / restore your home directory? Did you lose anything in the re-install? Just wondering before I do the same thing.

Thanks in advance,

Richard Cookson.

---

### Post by Habo on 2008-02-18
I had similar problem and solution was to delete corrupted bin files in  /var/cache/apt/ directory as suggested on 
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/192567](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/192567)

So I hope it helps.

---

### Post by CFBauer on 2008-03-23
> **RichardCookson said:**
> Hi, I have exactly the same problem. How did the re-install go? Did you have to backup / restore your home directory? Did you lose anything in the re-install? Just wondering before I do the same thing.

Thanks in advance,

Richard Cookson.
Sorry Richard, I didn't see your reply until now.

My reinstall worked perfectly.  I kept my home directory and all my files / settings.

---

### Post by CFBauer on 2008-03-23
> **Habo said:**
> I had similar problem and solution was to delete corrupted bin files in  /var/cache/apt/ directory as suggested on 
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/192567](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/192567)

So I hope it helps.
I didn't think about a bug report.  Whenever something like this happens, weather it's warranted or not, I tend to assume it's my fault. :)

---

