---
title: "Kubuntu 14.04 updates"
date: 2016-04-23
forum: General Help
---

### Post by Garry_Knight on 2016-04-23
I'm asking this on behalf of a friend who runs Kubuntu 14.04. For various reasons I haven't used Linux for some years and am getting a bit rusty but I think I know how to help her with some help from you.

She used to get notifications for new software updates but hasn't had any for some time. A couple of messages have been flashing up on the left side of the screen but they disappear too quickly for her to do a screen capture and she can't remember what they said. It happened while I was at the computer and one of them was from Apper but it was gone before I could read it.

So I tried a few things to find out what's going on. First I ran Muon Update Manager. It put up a message, "Last check for updates was over a week ago." but it gives no indication of when the last check was. Manually checking for updates gives the message, "E: Some index files failed to download. They have been ignored or old ones used instead." But it gives no indication as to which index files failed to download.

I then ran Muon Package Manager and ran a check for updates. It seemed to try to download the package lists then ended with the message, "Could not download packages". But it didn't say which ones and the Details button showed nothing.

So I ran Synaptic Package Manager and did a Reload. I got the same message, "E: Some files failed to download..." that I got with Muon Update Manager.

Lastly, I ran 'sudo apt-get update' in Konsole. I could see the lists it tried to retrieve and most of the items started with "Hit" but some started with "Ign" (ignore?). And again, I got the same "E: some files failed to download..." message. And again, there was no indication as to which ones failed. Unless that 'Ign' prefix was a clue?

I checked Muon Update Managers settings and "Show notifications for available updates" is checked.

So, my questions are:

1) How can I find out which sources lists failed to update?
2) How can I fix this?
3) How can I prevent it happening again?
4) How can I fix it so that she gets automatic notifications when updates are available?&#65279;

---

### Post by oldos2er on 2016-04-24
We need some info copy/pasted from her konsole here, if possible: ```
cat /etc/apt/sources.list

ls /etc/apt/sources.list.d/

sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Garry_Knight on 2016-04-24
Thanks for your reply oldos2er, and thanks for any help you can give.

The output of cat /etc/apt/sources.list
--------------------------------------
```
# deb cdrom:[Kubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
```


The output of ls /etc/apt/sources.list.d/
--------------------------------------
```
arctica0316-ppa-precise.list
arctica0316-ppa-precise.list.distUpgrade
arctica0316-ppa-precise.list.save
dropbox.list
dropbox.list.distUpgrade
dropbox.list.save
google-chrome.list
google-chrome.list.distUpgrade
google-chrome.list.save
google-talkplugin.list
google-talkplugin.list.distUpgrade
google-talkplugin.list.save
kilian-f.lux-lucid.list
kilian-f.lux-lucid.list.distUpgrade
kilian-f.lux-lucid.list.save
kilian-f_lux-precise.list
kilian-f_lux-precise.list.distUpgrade
kilian-f_lux-precise.list.save
kilian-f_lux-trusty.list
kilian-f_lux-trusty.list.save
lightzone.list
lightzone.list.save
mjblenner-ppa-hal-trusty.list
mjblenner-ppa-hal-trusty.list.save
nvbn-rm-ppa-precise.list
nvbn-rm-ppa-precise.list.distUpgrade
nvbn-rm-ppa-precise.list.save
opera.list
opera.list.distUpgrade
opera.list.save
otto-kesselgulasch-gimp-lucid.list
otto-kesselgulasch-gimp-lucid.list.distUpgrade
otto-kesselgulasch-gimp-lucid.list.save
otto-kesselgulasch-gimp-precise.list
otto-kesselgulasch-gimp-precise.list.distUpgrade
otto-kesselgulasch-gimp-precise.list.save
otto-kesselgulasch-gimp-trusty.list
otto-kesselgulasch-gimp-trusty.list.save
ubuntu-mozilla-security-ppa-precise.list
ubuntu-mozilla-security-ppa-precise.list.distUpgrade
ubuntu-mozilla-security-ppa-precise.list.save
```


The output of sudo apt-get update && sudo apt-get upgrade
----------------------------------------------------------
```
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Get:1 [http://deb.opera.com](http://deb.opera.com) stable InRelease [2,592 B]                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty InRelease                              
Ign [http://deb.opera.com](http://deb.opera.com) stable InRelease                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages/DiffIndex               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty Release.gpg                            
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/restricted Sources             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/universe Sources               
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/multiverse Sources             
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main i386 Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/restricted i386 Packages       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/universe i386 Packages         
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/multiverse i386 Packages       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/universe Translation-en        
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_GB                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources              
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main Sources                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main i386 Packages                     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted i386 Packages               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB                     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main Translation-en_GB                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main Translation-en                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse Translation-en_GB           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted Translation-en         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe Translation-en_GB        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe Translation-en           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en
Fetched 2,592 B in 7s (370 B/s)                                                
W: GPG error: [http://deb.opera.com](http://deb.opera.com) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 63F7D4AFF6D61D45
W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release](http://dl.google.com/linux/chrome/deb/dists/stable/Release)  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by Garry_Knight on 2016-04-24
More information. My friend managed to get screen grabs of the dialog  that has been popping up. It's the first one shown below. It just keeps repeating this message

"System update available
A security update is available for your system. 3 packages were updated for security reasons"

She says, "The  arrows on the left of the screengrabs seem to be purely decorative.  There's nowhere to click on in order to get the packages. The popups  appear every few minutes, so it seems unlikely that my system actually  was updated each time."

The second screen grab is what she sees if she clicks the Notifications icon in the system tray.
**Edit:** I've added another screen grab below

[IMG]http://i.imgur.com/ODjQ8WL.jpg[/IMG]

[IMG]http://i.imgur.com/5sI3vzg.jpg[/IMG]

**Edit Apr 25th:** Another message popped up today and she managed to do a screen grab:

[IMG]http://i.imgur.com/jOvB8ZY.jpg[/IMG]

---

### Post by mastablasta on 2016-04-25
```
W: GPG error: [http://deb.opera.com]("http://deb.opera.com/") stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 63F7D4AFF6D61D45

```
the ppa is not signed. you should fix this. Probably a command was missed during install.

```

W: Failed to fetch [http://dl.google.com/linux/chrome/de...stable/Release]("http://dl.google.com/linux/chrome/deb/dists/stable/Release")  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

```

as the error description says - something is wrong with this line in sources.list. is the repository still available? in any case try to comment the line (put the # sign in front of it) and see if this solves the original issue. If it does, we can look forward as to what went wrong there. 
note that if you comment out this line in sources.list Chrome will no longer be updated. Still if this works well, next step would be to check why is it not working. if link is still valid a forced update might solve the issue otherwise you can attempt to reinstall.

---

### Post by Garry_Knight on 2016-04-25
Thanks for your reply Mastablasta. I noticed those two warnings while I was at her place trying to find out what was wrong, and that they relate to the Opera and Chrome packages. I checked and found that she has the latest versions of both installed. So I assumed that it wasn't these warnings that were causing her problem but rather the error message:

E: Some index files failed to download. They have been ignored, or old ones used instead.

I can certainly get her to comment out those lines and see what happens, but I'm pretty certain that it's some other problem causing her system to fail to update. What do you think?

I could ask her to uninstall and reinstall both the Opera and Chrome packages. I think they both take care of their own sources.list entries, so that might remove those warnings. But she uses Chrome very heavily on a daily basis and could do without the interruption. Plus, I think Chrome and Opera both update themselves and don't rely on the package system.

---

### Post by Garry_Knight on 2016-04-27
It seems that Opera doesn't update itself. She found that she had version 12, dating back to 2011. So she uninstalled that and installed the latest version 36. But we're still no nearer understanding why she hasn't been getting any system updates for quite a while now.

Is there someone knowledgeable about apt who can tell us where to look?

---

### Post by oldos2er on 2016-04-27
According to [this]("http://deb.opera.com/manual.html") if you install Opera from a deb file the repository is added to your sources and should be updated. It might've been different five years ago; I don't know. But I'd try uninstalling the version she has now, downloading the latest deb file and install it from there.

---

### Post by Garry_Knight on 2016-04-28
Thanks for your reply, oldos2er. She had a look in Synaptic and found that the old version was installed and the latest version was listed, so she simply uninstalled the old one and installed the new one using Synaptic. Unfortunately, it wiped out her browsing history but as it's not her main browser, not too much damage done. In any case, we don't expect any further warnings re Opera. She's still getting the warning about Chrome and I'm pretty sure we'll sove that one, too.

But neither of these will fix the problem that apt-get update can't fetch some of the sources in sources.list, so I need to find out why, and how to fix it. I expect that apt-get will write the errors to a file somewhere so I'll try and hunt that down. I'll also install the same version she has (Kubuntu 14.04) into a virtual machine on my Windows PC and compare my sources.list with hers, plus any config files that apt-get relies on. One way or another I'll hunt down the cause of her problems. I'd hoped that someone might spot the cause from the evidence I've posted, just to save some time - which is always in short supply.

Also, I'm wondering if it's possible to force 14.04 to dist-upgrade to 16.04, but I expect we'll have to fix the errors before there's any chance of that.

---

### Post by oldos2er on 2016-04-28
This should get the gpg key you're missing: ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 63F7D4AFF6D61D45
``` If you open Synaptic, go to Settings, Repositories, Other Software tab, uncheck the dl.google.com repo, then 'Reload' your sources (this is the equivalent of running *sudo apt-get update*), your errors should be gone. If not, please post back.

The dl.google.com repo can be re-enabled at some point in the future.

---

### Post by Garry_Knight on 2016-04-29
Uh! I feel stupid, and somewhat humble. I'd assumed that the error message didn't relate to Chrome as there had already been a warning message about it. And it seemed strange that there would be two messages about the same problem.

The good news is that she's now getting a 'Your system is up to date' message. So thanks for your help, and in future I'll just do what I'm told :)

Thanks, oldos2er, and mastablasta too! My friend says, "Thanks, and indeed, let all the children boogie!"

---

### Post by oldos2er on 2016-04-29
Google is having some issues with their linux repositories, so if this happens again that might be why.

---

