---
title: "I need help with a repository glitch."
date: 2018-06-14
forum: General Help
---

### Post by staticpurge on 2018-06-14
I tired to install the Runescape NXT client but it failed do to an unsigned file. After that I tired to install Dolphin emulator but part way through it shows runescape being installed and then fails. This is the terminal input for installing Runescape.
```
              sudo -s -- << EOFwget -O - [https://content.runescape.com/downloads/ubuntu/runescape.gpg.key](https://content.runescape.com/downloads/ubuntu/runescape.gpg.key) | apt-key add -
              mkdir -p /etc/apt/sources.list.d
              echo "deb [https://content.runescape.com/downloads/ubuntu](https://content.runescape.com/downloads/ubuntu) trusty non-free" > /etc/apt/sources.list.d/runescape.list
              apt-get update
              apt-get install -y runescape-launcher
              EOF
```

When I Install dolphin this is what happens.

```
sudo apt-add-repository ppa:dolphin-emu/ppa
 
Unofficial builds for Dolphin Wii/Gamecube Emulator.


Install the dolphin-emu package for the latest stable release of Dolphin.


Install the dolphin-emu-master package for weekly builds that include the latest upstream changes from git.


The dolphin-emu-triforce package will allow you play Triforce games, as well Wii/Gamecube games. It's based on the old Triforce fork (4.0-315).


You'll need to enable the Universe repo before install Dolphin.


For Ubuntu 12.04 and 14.04 users: dolphin-emu needs an updated libstdc++6 (>=4.9), so install this PPA first:
[https://launchpad.net/~ubuntu-toolchain-r/+archive/ubuntu/test](https://launchpad.net/~ubuntu-toolchain-r/+archive/ubuntu/test)
It will update libstdc++6 in your system, so be careful.


For Ubuntu 16.04 users: A bug in the version of glibc shipped in Ubuntu 16.04 causes a performance regression in Dolphin. To work around this, upgrade to Ubuntu 16.10 or newer


THERE'S NO 32-bit (i386) BUILDS ANYMORE: [https://dolphin-emu.org/blog/2014/05/19/obituary-32bit/](https://dolphin-emu.org/blog/2014/05/19/obituary-32bit/)


ARMv8/AArch64/arm64 packages now ;)


Did you like this PPA?
Bitcoin donation: 1MhU9RxaRhj3yd1c6fSQAQhDPxpwLY6WU5
Litecoin donation: LiGLDxjntT9GjX6S6fpbgBCN5akemyYQ7c
 More info: [https://launchpad.net/~dolphin-emu/+archive/ubuntu/ppa](https://launchpad.net/~dolphin-emu/+archive/ubuntu/ppa)
Press [ENTER] to continue or Ctrl-c to cancel adding it.

```

```
Hit:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease                                                                
Ign:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                                              
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-security InRelease [83.2 kB]                                                                        
Hit:5 [http://ppa.launchpad.net/dolphin-emu/ppa/ubuntu](http://ppa.launchpad.net/dolphin-emu/ppa/ubuntu) bionic InRelease                                                                                          
Hit:6 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                                                                                                      
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease [83.2 kB]                                                                                         
Hit:8 [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) bionic InRelease                                                                 
Get:9 [https://content.runescape.com/downloads/ubuntu](https://content.runescape.com/downloads/ubuntu) trusty InRelease [2,236 B]                                                                                      
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB]                                                                                      
Get:11 [http://repo.linuxliteos.com/linuxlite](http://repo.linuxliteos.com/linuxlite) diamond InRelease [2,104 B]                                                                                             
Hit:12 [http://ppa.launchpad.net/teejee2008/ppa/ubuntu](http://ppa.launchpad.net/teejee2008/ppa/ubuntu) bionic InRelease
Err:9 [https://content.runescape.com/downloads/ubuntu](https://content.runescape.com/downloads/ubuntu) trusty InRelease
  The following signatures were invalid: AAC9264309E4D717441DB9527373B12CE03BEB4B
Get:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packages [141 kB]
Get:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main i386 Packages [127 kB]
Get:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main Translation-en [55.2 kB]
Get:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe i386 Packages [84.3 kB]    
Get:18 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 Packages [84.5 kB]
Get:19 [http://repo.linuxliteos.com/linuxlite](http://repo.linuxliteos.com/linuxlite) diamond/main i386 Packages [7,631 B]  
Get:20 [http://repo.linuxliteos.com/linuxlite](http://repo.linuxliteos.com/linuxlite) diamond/main amd64 Packages [12.7 kB]      
Reading package lists... Done                                   
W: GPG error: [https://content.runescape.com/downloads/ubuntu](https://content.runescape.com/downloads/ubuntu) trusty InRelease: The following signatures were invalid: AAC9264309E4D717441DB9527373B12CE03BEB4B
E: The repository 'https://content.runescape.com/downloads/ubuntu trusty InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```



I dont understand why it keeps trying to install. Im still learning how Linux works. Im using the newest version of linux lite currently.

---

### Post by deadflowr on 2018-06-14
[s]It seems the keys for runescpae are inaccessible
(the key server is currently not found
This is what I see
```
wget -O - https://content.runescape.com/downlo...escape.gpg.key | sudo apt-key add -
--2018-06-14 11:04:01--  https://content.runescape.com/downlo...escape.gpg.key
Resolving content.runescape.com (content.runescape.com)... 91.235.140.195, 91.235.140.194
Connecting to content.runescape.com (content.runescape.com)|91.235.140.195|:443... connected.
HTTP request sent, awaiting response... 404 Not found
2018-06-14 11:04:01 ERROR 404: Not found.

gpg: no valid OpenPGP data found.
```[/s]

Nevermind, I messed of the wget command.

For now, I would disable the runescape repository on the system.
(At least until the issue is resolved)

Open The program called Software and Updates and go to the Other Software tab.
Find the runescape entry and click the check box to remove the check mark for it.
(It'll ask for a password)
This will disable it.
Then click on close and let the system reload.

The you can try adding the dolphin-emu ppa.

(for what it's worth, dolphin-emu is already in Ubuntu's own repository system.
You can run 
```
sudo apt install dolphin-emu
```
If you really want to install the ppa version, then you can add the ppa repository and simply do a regular system update.
The regular system update will automatically install the updated dolphin-emu package from the added ppa.)

Best of luck

---

