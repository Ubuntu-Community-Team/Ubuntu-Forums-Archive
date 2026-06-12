---
title: "error 403 IP issue"
date: 2024-09-15
forum: General Help
---

### Post by aidenreid on 2024-09-15
I have been searching for hours for a solution to this problem, he problem is that when i try to use the sudo apt update it always responds with   "Failed to fetch [https://repositories.intel.com/gpu/ub.../dists/jammy/production/2328/InRelease](https://repositories.intel.com/gpu/ub.../dists/jammy/production/2328/InRelease)  403  Forbidden [IP: 143.204.29.114 443]"   here is the full thing:

sudo apt update
[sudo] password for aiden: 
Hit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal InRelease
Hit:2 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable InRelease                  
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates InRelease [128 kB]        
Hit:4 [http://ppa.launchpad.net/linuxuprising/java/ubuntu](http://ppa.launchpad.net/linuxuprising/java/ubuntu) focal InRelease   
Hit:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-backports InRelease          
Hit:6 [http://ppa.launchpad.net/lutris-team/lutris/ubuntu](http://ppa.launchpad.net/lutris-team/lutris/ubuntu) focal InRelease
Hit:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security InRelease
Err:8 [https://repositories.intel.com/gpu/ub](https://repositories.intel.com/gpu/ub)... jammy/production/2328 InRelease
  403  Forbidden [IP: 143.204.29.114 443]
Reading package lists... Done
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:7
E: Failed to fetch [https://repositories.intel.com/gpu/ub.../dists/jammy/production/2328/InRelease](https://repositories.intel.com/gpu/ub.../dists/jammy/production/2328/InRelease)  403  Forbidden [IP: 143.204.29.114 443]
E: The repository 'https://repositories.intel.com/gpu/ub... jammy/production/2328 InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:7
aiden@aiden-HP-Pavilion-g7-Notebook-PC:~/Desktop$ 

im also having a similar problem when trying to update the ubuntu version so it would really help if i could get a solution to this problem. Thank you!!!!!
[FONT=arial][/FONT]
P.s. Sorry for copy and pasting the information i just couldn't find a better way to do it lol.

---

### Post by QIII on 2024-09-15
Your issue appears to be an issue with a resource owned by Intel.  I am getting the 403 when trying to directly access the resource.

This may be a question to direct at Intel.

While you could certainly remove that repository from your sources, without more detailed information about what you have done to use the package, I can't predict whether or not that would have a deleterious effect on your system.

Generally, when upgrading to a new release, it is best to remove third party drivers, remove the repos from your sources, complete the upgrade and then attempt to reinstall the appropriate repo and package for the release.

---

### Post by aidenreid on 2024-09-16
Thank you so much!!! I was able to remove the repositories that were causing the issue and all is going well now.

---

