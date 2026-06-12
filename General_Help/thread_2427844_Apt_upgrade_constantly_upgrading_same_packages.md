---
title: "Apt upgrade constantly upgrading same packages?"
date: 2019-09-26
forum: General Help
---

### Post by degrowth on 2019-09-26
So I have a strange issue/question. For the last few weeks, every time I run apt update/upgrade, I have (roughly) the same list of packages to be updated. I normally run update/upgrade when I get home from work in the evenings, and there's no failures, I'm just curious what's going on. Here's what today's update/upgrade looks like:

[https://i.imgur.com/oY7HOSJ.png](https://i.imgur.com/oY7HOSJ.png)

Did I somehow put myself on a nightly build list for something that I can't figure out? 

Any help would be greatly appreciated!

---

### Post by ajgreeny on 2019-09-26
Can you please show us the output of commands ```
sudo apt update
sudo apt upgrade
```

Please do not use large inline images; either use a link as I have done, or use the attachment icon (paperclip) in the "Reply to Thread" toolbar.

However it is better to copy the text from the terminal by highlighting and using a right click (or Ctrl+Shift+C) and then paste the text into your reply.
Please use **Code-Tags** for terminal output to show that text in a more readable format, the same as it is in the terminal, not as plain text. See my signature below for a **How-to**

---

### Post by degrowth on 2019-09-26
Oh Lord, my apologies! I thought I was inserting a link, not the actual picture! It's been quite awhile since I've posted to a forum :(

Here's the update/upgrade:

```

foobar@DivinitysReach:~$ sudo apt update
[sudo] password for foobar: 
Ign:1 http://linux.dropbox.com/ubuntu bionic InRelease                                                
Hit:2 http://linux.dropbox.com/ubuntu bionic Release                                                  
Hit:3 https://brave-browser-apt-release.s3.brave.com bionic InRelease                                 
Hit:4 https://dl.winehq.org/wine-builds/ubuntu bionic InRelease                                       
Hit:5 http://us.archive.ubuntu.com/ubuntu bionic InRelease                                            
Hit:7 https://packages.microsoft.com/ubuntu/18.04/prod bionic InRelease                               
Hit:8 http://linux.teamviewer.com/deb stable InRelease                                                
Get:9 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]                          
Get:10 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]                          
Hit:11 http://ppa.launchpad.net/gns3/ppa/ubuntu bionic InRelease                                      
Ign:12 http://repo.vivaldi.com/stable/deb stable InRelease                                            
Hit:13 http://repo.vivaldi.com/stable/deb stable Release                                              
Hit:14 http://ppa.launchpad.net/lutris-team/lutris/ubuntu bionic InRelease                            
Get:15 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]                       
Hit:16 https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.04 ./ InRelease  
Hit:17 http://ppa.launchpad.net/nathan-renniewaldock/flux/ubuntu bionic InRelease                     
Hit:19 http://ppa.launchpad.net/obsproject/obs-studio/ubuntu bionic InRelease 
Get:20 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [740 kB]               
Get:21 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu bionic InRelease [20.8 kB]              
Get:22 http://us.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [586 kB]                 
Hit:23 http://ppa.launchpad.net/openrazer/stable/ubuntu bionic InRelease            
Hit:24 http://ppa.launchpad.net/paulo-miguel-dias/pkppa/ubuntu bionic InRelease                       
Get:25 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages [980 kB]             
Hit:26 http://ppa.launchpad.net/polychromatic/stable/ubuntu bionic InRelease                          
Get:27 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu bionic/main i386 Packages [18.1 kB]     
Get:28 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [1,007 kB]          
Fetched 3,603 kB in 13s (277 kB/s)                                                                    
Reading package lists... Done
Building dependency tree       
Reading state information... Done
18 packages can be upgraded. Run 'apt list --upgradable' to see them.

```

```
foobar@DivinitysReach:~$ sudo apt upgrade Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libllvm9:i386
The following packages will be upgraded:
  libegl-mesa0 libegl1-mesa libgbm1 libgl1-mesa-dri libgl1-mesa-dri:i386 libgl1-mesa-glx libgl1-mesa-glx:i386 libglapi-mesa libglapi-mesa:i386 libglx-mesa0
  libglx-mesa0:i386 libwayland-egl1-mesa libxatracker2 mesa-va-drivers mesa-vdpau-drivers mesa-vulkan-drivers vivaldi-stable
17 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 89.8 MB of archives.
After this operation, 148 kB of additional disk space will be used.
Do you want to continue? [Y/n] 

```

---

### Post by ajgreeny on 2019-09-26
So now hit Enter (at the Do you want to continue? question) and those packages should upgrade.

If there are any problems an error message will report back to you, so if that's the case please copy and paste the info again, with the error.

---

### Post by degrowth on 2019-09-26
I have no errors/issues with installing the updates/upgrades. My question was why are these same ~18 packages updating every day.

---

### Post by deadflowr on 2019-09-26
You have testing-level/bleeding edge ppas such as the oibaf driver ppa.
That will constantly update all those packages.
Particularly the mesa packages.

Seems like you have the libllvm9 32-bit version holding things up
Try running upgrade with
```
sudo apt full-upgrade
```
as oppose to the less powerful *sudo apt upgrade* you have been running.

---

### Post by degrowth on 2019-09-26
> **deadflowr said:**
> You have testing-level/bleeding edge ppas such as the oibaf driver ppa.
That will constantly update all those packages.
Particularly the mesa packages.


Ahhhh, that's what it was! Thank you!!!! I'll look at taking that one out (for now)

---

### Post by mc4man on 2019-09-26
> **degrowth said:**
> Ahhhh, that's what it was! Thank you!!!! I'll look at taking that one out (for now)
if you remove  oibaf driver ppa keep in mind you'll stay at the current mesa development version you have, could be fine but it is in essence just a random daily version.

If you are tempted at some point to do a 18.04 > 20.04 upgrade then before doing so you'll need to add back the ppa, update and probably upgrade, then use ppa-purge to return to the 18.04 mesa packages.
If you don't then the release upgrade will fail.

Additionally you have the paulo-miguel-dias/pkppa (padoka), which is a mesa stable ppa. While you're not using it's mesa packages as the  oibaf  ones are higher versioned you'd need to also acount for this ppa if attempting to do a release upgrade or ppa-purge on the  oibaf  ppa.

---

### Post by oldrocker99 on 2019-09-26
It is quite true that *some* PPAs will push out a new build of that program every damn day. Nothing to worry about.

---

