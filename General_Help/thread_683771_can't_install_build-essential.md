---
title: "can't install build-essential"
date: 2008-01-31
forum: General Help
---

### Post by Vaelrith on 2008-01-31
I've tried the suggestions of the other threads I found on this topic, but nothing helped.

When I try to install build-essential so that I can upgrade to the new nvidia driver, I get this error:

```
build-essential:
 Depends: libc6-dev but it is not going to be installed or
	libc-dev
 Depends: g++ but it is not going to be installed
```

I'm guessing it's something wrong with my sources list, but I don't know...

Thanks for the help.

---

### Post by FuturePilot on 2008-01-31
Can you post your sources.list
```
cat /etc/apt/sources.list
```

---

### Post by Vaelrith on 2008-01-31
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

---

### Post by EXCiD3 on 2008-01-31
Did you use synaptic or apt-get to install?

---

### Post by taurus on 2008-01-31
```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by Vaelrith on 2008-01-31
Exide: I tried both

taurus: Tried that, didn't work.

---

### Post by wirelessmonkey on 2008-01-31
Please post the output from those commands, so we can troubleshoot.

---

### Post by Vaelrith on 2008-01-31
```
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 http://us.archive.ubuntu.com gutsy Release.gpg [191B]                    
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US                  
Get:2 http://archive.ubuntu.com gutsy Release.gpg [191B]                       
Get:3 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Get:4 http://archive.canonical.com gutsy Release.gpg [191B]          
Ign http://archive.canonical.com gutsy/partner Translation-en_US               
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US    
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US  
Get:5 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]            
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US    
Hit http://archive.ubuntu.com gutsy Release                                    
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US       
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com gutsy-security Release                          
Get:6 http://archive.canonical.com gutsy Release [6998B]                       
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com gutsy Release                            
Hit http://archive.ubuntu.com gutsy/main Sources                               
Hit http://security.ubuntu.com gutsy-security/main Packages                    
Hit http://us.archive.ubuntu.com gutsy-updates Release                    
Hit http://archive.ubuntu.com gutsy/restricted Sources                         
Hit http://security.ubuntu.com gutsy-security/restricted Packages              
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://us.archive.ubuntu.com gutsy/main Packages                 
Hit http://us.archive.ubuntu.com gutsy/restricted Packages           
Hit http://us.archive.ubuntu.com gutsy/restricted Sources            
Hit http://security.ubuntu.com gutsy-security/multiverse Sources     
Hit http://security.ubuntu.com gutsy-security/universe Sources       
Hit http://security.ubuntu.com gutsy-security/universe Packages      
Hit http://security.ubuntu.com gutsy-security/multiverse Packages    
Get:7 http://archive.canonical.com gutsy/partner Packages [3658B]    
Hit http://us.archive.ubuntu.com gutsy/main Sources  
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/universe Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Get:8 http://archive.canonical.com gutsy/partner Sources [1393B]
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Fetched 12.2kB in 1s (10.7kB/s)
Reading package lists... Done
W: Duplicate sources.list entry http://archive.canonical.com gutsy/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_gutsy_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```

I did update again and the part about duplicate sosurces.list entry isn't there.  Intalling build-essential still gives the same error as before.

---

### Post by EXCiD3 on 2008-01-31
In the Administration->Software Sources, make sure you uncheck to use the Gutsy disc as a software source. This might be causing the problem. You can also edit out the disc from your sources.list file too instead.

---

### Post by Vaelrith on 2008-01-31
Still not working...

---

### Post by taurus on 2008-01-31
Can you at least run "sudo apt-get update" a couple of times?

---

### Post by Vaelrith on 2008-01-31
I did update 5 times, then tried to install build-essential and I still get the same error.

---

### Post by taurus on 2008-01-31
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and put a # in front of these two lines to comment them out.

```

**#**deb http://archive.canonical.com/ubuntu gutsy partner
**#**deb-src http://archive.canonical.com/ubuntu gutsy partner

```
Save it and then run

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by Vaelrith on 2008-01-31
didn't work, same error message.

---

### Post by zvacet on 2008-01-31
Insert disc in drive and type in terminal

```
sudo apt-cdrom add
```

```
sudo apt-get install build-essential
```

---

### Post by Vaelrith on 2008-01-31
nope...

---

### Post by mc4man on 2008-01-31
Is the error message still the same as in first post?

---

### Post by Vaelrith on 2008-01-31
> **mc4man said:**
> Is the error message still the same as in first post?

Yes :(

---

### Post by mc4man on 2008-01-31
I'm not suggesting you do anything but for the sake of gathering some info I'd go into synaptic and do a search on gcc, g++, libc6, and for the hell of it build-essential. There will be multiple listings for most of them, what you want to see is what is installed and what versions. I've got to out for a while, but there's much smarter people than me here, possibly some of that info may be relevant
will ck. back

---

### Post by Vaelrith on 2008-01-31
Thanks mc4man

gcc: installed, version 4:4.1.2-9ubuntu2
g++: not installed, when trying to install it says it depends on g++-4.1, when trying to install that it says it depends on libstdv++6-4.1-dev.  When trying to install that I get:
```
libstdc++6-4.1-dev:
 Depends: g++-4.1 but it is not going to be installed
 Depends: libc6-dev but it is not going to be installed
```
libc6: installed, version 2.7-5
libc6-dev: not installed, get this error:
```
libc6-dev:
  Depends: libc6 (=2.6.1-1ubuntu10) but 2.7-5 is to be installed
```

---

### Post by taurus on 2008-01-31
Try this.  Make a back up copy of your /etc/apt/sources.list.

```
sudo cp /etc/apt/sources.list  /etc/apt/sources.list.orig
```
Then, edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of all the lines _except_ the first one, cdrom.  Save it and close down gedit window.  Now, what happens when you run these two commands from a terminal?

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by mc4man on 2008-01-31
This is beyond me so I can't comment further but I am curious as to where this came from
> libc6: installed, version 2.7-5

---

### Post by Vaelrith on 2008-01-31
taurus, still same problem... This is really weird...

---

### Post by mc4man on 2008-01-31
Well i can't help but say that you're not going to install the packages you want with that version of libc6. I would think you'd have to either get back to ver. 2.6.1 or find packages that work with 2.7-5

---

### Post by Vaelrith on 2008-01-31
If I try to remove libc6, it says that there will be a whole whole lot of other packages removed too.  I'm not sure what libc6 does, but it seems pretty vital.  Is there a way I can downgrade it without completely removing it?

---

### Post by mc4man on 2008-02-01
i certainly don't think you'd want to remove it, hopefully someone more knowledgeable will come along to advise you. If you didn't care about possibly having to do a reinstall you may be able to force ver. 2.6.1  Might be more useful to first figure out how or why you got the version you have.

edit:
are there any entries in your gui of software sources under 3rd party that aren't in the list you posted ?

---

### Post by Vaelrith on 2008-02-01
Meh, I just did a reinstall.  It works now :)

---

### Post by matthewcraig on 2008-02-01
Just curious, but what did you reinstall ?
I've seen this error, but I never bothered to track down the source of the issue.

---

### Post by Vaelrith on 2008-02-01
I just reinstalled the same version I had, Ubuntu 7.10 i386.

---

