---
title: "Broke Ubuntu by updating with Canonical Repo"
date: 2020-03-20
forum: General Help
---

### Post by one-big-andreo on 2020-03-20
Hello! My ubuntu installation completely broke after adding the Canonical Repository in my update settings, and then normally updating. My current installation gives me a list of fatal errors even when just logging in, and when updating or trying to fix broken packages in the terminal, or even opening settings is not possible anymore. 

I would like to ask why did this happen and why would the normal Canonical repository not be added in the first place.
[B]
Suspected cause of problem:[/B]
In the updater settings by additional repositories I added the Canonical repository, because one would think that they know what they are doing as they almost entirely made Ubuntu. After this Ubuntu thought it was not up-to-date anymore as one would expect, and started to update everything. At one point I got an pop-up, stating that something could go wrong, which I regrettably ignored and pressed continue. When it was finished, I got a crashing system that gave me the bootloader (or another blue screen I couldn't see).  
[B]
Problems:[/B]
Not being able to update, open settings, login,  upgrade or much else. With the terminal giving me this for example when updating as can be seen:
```
[COLOR=#4E9A06]**andres@andres-Lenovo-ideapad**[/COLOR]:[COLOR=#3465A4]**~**[/COLOR]$ sudo apt-get update
[sudo] password for andres: 
Hit:1 https://brave-browser-apt-release.s3.brave.com stable InRelease
Hit:2 http://nl.archive.ubuntu.com/ubuntu eoan InRelease                       
Hit:3 http://ppa.launchpad.net/lutris-team/lutris/ubuntu eoan InRelease        
Ign:4 http://dl.google.com/linux/chrome/deb stable InRelease                   
Hit:5 http://nl.archive.ubuntu.com/ubuntu eoan-updates InRelease               
Hit:6 http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu eoan InRelease      
Hit:7 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:8 http://nl.archive.ubuntu.com/ubuntu eoan-backports InRelease             
Get:9 http://security.ubuntu.com/ubuntu eoan-security InRelease [97,5 kB]      
Hit:10 http://mirror.serverius.net/kali kali-rolling InRelease                 
Hit:12 http://repo.steampowered.com/steam precise InRelease
Fetched 97,5 kB in 5s (19,5 kB/s)
Reading package lists... Done
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Packages (contrib/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Packages (contrib/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Packages (contrib/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Translations (contrib/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Translations (contrib/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target DEP-11 (contrib/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target DEP-11 (contrib/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target DEP-11-icons-small (contrib/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target DEP-11-icons (contrib/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target CNF (contrib/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target CNF (contrib/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Packages (non-free/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Packages (non-free/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Packages (non-free/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Translations (non-free/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Translations (non-free/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target DEP-11 (non-free/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target DEP-11 (non-free/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target DEP-11-icons-small (non-free/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target DEP-11-icons (non-free/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target CNF (non-free/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target CNF (non-free/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Packages (contrib/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Packages (contrib/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Packages (contrib/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Translations (contrib/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Translations (contrib/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target DEP-11 (contrib/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target DEP-11 (contrib/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target DEP-11-icons-small (contrib/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target DEP-11-icons (contrib/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target CNF (contrib/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target CNF (contrib/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Packages (non-free/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Packages (non-free/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Packages (non-free/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Translations (non-free/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Translations (non-free/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target DEP-11 (non-free/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target DEP-11 (non-free/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target DEP-11-icons-small (non-free/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target DEP-11-icons (non-free/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target CNF (non-free/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target CNF (non-free/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target Packages (contrib/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target Packages (contrib/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target Packages (contrib/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target Translations (contrib/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target Translations (contrib/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target DEP-11 (contrib/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target DEP-11 (contrib/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target DEP-11-icons-small (contrib/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target DEP-11-icons (contrib/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target CNF (contrib/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target CNF (contrib/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target Packages (non-free/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target Packages (non-free/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target Packages (non-free/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target Translations (non-free/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target Translations (non-free/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target DEP-11 (non-free/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target DEP-11 (non-free/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target DEP-11-icons-small (non-free/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target DEP-11-icons (non-free/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target CNF (non-free/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target CNF (non-free/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Packages (contrib/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Packages (contrib/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Packages (contrib/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Translations (contrib/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Translations (contrib/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target DEP-11 (contrib/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target DEP-11 (contrib/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target DEP-11-icons-small (contrib/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target DEP-11-icons (contrib/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target CNF (contrib/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target CNF (contrib/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Packages (non-free/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Packages (non-free/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Packages (non-free/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Translations (non-free/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Translations (non-free/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target DEP-11 (non-free/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target DEP-11 (non-free/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target DEP-11-icons-small (non-free/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target DEP-11-icons (non-free/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target CNF (non-free/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target CNF (non-free/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:61
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Packages (contrib/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Packages (contrib/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Packages (contrib/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Translations (contrib/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Translations (contrib/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target DEP-11 (contrib/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target DEP-11 (contrib/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target DEP-11-icons-small (contrib/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target DEP-11-icons (contrib/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target CNF (contrib/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target CNF (contrib/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Packages (non-free/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Packages (non-free/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Packages (non-free/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Translations (non-free/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Translations (non-free/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target DEP-11 (non-free/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target DEP-11 (non-free/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target DEP-11-icons-small (non-free/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target DEP-11-icons (non-free/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target CNF (non-free/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target CNF (non-free/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:63
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target Packages (contrib/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target Packages (contrib/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target Packages (contrib/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target Translations (contrib/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target Translations (contrib/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target DEP-11 (contrib/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target DEP-11 (contrib/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target DEP-11-icons-small (contrib/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target DEP-11-icons (contrib/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target CNF (contrib/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target CNF (contrib/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target Packages (non-free/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target Packages (non-free/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target Packages (non-free/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target Translations (non-free/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target Translations (non-free/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target DEP-11 (non-free/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target DEP-11 (non-free/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target DEP-11-icons-small (non-free/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target DEP-11-icons (non-free/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target CNF (non-free/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65
W: Target CNF (non-free/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:59 and /etc/apt/sources.list:65

```

Packages I have installed are not recognized anymore, even the 'basics' like python. 
When trying to reinstalling Ubuntu from a live-usb it didn't recognize an already present Ubuntu installation on the system. 

**Conclusion:**
Why did this happen, and does this by coincidence has an easy fix i'm not seeing? Why does one have the Canonical Repo by default listed, and how could it break my entire system?

As for me I'm proceeding now to freshly reinstall Ubuntu and wipe everything, then manually recover my backup files from an usb. I hope you could help shed some light on my issue, thanks in advance. And I would otherwise be a happy fan and loyal user of Ubuntu ;)

---

### Post by deadflowr on 2020-03-20
Post back the results of
```
cat /etc/apt/sources.list
```

---

