---
title: "Unable to remove Wine. seeing so many hits, Err &amp; Warning"
date: 2023-03-13
forum: General Help
---

### Post by appusony on 2023-03-13
Dear Ubuntu Support team,


 I am using:
 


```
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.5 LTS
Release:    20.04
Codename:    focal
(base) appu@appu-UX305UA:~$
```




I tried triggering:
 
sudo apt-get update
 sudo apt-get upgrade


It's been long while now ,where I was trying to fix , the below Hit's, Err, Ign, warnings, 


I am seeing the below Hit's, Err, Ign, warnings, may I know please,


1. how to fix this  Hit's, Err, Ign, warnings?


2. How to install wine, so that I can install mobaxterm as per the link please - [https://dev.to/selllami/how-to-run-mobaxterm-on-ubuntu-linux-with-wine-ohf](https://dev.to/selllami/how-to-run-mobaxterm-on-ubuntu-linux-with-wine-ohf)

```

(base) appu@appu-UX305UA:~$ sudo apt-get update
Get:1 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) focal InRelease [8,041 B]
Hit:2 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable InRelease                                                                                                                                             
Hit:3 [https://linux.teamviewer.com/deb](https://linux.teamviewer.com/deb) stable InRelease                                                                                                                                                   
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal InRelease                                                                                                                                                    
Hit:5 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) focal InRelease                                                                                                          
Err:1 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) focal InRelease                                                                                               
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F
Hit:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates InRelease                                                                                              
Hit:7 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal InRelease                                                                                                   
Hit:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-backports InRelease                                                                                            
Hit:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security InRelease                                                                       
Hit:10 [https://download.sublimetext.com](https://download.sublimetext.com) apt/stable/ InRelease                                                                         
Ign:11 [https://www.scootersoftware.com](https://www.scootersoftware.com) bcompare4 InRelease
Hit:12 [https://www.scootersoftware.com](https://www.scootersoftware.com) bcompare4 Release
Reading package lists... Done
W: GPG error: [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) focal InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F
E: The repository 'https://dl.winehq.org/wine-builds/ubuntu focal InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Translations (main/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Sources (restricted/source/Sources) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:7
W: Target Sources (restricted/source/Sources) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:7
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Translations (main/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
(base) appu@appu-UX305UA:~$ 

```

kindly do the needful, as I am stuck with this from past many days.


Many Thanks in advance,

---

### Post by coffeecat on 2023-03-13
I've enclosed your terminal outputs between BBCode code tags to make them readable. Please use code tags when posting terminal output, code, contents of config files and the like. There is a link in my sig about code tags if you need it.

> **appusony said:**
> Dear Ubuntu Support team,

Just so there is no misunderstanding: the members of the forum, staff included, are end-users such as yourself, who volunteer their time freely to help others. We are not employed by Canonical. We are a community rather than a "team".

Good luck.

---

### Post by Impavidus on 2023-03-13
Hit is fine. It means that apt could find what is was looking for, but didn't download as it wasn't changed since the previous check.
Ign is fine too. It means that a software source is listed in your files, but disabled.
Get is fine too. It means apt downloaded a list of packages available in some repository.
Err means there was some error. Here, apt couldn't verify the authenticity of the software source as the cryptographic key, known as 76F1A20FF987672F, isn't installed on your computer. You may be able to get the key from a trusted key server. It looks like some things changed recently, but I think this is still supposed to work:```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 76F1A20FF987672F
```
W gives a warning. Some software sources are defined multiple times. Some are both in /etc/apt/sources.list.d/google-chrome-unstable.list and in /etc/apt/sources.list.d/google-chrome.list, some are defined twice in /etc/apt/sources.list, both on line 2 and line 7. Look at those files and clean them up.

You can edit root-owned files (or actually, files where you need root permissions to edit them) with the sudoedit command:```
sudoedit filename
```
Most people don't need the source code repositories. They're disabled by default.

I've never use wine myself, so there are other people who know more about that.

---

### Post by appusony on 2023-03-14
> **coffeecat said:**
> I've enclosed your terminal outputs between BBCode code tags to make them readable. Please use code tags when posting terminal output, code, contents of config files and the like. There is a link in my sig about code tags if you need it.



Just so there is no misunderstanding: the members of the forum, staff included, are end-users such as yourself, who volunteer their time freely to help others. We are not employed by Canonical. We are a community rather than a "team".

Good luck.


Thanks a Million!, I am so extremely sorry for my misunderstanding, please excuse me & please forgive me, I feel so very much blessed, to meet you all such kind of wonderful & fabulous people. Love you all always. Many things to learn from you all.

---

### Post by appusony on 2023-03-14
Thanks a Million Impavidus!, all your pointers really worked out of the box!, once again many thanks for the detailed steps above.

---

