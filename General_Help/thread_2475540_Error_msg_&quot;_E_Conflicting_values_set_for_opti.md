---
title: "Error msg: &quot; E: Conflicting values set for option Signed-By regarding source"
date: 2022-05-31
forum: General Help
---

### Post by parag-puranik on 2022-05-31
On my **Ubuntu 22.04 **system Terminal when I execute the command: " sudo apt-get remove wine --purge " I get the following **error message** : 
" E: Conflicting values set for option Signed-By regarding source [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) jammy: /usr/share/keyrings/winehq-archive.key != /usr/share/keyrings/winehq.gpg E: The list of sources could not be read. "

I was in the process of removing an earlier Wine version 6.0.3~repack-1 to later on install latest Wine 7.0 stable version, but I am encountering this error at every step of reinstall process. 

Even when I try to open **Synaptic Package Manager** the **same error** crops in and the package manager fails to open. 

My question was -**how to get rid of the error ?** . . so that I can fresh install Wine- 7.0 version. 

I have gone through similar questions on this forum but still I am not able to compose correct/proper syntax for my peculiar case. Please help - considering that I migrated to Ubuntu from Windows hardly 2 months back, and so I am a newbie.

---

### Post by parag-puranik on 2022-06-02
Here is my System Info regarding Repos: 
Repos:     No active apt repos in: /etc/apt/sources.list 
           Active apt repos in: /etc/apt/sources.list.d/additional-repositories.list 
           1: deb https: //dl.winehq.org/wine-builds/ubuntu/ focal main
           Active apt repos in: /etc/apt/sources.list.d/balena-etcher.list 
           1: deb https: //dl.cloudsmith.io/public/balena/etcher/deb/linuxmint una main
           2: deb-src https: //dl.cloudsmith.io/public/balena/etcher/deb/linuxmint una main
           Active apt repos in: /etc/apt/sources.list.d/official-package-repositories.list 
           1: deb http: //packages.linuxmint.com una main upstream import backport #id:linuxmint_main
           2: deb http: //archive.ubuntu.com/ubuntu focal main restricted universe multiverse
           3: deb http: //archive.ubuntu.com/ubuntu focal-updates main restricted universe multiverse
           4: deb http: //archive.ubuntu.com/ubuntu focal-backports main restricted universe multiverse
           5: deb http: //security.ubuntu.com/ubuntu/ focal-security main restricted universe multiverse
           6: deb http: //archive.canonical.com/ubuntu/ focal partner
Info:      Processes: 186 Uptime: 12m Memory: 3.59 GiB used: 1.10 GiB (30.6%) Init: systemd v: 245 
           runlevel: 5 Compilers: gcc: 9.4.0 alt: 9 Client: Unknown python3.8 client inxi: 3.0.38

---

### Post by HermanAB on 2022-06-02
Hmm, new Linux users always struggle with Wine.  After some time, they discover virtual systems, and install an old version of Windows in a VM for the odd thing they need to run on another system.

---

### Post by parag-puranik on 2022-06-02
[SIZE=3]Additional info: 
[/SIZE]
[SIZE=3] [/SIZE]
[LIST=1]
[*][SIZE=3]when I execute the command:[/SIZE]
[SIZE=3] [/SIZE][SIZE=3]ls /etc/apt/sources.list.d 
[/SIZE][SIZE=3] [/SIZE][SIZE=3]I get the output:[/SIZE]
[SIZE=3] [/SIZE][SIZE=3]unit193-ubuntu-encryption-jammy.list    winehq-jammy.sources  winehq.list.save
unit193-ubuntu-encryption-jammy.list.save  winehq.list
[/SIZE][SIZE=3] [/SIZE]
[*][SIZE=3]command:[/SIZE]
[SIZE=3] [/SIZE][SIZE=3]sudo rm -r /var/lib/apt/lists/*
[/SIZE][SIZE=3] [/SIZE][SIZE=3]output:[/SIZE]
[SIZE=3] [/SIZE][SIZE=3]rm: cannot remove '/var/lib/apt/lists/*': No such file or directory
[/SIZE][SIZE=3] [/SIZE]
[*][SIZE=3]command:[/SIZE]
[SIZE=3] [/SIZE][SIZE=3]sudo apt-get update
[/SIZE][SIZE=3] [/SIZE][SIZE=3][COLOR=#ff0000][/COLOR]output:[/SIZE]

[SIZE=3] [/SIZE][COLOR=#ff0000][B][SIZE=3]E: Conflicting values set for option Signed-By regarding source [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) jammy: /usr/share/keyrings/winehq-archive.key != /usr/share/keyrings/winehq.gpg
E: The list of sources could not be read.
[/SIZE][/B][/COLOR][SIZE=3] [/SIZE]
[*][SIZE=3]On clicking Software and Updates, nothing opens.Please help.

Please tell me how to remove the PPA. The  entry 'Wine' in Software is already gone. Even when I try to open  Synaptic Package Manager the same error crops in and the package manager  fails to open.

I tried 
sudo apt-get autoclean
 
sudo apt-get -f  install
 
sudo dpkg --configure -a 

sudo apt-get -f install 

sudo  apt-get update
 
sudo apt-get -u dist-upgrade
 
sudo apt-get -o Debug::pkgProblemResolver=yes dist-upgrade 

sudo apt-get remove --dry-run  package-name 

sudo apt-get update 

sudo apt-get -u dist-upgrade  

sudo apt-get clean package-name 

sudo apt-get install --reinstall  package-name 

 . . .Still I am getting the same error : [/SIZE][SIZE=3]
[/SIZE]
[COLOR=#ff0000][B][SIZE=3]E: Conflicting values set for option Signed-By regarding source [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) jammy: /usr/share/keyrings/winehq-archive.key != /usr/share/keyrings/winehq.gpg
E: The list of sources could not be read.

[/SIZE][/B][/COLOR]My question was -how to get rid of the error ?
 . . so that I can  reinstall Wine- whatever version. Even when I try to
 open Synaptic Package Manager the same error crops in and the package 
manager fails to open. 
I tried as written in [websetnet.net/how-to-fix-unmet-dependencies-error-on-ubuntu]("https://websetnet.net/how-to-fix-unmet-dependencies-error-on-ubuntu/") 
Any assistance on this is welcome.


[COLOR=#ff0000]**[SIZE=3][/SIZE]**[/COLOR]**[SIZE=3][COLOR=#ff0000][/COLOR][/SIZE]**
[/LIST]

---

### Post by parag-puranik on 2022-06-02
[SIZE=3]**[ 						 							HermanAB ]("https://ubuntuforums.org/member.php?u=44990")**What I understood till now is . . . **probably **...this is Ubuntu 22.04 problem rather than Wine problem. Please go through my latest reply,[/SIZE]

---

### Post by HermanAB on 2022-06-02
Well, you seem to be learning rapidly, but once you get tired and want something that works again, just reinstall Ubuntu - it only takes about twenty minutes.

If you are really serious about using Wine - consider installing CxOffice from Codeweavers.  That actually works, but it costs a few dollars:
https://www.codeweavers.com/

---

### Post by parag-puranik on 2022-06-06
Reinstalling Ubuntu may take only 20 min. -Alright, But installing other apps and configuring everything all over again is pain. Moreover, How do I learn for future similar circumstances if I adopt the shortcut of fresh Install every time I encounter similar problems ? I hope you understand my dilemma, which I am sure every Windows user is facing if he chooses to migrate to Linux. Meanwhile my problem remains unsolved.

---

### Post by ActionParsnip on 2022-06-06
This may give clues
[https://stackoverflow.com/questions/71553340/sudo-apt-get-update-does-not-work-after-trying-to-install-elasticsearch-throug](https://stackoverflow.com/questions/71553340/sudo-apt-get-update-does-not-work-after-trying-to-install-elasticsearch-throug)

---

