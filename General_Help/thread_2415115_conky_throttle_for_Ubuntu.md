---
title: "conky throttle for Ubuntu"
date: 2019-03-20
forum: General Help
---

### Post by RobGoss on 2019-03-20
Hello everyone, I have Ubuntu 18.04 installed and recently installed Conky manager, is there anyway to change the font color and other aspects of conky like MX Linux has. I believe they use conky throttle or something along the line

Thanks so much

---

### Post by again? on 2019-04-01
The application used as a supplement to conky-manager is mx-conky.
You can install by adding the mx repo.
From the repo I installed conky-manager and mx-conky.

**_Add the repo signing key_**
```
cd ~/Downloads
wget http://teharris.net/mx17repo.asc
sudo apt-key add mx17repo.asc
```

**_Add the mx repo_**
```
sudo add-apt-repository "deb http://mxrepo.com/mx/repo/ stretch main non-free"
```

**_Install conky-manager_** (if not already installed)
If you install conky-manager from the mx repository it depends on a package called realpath.
Realpath was moved into the coreutils package a number of years ago in Ubuntu.
To satisfy the dependency you can install the xenial package which is an empty transitional package.
```
cd ~/Downloads
wget http://us.archive.ubuntu.com/ubuntu/pool/main/c/coreutils/realpath_8.25-2ubuntu3~16.04_all.deb
sudo apt install ~/Downloads/realpath_8.25-2ubuntu3~16.04_all.deb
sudo apt install conky-manager
```

**_Install mx-conky_**
```
sudo apt install mx-conky
```

**_*** Remove the mx repo to avoid package conflicts ***_**
```
sudo add-apt-repository -r "deb [http://mxrepo.com/mx/repo/](http://mxrepo.com/mx/repo/) stretch main non-free"
```


**Note: mx-conky pulls in a libcmd package from the mx repos which is not available in Ubuntu 
and is used by mx packages.
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] apt rdepends libcmd**
libcmd
Reverse Depends:
  Depends: custom-toolbox
  Depends: mx-user
  Depends: mx-snapshot
  Depends: mx-repo-manager
  Depends: mx-packageinstaller
  Depends: mx-network-assistant
  Depends: mx-live-usb-maker
  Depends: mx-installer
  Depends: mx-conky
  Depends: mx-codecs
  Depends: mx-cleanup
  Depends: mx-boot-options
```
If you remove mx-conky, you can remove libcmd as well.

---

