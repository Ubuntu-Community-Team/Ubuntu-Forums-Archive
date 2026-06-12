---
title: "broke apt-update"
date: 2020-07-16
forum: General Help
---

### Post by urubu66 on 2020-07-16
Hello,
after trying and failing to install wine and wasting a couple hours following different manuals online, I managed to break my apt update by adding a get with an unsafe repository.

```


sudo apt update
Hit:1 http://cz.archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 http://ppa.launchpad.net/cybermax-dexter/sdl2-backport/ubuntu bionic InRelease
Hit:3 http://cz.archive.ubuntu.com/ubuntu bionic-updates InRelease             
Get:4 http://cz.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB] 
Hit:5 http://ppa.launchpad.net/jtaylor/keepass/ubuntu bionic InRelease         
Hit:6 https://dl.winehq.org/wine-builds/ubuntu bionic InRelease                
Hit:7 http://linux.teamviewer.com/deb stable InRelease                         
Get:8 https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.04 ./ InRelease [1,562 B]
Get:9 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]    
Err:8 https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.04 ./ InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DFA175A75104960E
Reading package lists... Done
W: GPG error: https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.04 ./ InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DFA175A75104960E
E: The repository 'https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.04 ./ InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details
```

I tried running sudo apt-secure and sudo apt-secure(8) but it gives me a command not found and syntax error.

Any ideas?

---

### Post by ActionParsnip on 2020-07-16
```
 
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DFA175A75104960E

```

Should do it

---

### Post by urubu66 on 2020-07-16
Seems to have worked, thanks!

Follow up question: do you happen to know the way to install Wine on Ubuntu 18.04?

---

### Post by ActionParsnip on 2020-07-16
> **urubu66 said:**
> Seems to have worked, thanks!

Follow up question: do you happen to know the way to install Wine on Ubuntu 18.04?

```

sudo apt update
sudo apt install wine

```

Done

---

### Post by ActionParsnip on 2020-07-16
Remember to check the WineAppDB for compatibility. Not all apps run. Some won't even install
[https://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true](https://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true)

---

### Post by urubu66 on 2020-07-16
```
sudo apt install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is a virtual package provided by:
  winehq-staging 5.12~bionic
  winehq-stable 5.0.1~bionic
  winehq-devel 5.12~bionic
  wine-development 3.6-1
You should explicitly select one to install.

E: Package 'wine' has no installation candidate


```

and then

```

sudo apt install  winehq-stable 5.0.1~bionic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package 5.0.1~bionic
E: Couldn't find any package by glob '5.0.1~bionic'
E: Couldn't find any package by regex '5.0.1~bionic'



```

---

### Post by urubu66 on 2020-07-16
So I followed this manual

[http://ubuntuhandbook.org/index.php/2020/01/install-wine-5-0-stable-ubuntu-18-04-19-10/](http://ubuntuhandbook.org/index.php/2020/01/install-wine-5-0-stable-ubuntu-18-04-19-10/)

seems to have installed

```
wine --version
wine-5.0.1
```

However it's still useless to me, because if I rightclick on an .exe and open with view all application, wine is not on the list. 
(I'm sure the .exe is compatible with wine)

How can I get it added so I can actually use it?

---

### Post by dino99 on 2020-07-16
try the terminal command line:

sudo wine app.exe (replace app by the real name indeed)

if it fails you will get additional error(s) to dig around

---

### Post by &amp;KyT$0P# on 2020-07-16
> **dino99 said:**
> try the terminal command line:

sudo wine app.exe (replace app by the real name indeed)

:shock: Why run wine as root?  Isn't that highly dangerous?!?

---

### Post by CatKiller on 2020-07-16
> **urubu66 said:**
> However it's still useless to me, because if I rightclick on an .exe and open with view all application, wine is not on the list. 

Wine used to have that ability by default, but it got taken out for reasons that are unclear. The solution is to copy some desktop files from an examples directory to an applications directory and then logout, which should restore the old behaviour.

---

