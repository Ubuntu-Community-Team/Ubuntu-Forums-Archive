---
title: "Issues updating an old computer from Saucy to Trusty"
date: 2016-01-05
forum: General Help
---

### Post by tstack77 on 2016-01-05
I am trying to update a computer that hasn't been upgraded since early '14 and want to put it on a LTS release. I've tried updating the sources.list to point to 'us.old-releases.ubuntu.com' but am still having issues.

I ran

```
sudo sed -i -e 's/ca.archive.ubuntu.com\|security.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list

```

```
~$ sudo apt-get update

Err http://us.old-releases.ubuntu.com saucy InRelease
  
Err http://us.old-releases.ubuntu.com saucy-updates InRelease                  
  
Err http://us.old-releases.ubuntu.com saucy-backports InRelease                
  
Err http://us.old-releases.ubuntu.com saucy Release.gpg                        
  Could not resolve 'us.old-releases.ubuntu.com'
Err http://us.old-releases.ubuntu.com saucy-updates Release.gpg                
  Could not resolve 'us.old-releases.ubuntu.com'
Err http://us.old-releases.ubuntu.com saucy-backports Release.gpg              
  Could not resolve 'us.old-releases.ubuntu.com'
Ign http://old-releases.ubuntu.com saucy-security InRelease                    
Ign http://extras.ubuntu.com saucy InRelease                                   
Hit http://archive.canonical.com saucy InRelease                               
Ign http://ppa.launchpad.net saucy InRelease                                   
Ign http://dl.google.com stable InRelease                                      
Hit http://extras.ubuntu.com saucy Release.gpg                                 
Hit http://old-releases.ubuntu.com saucy-security Release.gpg                  
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Hit http://archive.canonical.com saucy/partner amd64 Packages                  
Hit http://dl.google.com stable Release.gpg                                    
Hit http://extras.ubuntu.com saucy Release                                     
Hit http://old-releases.ubuntu.com saucy-security Release                      
Hit http://ppa.launchpad.net saucy Release                                     
Hit http://dl.google.com stable Release                                        
Hit http://archive.canonical.com saucy/partner i386 Packages                   
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://extras.ubuntu.com saucy/main Sources                                
Hit http://old-releases.ubuntu.com saucy-security/main Sources                 
Hit http://ppa.launchpad.net saucy/main amd64 Packages                         
Hit http://extras.ubuntu.com saucy/main amd64 Packages                         
Hit http://old-releases.ubuntu.com saucy-security/restricted Sources           
Hit http://ppa.launchpad.net saucy/main i386 Packages                          
Hit http://extras.ubuntu.com saucy/main i386 Packages                          
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://old-releases.ubuntu.com saucy-security/universe Sources             
Hit http://old-releases.ubuntu.com saucy-security/multiverse Sources           
Hit http://old-releases.ubuntu.com saucy-security/main amd64 Packages          
Hit http://old-releases.ubuntu.com saucy-security/restricted amd64 Packages    
Hit http://old-releases.ubuntu.com saucy-security/universe amd64 Packages      
Hit http://old-releases.ubuntu.com saucy-security/multiverse amd64 Packages    
Hit http://old-releases.ubuntu.com saucy-security/main i386 Packages           
Ign http://archive.canonical.com saucy/partner Translation-en_US               
Hit http://old-releases.ubuntu.com saucy-security/restricted i386 Packages     
Ign http://archive.canonical.com saucy/partner Translation-en                  
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://old-releases.ubuntu.com saucy-security/universe i386 Packages       
Ign http://extras.ubuntu.com saucy/main Translation-en_US            
Ign http://ppa.launchpad.net saucy/main Translation-en_US            
Hit http://old-releases.ubuntu.com saucy-security/multiverse i386 Packages
Ign http://dl.google.com stable/main Translation-en                            
Ign http://extras.ubuntu.com saucy/main Translation-en                         
Ign http://ppa.launchpad.net saucy/main Translation-en               
Hit http://old-releases.ubuntu.com saucy-security/main Translation-en
Hit http://old-releases.ubuntu.com saucy-security/multiverse Translation-en
Hit http://old-releases.ubuntu.com saucy-security/restricted Translation-en
Hit http://old-releases.ubuntu.com saucy-security/universe Translation-en
Ign http://old-releases.ubuntu.com saucy-security/main Translation-en_US
Ign http://old-releases.ubuntu.com saucy-security/multiverse Translation-en_US
Ign http://old-releases.ubuntu.com saucy-security/restricted Translation-en_US
Ign http://old-releases.ubuntu.com saucy-security/universe Translation-en_US
Reading package lists... Done
W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/saucy/InRelease  

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/saucy-updates/InRelease  

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/saucy-backports/InRelease  

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/saucy/Release.gpg  Could not resolve 'us.old-releases.ubuntu.com'

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/saucy-updates/Release.gpg  Could not resolve 'us.old-releases.ubuntu.com'

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/saucy-backports/Release.gpg  Could not resolve 'us.old-releases.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

Seems the problem is **Could not resolve 'us.old-releases.ubuntu.com'**

Google has gotten me this far but I can't find any other workaround beyond pointing to old-releases. Any ideas?

---

### Post by tstack77 on 2016-01-05
Nevermind, I realized that us.old-releases.ubuntu.com is down (or never existed?) and simply deleted all "us." prefixes from sources.list. It's updating as I type this.

---

### Post by howefield on 2016-01-05
Try removing the us. from the repository info.. ie make

```
http://us.old-releases.ubuntu.com saucy
```

look like

```
http://old-releases.ubuntu.com saucy
```

---

### Post by howefield on 2016-01-05
> **tstack77 said:**
> Nevermind, I realized that us.old-releases.ubuntu.com is down (or never existed?) and simply deleted all "us." prefixes from sources.list. It's updating as I type this.

You got it, never existed.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by tstack77 on 2016-01-05
Haha, nice to almost solve it on my own. Unfortunately now I'm not receiving a prompt from the upgrade manager or finding anything using the terminal.

```

~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

```
~$ sudo do-release-upgrade
Checking for a new Ubuntu release
No new release found
```

```
~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy

```

---

### Post by Bashing-om on 2016-01-05
tstack77; Hello;

Verify that the /etc/source.list file is in proper format.
the field " [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) " is set in all instances AND that the 'code name' is that of the install that you are upgrading FROM .
then in terminal all that should be required is :
```

sudo apt-get update
sudo apt-get dist-upgrade
sudo do-release-upgrade

```
where :
 " update ' syncs the data bases;
" dist-upgrade " deals with the installed package upgrades that a general "upgrade" does not handle;
" do-release-upgrade" will perform the actual release upgrade.

Make sure that - if used - the proprietary graphics driver is reverted to open source AND my best advise that all other PPAs are reverted to packages in the software repository. There is no guarantee that a packaged PPA will have support in the next release !  Possible that you will drive the package manager nuts trying to deal with packages it can not deal with .

Lastly ; disable any screen savers . 

Now you are ready to DO IT.

Be aware, doing as above, I have never ever had a problem doing a release upgrade. 

[INDENT][INDENT]My bit to try and help
[/INDENT][/INDENT]

---

### Post by tstack77 on 2016-01-05
Everything looks to be properly formatted but I still cannot find/force the upgrade. As an aside, great tip about reverting proprietary drivers, I've never heard that one.


```
# deb cdrom:[Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1)]/ saucy main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://old-releases.ubuntu.com/ubuntu/ saucy main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ saucy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://old-releases.ubuntu.com/ubuntu/ saucy-updates main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ saucy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://old-releases.ubuntu.com/ubuntu/ saucy universe
deb-src http://old-releases.ubuntu.com/ubuntu/ saucy universe
deb http://old-releases.ubuntu.com/ubuntu/ saucy-updates universe
deb-src http://old-releases.ubuntu.com/ubuntu/ saucy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://old-releases.ubuntu.com/ubuntu/ saucy multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ saucy multiverse
deb http://old-releases.ubuntu.com/ubuntu/ saucy-updates multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ saucy-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://old-releases.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse

deb http://old-releases.ubuntu.com/ubuntu saucy-security main restricted
deb-src http://old-releases.ubuntu.com/ubuntu saucy-security main restricted
deb http://old-releases.ubuntu.com/ubuntu saucy-security universe
deb-src http://old-releases.ubuntu.com/ubuntu saucy-security universe
deb http://old-releases.ubuntu.com/ubuntu saucy-security multiverse
deb-src http://old-releases.ubuntu.com/ubuntu saucy-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu saucy partner
# deb-src http://archive.canonical.com/ubuntu saucy partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu saucy main
deb-src http://extras.ubuntu.com/ubuntu saucy main
```

---

### Post by howefield on 2016-01-05
You probably have but might be worth checking that you have the update-manager and update-manager-core packages installed.

---

### Post by tstack77 on 2016-01-05
Made sense but both are installed and "already the newest version". This is very strange. I would just install it manually at this point if it wasn't my mother's computer and intricately setup.

---

### Post by tstack77 on 2016-01-05
SOLVED!

For some reason the **Notify me of new Ubuntu version** setting has to be **For any new version**. I had LTS only thinking it would skip to 15.10.  After changing that dist-upgrade and release-upgrade are working (and only updating to trusty).

For anyone else reading this in the future, this can also be done in terminal by making Prompt=normal in /etc/update-manager/release-upgrades

Thanks for all the help!

---

### Post by Bashing-om on 2016-01-05
tstack77; Outstanding !

You do good work .
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

