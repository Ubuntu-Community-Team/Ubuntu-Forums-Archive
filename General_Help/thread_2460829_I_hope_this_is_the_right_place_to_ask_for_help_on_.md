---
title: "I hope this is the right place to ask for help on this"
date: 2021-04-19
forum: General Help
---

### Post by sleebz on 2021-04-19
Im pretty new with Linux. I'm running Ubuntu 20.04 LTS. 
How do I fix this?

```
» sudo apt update
[sudo] password for hyros: 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates InRelease              
Hit:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports InRelease            
Hit:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease               
Ign:6 [http://ppa.launchpad.net/xenatt/xenlism/ubuntu](http://ppa.launchpad.net/xenatt/xenlism/ubuntu) focal InRelease           
Hit:7 [https://repo.nordvpn.com//deb/nordvpn/debian](https://repo.nordvpn.com//deb/nordvpn/debian) stable InRelease            
Err:8 [http://ppa.launchpad.net/xenatt/xenlism/ubuntu](http://ppa.launchpad.net/xenatt/xenlism/ubuntu) focal Release             
  404  Not Found [IP: 2001:67c:1560:8008::19 80]
Reading package lists... Done
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
E: The repository 'http://ppa.launchpad.net/xenatt/xenlism/ubuntu focal Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1
[6:21:48] hyros :: hyros  &#10140;  ~ »
```

---

### Post by oldfred on 2021-04-19
Please use code tags for longer terminal output. 
Easy to add with # icon in Forum's advanced editor.

As it says you have duplicate sources.
Did you run the add command more than once?
Best to add one at a time & then update to be sure it works.

If you installed from command line you can see your history:
history

then remove duplicates:
sudo add-apt-repository --remove xxxxx

You can see your ppa added sources like this:
```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ ll /etc/apt/sources.list.d [/COLOR]
total 32 
drwxr-xr-x 2 root root 4096 Jan 13 22:55 [COLOR=#5454ff]**.**[/COLOR][COLOR=#000000]/ [/COLOR]
drwxr-xr-x 7 root root 4096 Nov  2 15:20 [COLOR=#5454ff]**..**[/COLOR][COLOR=#000000]/ [/COLOR]
-rw-r--r-- 1 root root  123 Jan 13 22:55 mkusb-ubuntu-ppa-focal.list 
-rw-r--r-- 1 root root  125 Jan 13 22:55 mkusb-ubuntu-ppa-focal.list.save 
-rw-r--r-- 1 root root  143 Jan 13 22:55 phoerious-ubuntu-keepassxc-focal.list 
-rw-r--r-- 1 root root  145 Jan 13 22:55 phoerious-ubuntu-keepassxc-focal.list.save 
-rw-r--r-- 1 root root  149 Jan 13 22:55 yannubuntu-ubuntu-boot-repair-focal.list 
-rw-r--r-- 1 root root  151 Jan 13 22:55 yannubuntu-ubuntu-boot-repair-focal.list.save


[/FONT]
```

---

### Post by sleebz on 2021-04-19
i cant figure out how to add the code tags lol

---

### Post by ActionParsnip on 2021-04-20
[http://ppa.launchpad.net/xenatt/xenlism/ubuntu/dists/](http://ppa.launchpad.net/xenatt/xenlism/ubuntu/dists/)

The PPA doesn't support your release and should be removed

---

### Post by ActionParsnip on 2021-04-20
Also run
```

sudo rm /etc/apt/sources.list.d/google.list

```

---

### Post by Frogs Hair on 2021-04-20
The following PPA listed in the output is not supported on your release or not found. You can remove the entry by opening software sources, enter the other software tab, locate and select the PPA from the list, and use the remove option on the bottom.    
```
Err:8 http://ppa.launchpad.net/xenatt/xenlism/ubuntu focal Release             
  404  Not Found [IP: 2001:67c:1560:8008::19 80]

```

---

