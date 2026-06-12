---
title: "Anbox doesn't start on Ubuntu Budgie 18.10"
date: 2018-10-27
forum: General Help
---

### Post by tackskull on 2018-10-27
Hi everybody, I am trying to run Anbox on my pc running Ubuntu Budgie 18.10. I tried to install it both via terminal and via software center. BAsically the installation is ok but when I launch the program just start and crash after a few seconds of loading. Can you guys help me to let this program work?

Thanks :)

---

### Post by Holger_Gehrke on 2018-10-27
The first step in diagnosing this kind of problem is **always** the same: start the program from a shell because crashing programs usually give some error messages on standard output. To find out the name of the program look at the Exec-line in the .desktop file for anbox in /var/lib/snapd/desktop/applications/.

Holger

---

### Post by tackskull on 2018-10-27
Hi Holger, thanks for reply,

I don't know nothing about pc and would like to learn: what I have to do for start a program in shell? And what this mean?
I went in  /var/lib/snapd/desktop/applications/ but here there isn't the .desktop file you said.

---

### Post by Holger_Gehrke on 2018-10-28
The shell is the command interpreter you get when you open a terminal. The terminal just feeds input (as text) to a program and displays it's output graphically. You can have a terminal with another program than the shell and you can have a shell without the terminal (executing scripts or working in text mode in a virtual terminal or over ssh or ... ). So I should probably have told you to run it in the terminal, but as you can see from my explanation above, that would not be quite correct.

Is that the [anbox]("https://anbox.io") you are talking about ? Then there's two things which you should have done when installing it:

[LIST=1]
[*]Anbox needs two non-standard kernel-modules (ashmem and binder). Did you install those ? 
[*]It doesn't work with normal snap confinement, it needs to be installed in development mode. 
[/LIST]
 Instructions can be found at [https://docs.anbox.io/userguide/install.html](https://docs.anbox.io/userguide/install.html)

I've tried it and it works - s-l-o-w-l-y . My PC (XUbuntu 18.04, 4 cores @ 1.8 GHz, 4 GB RAM) is probably not quite the system needed for this ...

Holger

---

### Post by tackskull on 2018-10-29
I followed your guide, basically (I didn't notice) installing the kernels the terminal say error 404 not found. I installed well anbox on my pc with ubuntu 18.04 but on ubuntu budgie 18.10 seems have problems. I need this pc for my job and would like to install here anbox. Can be that the new 18.10 ubuntu has different sources for installing kernels or and progams? How can I solve this?

---

### Post by tackskull on 2018-10-29
This is what happen interminal, 404 not found and other errors:



```
tackskull@tackskull-HP-250-G4-Notebook-PC:~$ sudo add-apt-repository ppa:morphis/anbox-support
[sudo] password for tackskull: 
 
 More info: https://launchpad.net/~morphis/+archive/ubuntu/anbox-support
Press [ENTER] to continue or Ctrl-c to cancel adding it.

Hit:1 http://it.archive.ubuntu.com/ubuntu cosmic InRelease
Hit:2 http://it.archive.ubuntu.com/ubuntu cosmic-updates InRelease             
Hit:3 http://it.archive.ubuntu.com/ubuntu cosmic-backports InRelease           
Get:4 http://security.ubuntu.com/ubuntu cosmic-security InRelease [79,6 kB]    
Ign:5 http://dl.google.com/linux/chrome/deb stable InRelease                   
Ign:6 http://ppa.launchpad.net/morphis/anbox-support/ubuntu cosmic InRelease   
Err:7 http://ppa.launchpad.net/morphis/anbox-support/ubuntu cosmic Release     
  404  Not Found [IP: 91.189.95.83 80]
Hit:8 http://dl.google.com/linux/chrome/deb stable Release              
Get:9 http://security.ubuntu.com/ubuntu cosmic-security/main i386 Packages [21,8 kB]
Get:10 http://security.ubuntu.com/ubuntu cosmic-security/main amd64 Packages [21,8 kB]
Reading package lists... Done                                  
E: The repository 'http://ppa.launchpad.net/morphis/anbox-support/ubuntu cosmic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
tackskull@tackskull-HP-250-G4-Notebook-PC:~$ sudo apt update
Hit:1 http://it.archive.ubuntu.com/ubuntu cosmic InRelease
Hit:2 http://it.archive.ubuntu.com/ubuntu cosmic-updates InRelease  
Ign:3 http://ppa.launchpad.net/morphis/anbox-support/ubuntu cosmic InRelease
Hit:4 http://security.ubuntu.com/ubuntu cosmic-security InRelease   
Hit:5 http://it.archive.ubuntu.com/ubuntu cosmic-backports InRelease
Ign:6 http://dl.google.com/linux/chrome/deb stable InRelease                   
Err:7 http://ppa.launchpad.net/morphis/anbox-support/ubuntu cosmic Release     
  404  Not Found [IP: 91.189.95.83 80]
Hit:8 http://dl.google.com/linux/chrome/deb stable Release                   
Reading package lists... Done                     
E: The repository 'http://ppa.launchpad.net/morphis/anbox-support/ubuntu cosmic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/google-chrome-unstable.list:3 and /etc/apt/sources.list.d/google-chrome.list:3
tackskull@tackskull-HP-250-G4-Notebook-PC:~$  sudo apt install linux-headers-generic anbox-modules-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package anbox-modules-dkms
tackskull@tackskull-HP-250-G4-Notebook-PC:~$ sudo modprobe ashmem_linux
modprobe: FATAL: Module ashmem_linux not found in directory /lib/modules/4.18.0-10-generic
tackskull@tackskull-HP-250-G4-Notebook-PC:~$ sudo modprobe binder_linux
modprobe: FATAL: Module binder_linux not found in directory /lib/modules/4.18.0-10-generic

```

---

### Post by Holger_Gehrke on 2018-10-29
The PPA with the kernel modules only offers them for 16.04 and 18.04 (the two most recent LTS releases). You can try to download them directly from the PPA and install them through dpkg or gdebi. Since they contain source code that gets compiled as part of the installation, they *should* work with any recent kernel. Can't guarantee that though, since I don't use 18.10 and haven't tried it.

Holger

---

### Post by tackskull on 2018-10-29
How can I directly install? From software center? I want to try

---

### Post by Holger_Gehrke on 2018-10-29
You download the package from [http://ppa.launchpad.net/morphis/anbox-support/ubuntu/pool/main/a/anbox-modules/](http://ppa.launchpad.net/morphis/anbox-support/ubuntu/pool/main/a/anbox-modules/), install dkms (Dynamic Kernel Module Support, as far as I can tell the only dependency of the package; dkms depends on a lot of stuff - C-compiler, make, kernel-headers - which will get pulled in by apt) with 'sudo apt install dkms' , then install the modules with 'sudo dpkg -i anbox-modules-dkms_13_all.deb'. If this doesn't give any errors, you can load the modules with 'sudo modprobe ashmem_linux; sudo modprobe binder_linux' (they will load automatically on the next boot). In theory this should work, but as I don't have a 18.10 system, I can't give you any guarantee.

Holger

---

### Post by tackskull on 2018-10-29
Awesome Man, it works grate!!! Thanks a lot for your help and time!!!

---

