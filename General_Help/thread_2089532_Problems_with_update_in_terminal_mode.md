---
title: "Problems with update in terminal mode"
date: 2012-11-29
forum: General Help
---

### Post by thedoctor81877 on 2012-11-29
When I try to update using the terminmal, I get the following:

```
thedoctor@thedoctorstardis:~$ sudo apt-get upgrade
[sudo] password for thedoctor: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ quantal/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_quantal_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
thedoctor@thedoctorstardis:~$ sudo apt-get update
Ign http://mirror.umd.edu quantal InRelease
Ign http://us.archive.ubuntu.com precise-proposed InRelease                                         
Ign http://mirror.umd.edu quantal-updates InRelease                                                 
Ign http://us.archive.ubuntu.com precise-updates InRelease                                          
Ign http://mirror.umd.edu quantal-backports InRelease                                               
Ign http://us.archive.ubuntu.com precise-backports InRelease                                        
Ign http://dl.google.com stable InRelease                                                           
Ign http://mirror.umd.edu quantal-security InRelease                                                
Ign http://ppa.launchpad.net quantal InRelease                                                      
Ign http://security.ubuntu.com precise-security InRelease                                           
Ign http://archive.canonical.com quantal InRelease                                                  
Hit http://us.archive.ubuntu.com precise-proposed Release.gpg                                       
Ign http://mirror.umd.edu quantal-proposed InRelease                                                
Ign http://extras.ubuntu.com quantal InRelease                                                      
Hit http://mirror.umd.edu quantal Release.gpg                                                       
Hit http://us.archive.ubuntu.com precise-updates Release.gpg                                        
Hit http://mirror.umd.edu quantal-updates Release.gpg                                               
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                                      
Ign http://ppa.launchpad.net quantal InRelease                                                      
Hit http://security.ubuntu.com precise-security Release.gpg                                         
Ign http://archive.canonical.com [distro] InRelease                                                 
Hit http://mirror.umd.edu quantal-backports Release.gpg                                             
Hit http://extras.ubuntu.com quantal Release.gpg                                                    
Hit http://us.archive.ubuntu.com precise-proposed Release                                           
Hit http://mirror.umd.edu quantal-security Release.gpg                                              
Hit http://us.archive.ubuntu.com precise-updates Release                                            
Hit http://mirror.umd.edu quantal-proposed Release.gpg                                              
Ign http://ppa.launchpad.net quantal InRelease                                                      
Hit http://mirror.umd.edu quantal Release                                                           
Hit http://security.ubuntu.com precise-security Release                                             
Hit http://us.archive.ubuntu.com precise-backports Release                                          
Hit http://archive.canonical.com quantal Release.gpg                                                
Hit http://extras.ubuntu.com quantal Release                                                        
Hit http://mirror.umd.edu quantal-updates Release                                                   
Hit http://mirror.umd.edu quantal-backports Release                                                 
Hit http://us.archive.ubuntu.com precise-proposed/universe i386 Packages                            
Ign http://ppa.launchpad.net quantal InRelease                                                      
Hit http://mirror.umd.edu quantal-security Release                                                  
Ign http://archive.canonical.com [distro] Release.gpg                                               
Hit http://us.archive.ubuntu.com precise-proposed/main i386 Packages                                
Hit http://mirror.umd.edu quantal-proposed Release                                                  
Hit http://security.ubuntu.com precise-security/universe i386 Packages                              
Hit http://mirror.umd.edu quantal/restricted Sources                                                
Hit http://us.archive.ubuntu.com precise-proposed/multiverse i386 Packages                          
Hit http://extras.ubuntu.com quantal/main Sources                                                   
Hit http://mirror.umd.edu quantal/main Sources                                                      
Ign http://ppa.launchpad.net quantal InRelease                                                      
Hit http://us.archive.ubuntu.com precise-proposed/restricted i386 Packages                          
Hit http://archive.canonical.com quantal Release                                                    
Hit http://mirror.umd.edu quantal/multiverse Sources                                                
Hit http://security.ubuntu.com precise-security/main i386 Packages                                  
Hit http://us.archive.ubuntu.com precise-proposed/main Translation-en                               
Hit http://extras.ubuntu.com quantal/main i386 Packages                                             
Ign http://ppa.launchpad.net quantal InRelease                                                      
Ign http://archive.canonical.com [distro] Release                                                   
Hit http://mirror.umd.edu quantal/universe Sources                                                  
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages                            
Hit http://mirror.umd.edu quantal/restricted i386 Packages                                          
Hit http://us.archive.ubuntu.com precise-proposed/multiverse Translation-en                         
Hit http://mirror.umd.edu quantal/main i386 Packages                                                
Hit http://ppa.launchpad.net quantal Release.gpg                                                    
Hit http://archive.canonical.com quantal/partner Sources                                            
Hit http://mirror.umd.edu quantal/universe i386 Packages                                            
Hit http://security.ubuntu.com precise-security/restricted i386 Packages                            
Hit http://mirror.umd.edu quantal/multiverse i386 Packages                                          
Hit http://ppa.launchpad.net quantal Release.gpg                                                    
Hit http://archive.canonical.com quantal/partner i386 Packages                                      
Hit http://us.archive.ubuntu.com precise-proposed/restricted Translation-en                         
Hit http://mirror.umd.edu quantal/main Translation-en                                               
Hit http://dl.google.com stable Release.gpg                                                         
Hit http://mirror.umd.edu quantal/multiverse Translation-en                                         
Hit http://ppa.launchpad.net quantal Release.gpg                                                    
Hit http://us.archive.ubuntu.com precise-proposed/universe Translation-en                           
Hit http://dl.google.com stable Release                                                             
Hit http://security.ubuntu.com precise-security/main Translation-en                                 
Hit http://mirror.umd.edu quantal/restricted Translation-en                                         
Hit http://us.archive.ubuntu.com precise-updates/universe i386 Packages                             
Hit http://ppa.launchpad.net quantal Release.gpg                                                    
Hit http://us.archive.ubuntu.com precise-updates/main i386 Packages                                 
Hit http://mirror.umd.edu quantal/universe Translation-en                                           
Hit http://dl.google.com stable/main i386 Packages                                                  
Hit http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages                           
Hit http://mirror.umd.edu quantal-updates/restricted Sources                                        
Hit http://mirror.umd.edu quantal-updates/main Sources                                              
Hit http://us.archive.ubuntu.com precise-updates/restricted i386 Packages                           
Ign http://ppa.launchpad.net quantal Release.gpg                                                    
Hit http://mirror.umd.edu quantal-updates/multiverse Sources                                        
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                           
Hit http://mirror.umd.edu quantal-updates/universe Sources                                          
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en                                
Hit http://ppa.launchpad.net quantal Release.gpg                                                    
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en                          
Hit http://mirror.umd.edu quantal-updates/restricted i386 Packages                                  
Hit http://ppa.launchpad.net quantal Release                                                        
Hit http://mirror.umd.edu quantal-updates/main i386 Packages                                        
Hit http://mirror.umd.edu quantal-updates/universe i386 Packages                                    
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en                          
Hit http://security.ubuntu.com precise-security/restricted Translation-en                           
Hit http://mirror.umd.edu quantal-updates/multiverse i386 Packages                                  
Hit http://ppa.launchpad.net quantal Release                                                        
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en                            
Hit http://mirror.umd.edu quantal-updates/main Translation-en                                       
Ign http://extras.ubuntu.com quantal/main Translation-en_US                                         
Hit http://mirror.umd.edu quantal-updates/multiverse Translation-en                                 
Hit http://ppa.launchpad.net quantal Release                                                        
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages                           
Hit http://security.ubuntu.com precise-security/universe Translation-en                             
Hit http://mirror.umd.edu quantal-updates/restricted Translation-en                                 
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages                               
Ign http://extras.ubuntu.com quantal/main Translation-en                                            
Hit http://ppa.launchpad.net quantal Release                                                        
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages                         
Hit http://mirror.umd.edu quantal-updates/universe Translation-en                                   
Ign http://dl.google.com stable/main Translation-en_US                                              
Hit http://mirror.umd.edu quantal-backports/restricted Sources                                      
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages                         
Hit http://mirror.umd.edu quantal-backports/universe Sources                                        
Ign http://ppa.launchpad.net quantal Release                                                        
Hit http://mirror.umd.edu quantal-backports/multiverse Sources                                      
Ign http://dl.google.com stable/main Translation-en                                                 
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en                              
Hit http://mirror.umd.edu quantal-backports/main Sources                                            
Hit http://mirror.umd.edu quantal-backports/restricted i386 Packages                       
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en                        
Hit http://mirror.umd.edu quantal-backports/universe i386 Packages                                  
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en               
Hit http://mirror.umd.edu quantal-backports/multiverse i386 Packages                                
Hit http://ppa.launchpad.net quantal Release                                                        
Hit http://mirror.umd.edu quantal-backports/main i386 Packages                                      
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en                          
Hit http://mirror.umd.edu quantal-backports/main Translation-en                            
Hit http://ppa.launchpad.net quantal/main Sources                                          
Hit http://mirror.umd.edu quantal-backports/multiverse Translation-en                               
Hit http://ppa.launchpad.net quantal/main i386 Packages                                             
Hit http://mirror.umd.edu quantal-backports/restricted Translation-en                               
Hit http://mirror.umd.edu quantal-backports/universe Translation-en                                 
Hit http://mirror.umd.edu quantal-security/restricted Sources                                       
Hit http://mirror.umd.edu quantal-security/main Sources                                             
Hit http://mirror.umd.edu quantal-security/multiverse Sources                                       
Hit http://mirror.umd.edu quantal-security/universe Sources                                         
Hit http://mirror.umd.edu quantal-security/restricted i386 Packages                                 
Hit http://mirror.umd.edu quantal-security/main i386 Packages                                       
Hit http://ppa.launchpad.net quantal/main Sources                                                   
Hit http://mirror.umd.edu quantal-security/universe i386 Packages                                   
Hit http://mirror.umd.edu quantal-security/multiverse i386 Packages                                 
Hit http://ppa.launchpad.net quantal/main i386 Packages                                    
Hit http://mirror.umd.edu quantal-security/main Translation-en                             
Hit http://mirror.umd.edu quantal-security/multiverse Translation-en                       
Hit http://mirror.umd.edu quantal-security/restricted Translation-en                                
Hit http://mirror.umd.edu quantal-security/universe Translation-en                                  
Hit http://ppa.launchpad.net quantal/main Sources                                          
Hit http://mirror.umd.edu quantal-proposed/restricted Sources                              
Hit http://mirror.umd.edu quantal-proposed/multiverse Sources                                       
Hit http://mirror.umd.edu quantal-proposed/universe Sources                                         
Hit http://ppa.launchpad.net quantal/main i386 Packages                                             
Hit http://mirror.umd.edu quantal-proposed/main Sources                                             
Ign http://security.ubuntu.com precise-security/main Translation-en_US                              
Hit http://mirror.umd.edu quantal-proposed/restricted i386 Packages                                 
Hit http://mirror.umd.edu quantal-proposed/multiverse i386 Packages                        
Hit http://mirror.umd.edu quantal-proposed/universe i386 Packages                                   
Ign http://security.ubuntu.com precise-security/multiverse Translation-en_US                        
Ign http://security.ubuntu.com precise-security/restricted Translation-en_US                        
Hit http://mirror.umd.edu quantal-proposed/main i386 Packages                                       
Hit http://mirror.umd.edu quantal-proposed/main Translation-en                                      
Hit http://ppa.launchpad.net quantal/main Sources                                          
Ign http://security.ubuntu.com precise-security/universe Translation-en_US                          
Hit http://mirror.umd.edu quantal-proposed/multiverse Translation-en                                
Hit http://ppa.launchpad.net quantal/main i386 Packages                                    
Hit http://mirror.umd.edu quantal-proposed/restricted Translation-en 
Ign http://archive.canonical.com quantal/partner Translation-en_US   
Hit http://mirror.umd.edu quantal-proposed/universe Translation-en   
Ign http://archive.canonical.com quantal/partner Translation-en                            
Err http://archive.canonical.com [distro]/partner Sources                                  
  404  Not Found [IP: 91.189.92.191 80]
Err http://archive.canonical.com [distro]/partner i386 Packages      
  404  Not Found [IP: 91.189.92.191 80]
Ign http://us.archive.ubuntu.com precise-proposed/main Translation-en_US                   
Ign http://archive.canonical.com [distro]/partner Translation-en_US                        
Ign http://us.archive.ubuntu.com precise-proposed/multiverse Translation-en_US             
Ign http://archive.canonical.com [distro]/partner Translation-en                           
Ign http://us.archive.ubuntu.com precise-proposed/restricted Translation-en_US
Ign http://us.archive.ubuntu.com precise-proposed/universe Translation-en_US
Ign http://us.archive.ubuntu.com precise-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com precise-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com precise-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com precise-updates/universe Translation-en_US
Hit http://ppa.launchpad.net quantal/main Sources                    
Hit http://ppa.launchpad.net quantal/main i386 Packages
Ign http://us.archive.ubuntu.com precise-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com precise-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com precise-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com precise-backports/universe Translation-en_US
Ign http://mirror.umd.edu quantal/main Translation-en_US
Ign http://mirror.umd.edu quantal/multiverse Translation-en_US
Ign http://mirror.umd.edu quantal/restricted Translation-en_US
Ign http://mirror.umd.edu quantal/universe Translation-en_US
Ign http://mirror.umd.edu quantal-updates/main Translation-en_US
Ign http://mirror.umd.edu quantal-updates/multiverse Translation-en_US
Ign http://mirror.umd.edu quantal-updates/restricted Translation-en_US
Ign http://mirror.umd.edu quantal-updates/universe Translation-en_US
Ign http://mirror.umd.edu quantal-backports/main Translation-en_US
Ign http://mirror.umd.edu quantal-backports/multiverse Translation-en_US
Ign http://mirror.umd.edu quantal-backports/restricted Translation-en_US
Ign http://mirror.umd.edu quantal-backports/universe Translation-en_US
Ign http://mirror.umd.edu quantal-security/main Translation-en_US
Ign http://mirror.umd.edu quantal-security/multiverse Translation-en_US
Ign http://mirror.umd.edu quantal-security/restricted Translation-en_US
Ign http://mirror.umd.edu quantal-security/universe Translation-en_US
Ign http://mirror.umd.edu quantal-proposed/main Translation-en_US
Ign http://mirror.umd.edu quantal-proposed/multiverse Translation-en_US
Ign http://mirror.umd.edu quantal-proposed/restricted Translation-en_US
Ign http://mirror.umd.edu quantal-proposed/universe Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Err http://ppa.launchpad.net quantal/main Sources
  404  Not Found
Err http://ppa.launchpad.net quantal/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
W: Failed to fetch http://archive.canonical.com/dists/[distro]/partner/source/Sources  404  Not Found [IP: 91.189.92.191 80]

W: Failed to fetch http://archive.canonical.com/dists/[distro]/partner/binary-i386/Packages  404  Not Found [IP: 91.189.92.191 80]

W: Failed to fetch http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
thedoctor@thedoctorstardis:~$ /etc/apt/sources.list

```

---

### Post by thedoctor81877 on 2012-11-29
The following is the content of my [B]/etc/apt/sources.list
[/B]
```


# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mirror.umd.edu/ubuntu/ quantal restricted main
deb-src http://mirror.umd.edu/ubuntu/ quantal restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.umd.edu/ubuntu/ quantal-updates restricted main
deb-src http://mirror.umd.edu/ubuntu/ quantal-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.umd.edu/ubuntu/ quantal universe
deb http://mirror.umd.edu/ubuntu/ quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.umd.edu/ubuntu/ quantal multiverse
deb http://mirror.umd.edu/ubuntu/ quantal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirror.umd.edu/ubuntu/ quantal-backports restricted universe multiverse main
deb-src http://mirror.umd.edu/ubuntu/ quantal-backports restricted universe multiverse main #Added by software-properties

deb http://mirror.umd.edu/ubuntu/ quantal-security restricted main
deb-src http://mirror.umd.edu/ubuntu/ quantal-security restricted main multiverse universe #Added by software-properties
deb http://mirror.umd.edu/ubuntu/ quantal-security universe
deb http://mirror.umd.edu/ubuntu/ quantal-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu quantal partner
deb-src http://archive.canonical.com/ubuntu quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu quantal main
deb-src http://extras.ubuntu.com/ubuntu quantal main
deb http://mirror.umd.edu/ubuntu/ quantal-proposed restricted multiverse universe main
deb-src http://mirror.umd.edu/ubuntu/ quantal-proposed restricted multiverse universe main #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ precise-security universe main multiverse restricted
deb http://us.archive.ubuntu.com/ubuntu/ precise-proposed universe main multiverse restricted
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe main multiverse restricted
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports universe main multiverse restricted
deb http://archive.canonical.com/ [distro] partner
deb-src http://archive.canonical.com/ [distro] partner
# deb http://archive.canonical.com/ quantal partner
# deb-src http://archive.canonical.com/ quantal partner

# deb http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu lucid main
# deb-src http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu lucid main


```

---

### Post by plucky on 2012-11-29
> deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security universe main multiverse restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-proposed universe main multiverse restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe main multiverse restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports universe main multiverse restricted
deb [http://archive.canonical.com/](http://archive.canonical.com/) [distro] partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) [distro] partner

and also > Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages
  404  Not Found


Remove all those from your sources.list then run the update again.

Good Luck

---

### Post by thedoctor81877 on 2012-11-29
Please forgive my ignorance, but how to I delete repositories from that file? Thanks.

---

### Post by SeijiSensei on 2012-11-29
I recommend that beginners use the nano editor which comes with Ubuntu by default.  Open a terminal, then type "sudo nano /etc/apt/sources.list".  You'll see a menu of commands at the bottom of the screen, all of which are "control-key" combinations where you hold down the Ctrl key (represented as "^") and type a letter.  To delete a line use Ctrl-K.  Use ^S^X to save the file and exit when you are done.

I have one annoyance with nano: ^K deletes the entire line rather than the text from the cursor to the end of the line as is common in other editors like Emacs and jed.  (I use the latter in Emacs mode, but you need to have memorized a lot of control-key sequences to be proficient.)  For beginners, nano is the best choice because it has menus and decent help.

---

### Post by thedoctor81877 on 2012-11-29
Many thanks to SeijiSensi, and plucky for all your help in this matter. However, [upon removing the mentioned sources] I now am getting the following:

```


W: Failed to fetch http://archive.canonical.com/dists/[distro]/partner/source/Sources  404  Not Found [IP: 91.189.92.150 80]

W: Failed to fetch http://archive.canonical.com/dists/[distro]/partner/binary-i386/Packages  404  Not Found [IP: 91.189.92.150 80]

W: Failed to fetch http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.



```

Thanks again!!!

---

### Post by oldfred on 2012-11-29
Similar issue.

All the sources must be to your current version. [distro] then is supposed to be your current version. But I would comment out all four lines.  # as first character converts to comment.

Why a ppa for Thunderbird. Ubuntu currently updates to the new version almost as soon as released now.

---

### Post by SeijiSensei on 2012-11-29
> **thedoctor81877 said:**
> 
```

W: Failed to fetch http://archive.canonical.com/dists/[distro]/partner/source/Sources  404  Not Found [IP: 91.189.92.150 80]

W: Failed to fetch http://archive.canonical.com/dists/[distro]/partner/binary-i386/Packages  404  Not Found [IP: 91.189.92.150 80]

```

If the string "[distro]" really appears in the entries in sources.list, it needs to be replaced with the actual name of the distro, "quantal" in your case.

> ```

W: Failed to fetch http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/quantal/main/source/Sources  404  Not Found

```

There's no need to include support for the source code repos unless you intend to recompile the applications yourself.  Either delete them, or put a hash mark ("#") at the beginning of the line to disable them.  However you should just delete this one because....

> ```

W: Failed to fetch http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

```

If you try opening that URL with a web browser, you'll see that it fails.  In fact, browsing up the tree shows there is nothing in the "dists" directory at all.  Just delete this one and use the version of Thunderbird in the standard repos.

---

### Post by thedoctor81877 on 2012-11-29
Thank you, oldfred as well. I just have one last thing. Upon following the advice given here, I still am getting the following:

```

W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ quantal/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_quantal_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

and I am not seeing these lines in the /etc/apt/sources.list at all. 

Thanks again!

---

### Post by thedoctor81877 on 2012-11-29
Oh, now I see those lines 

```

# deb http://archive.canonical.com/ [distro] partner
# deb-src http://archive.canonical.com/ [distro] partner

```

but they are hashed out. So, should I uncomment them? I am feeling really stupid [concerning Ubuntu and Linux in general] at the moment, and please forgive me missing obvious things. 

Thanks for all your patience and help!!!

---

### Post by plucky on 2012-11-29
> **thedoctor81877 said:**
> Oh, now I see those lines 

```

# deb http://archive.canonical.com/ [distro] partner
# deb-src http://archive.canonical.com/ [distro] partner

```

but they are hashed out. So, should I uncomment them? I am feeling really stupid [concerning Ubuntu and Linux in general] at the moment, and please forgive me missing obvious things. 

Thanks for all your patience and help!!!

No,leave them with the # so they don't cause further problems.Or delete them from the sources.list file.


> W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) quantal/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_quantal_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

I think that problem is caused by the [distro] line being in sources.list and has left an incorrect file in your .list files.

To correct the error,open a terminal and run ```
sudo rm /var/lib/apt/lists/* -vf
``` to delete the .list files and then run ```
sudo apt-get update
``` to reload the .list files.

Good Luck

---

### Post by thedoctor81877 on 2012-11-30
Thank you plucky, and everyone else who has helped me to fix this problem!

---

