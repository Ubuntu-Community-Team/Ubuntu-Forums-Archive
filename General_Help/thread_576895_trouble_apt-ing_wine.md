---
title: "trouble apt-ing wine"
date: 2007-10-15
forum: General Help
---

### Post by vizitorq on 2007-10-15
```

neema@pavilion:~ % uname -a
Linux pavilion 2.6.20-16-generic #2 SMP Sun Sep 23 18:31:23 UTC 2007 x86_64 GNU/Linux
neema@pavilion:~ % cat /etc/apt/sources.list | grep wine
deb http://wine.budgetdedicated.com/apt feisty main #WineHQ - Ubuntu 7.04 "Feisty Fawn"
deb-src http://wine.budgetdedicated.com/apt feisty main #WineHQ - Ubuntu 7.04 "Feisty Fawn"
neema@pavilion:~ % sudo apt-get install wine            
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate


```
what is going on here?

---

### Post by ruibernardo on 2007-10-15
When you type

```
 sudo apt-get update
```

you must be having errors about that repository. Maybe you forgot to add the key of that repository. Look at WineHQ webpage to see how to add their key and repository: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb).

After that run "sudo apt-get update" again and then you can install wine package.

Hope this helps.

---

### Post by vizitorq on 2007-10-15
thanks for the reply. that's the exact guide i followed to get wine on my machine. but it's not working. same error on install. i run zsh as my shell and i have configured tab-completion to best suite my development environment, and when i tab-complete wine, it brings up several possibilities:

```

kumi@throne:~ % sudo apt-get install wine
---- package
wine         wine-dev     wine-doc     winefish     winesetuptk  wine-utils 

```

it wouldn't do that unless it actually HAD those options. before i added the repositories to my sources.list it wouldn't bring anything up when i tried to tab-complete wine with apt-get. so, there must be some other reason why it won't install, or why this happens:

```

kumi@throne:~ % sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

```

i could use some help with this one. i can't be the only one having trouble with this. please help.

---

### Post by ruibernardo on 2007-10-15
This is very strange. Could you please confirm that your two boxes are really using and reading the wine repository by running "sudo apt-get update" on each one of them and looking for a repository error?

---

### Post by vizitorq on 2007-10-16
i agree it is strange. sorry for not posting the output before:

```

kumi@throne:~ % sudo apt-get update
Password:
Get:1 http://download.tuxfamily.org feisty Release.gpg [189B]
Ign http://download.tuxfamily.org feisty/eyecandy-amd64 Translation-en_US   
Get:2 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US       
Get:3 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US              
Hit http://download.tuxfamily.org feisty Release
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com feisty-security Release              
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:4 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Get:5 http://us.archive.ubuntu.com feisty-backports Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty-backports/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release                      
Hit http://download.tuxfamily.org feisty/eyecandy-amd64 Packages               
Hit http://security.ubuntu.com feisty-security/main Packages                   
Hit http://us.archive.ubuntu.com feisty-updates Release
Hit http://us.archive.ubuntu.com feisty-backports Release           
Hit http://security.ubuntu.com feisty-security/restricted Packages  
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://us.archive.ubuntu.com feisty/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/main Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Sources
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://us.archive.ubuntu.com feisty-backports/main Packages
Hit http://us.archive.ubuntu.com feisty-backports/restricted Packages
Hit http://us.archive.ubuntu.com feisty-backports/universe Packages
Hit http://us.archive.ubuntu.com feisty-backports/multiverse Packages
Hit http://us.archive.ubuntu.com feisty-backports/main Sources
Hit http://us.archive.ubuntu.com feisty-backports/restricted Sources
Hit http://us.archive.ubuntu.com feisty-backports/universe Sources
Hit http://us.archive.ubuntu.com feisty-backports/multiverse Sources
Fetched 5B in 1s (3B/s)  
Reading package lists... Done

```

i don't know what an error looks like.

---

### Post by ruibernardo on 2007-10-16
If your sources.list had the repository from winehq active, they would have something like this:

```
Get:6 http://wine.budgetdedicated.com feisty Release.gpg [191B]              
Ign http://wine.budgetdedicated.com feisty/main Translation-pt_PT
Get:7 http://wine.budgetdedicated.com feisty Release [1007B]
Ign http://wine.budgetdedicated.com feisty/main Packages
Get:8 http://wine.budgetdedicated.com feisty/main Sources [779B]
Get:9 http://wine.budgetdedicated.com feisty/main Packages [1084B]
```And, in your case, they are not listed.

Please follow the instructions from the page [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb). To get the keys of the repository:
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

```And then, to actually add the repository:
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
```(please note that the winehq repository isn't directly added to sources.list, but to the file winehq.list in the directory /etc/apt/sources.list.d/).

Still, wine should have been available to you, from the universe repository, although it is an older version (0.9.33). Please confirm you have your universe repository active in the menu System, Adminstration, Software Sources or in Synaptic.

Don't forget to update the repositories after changing them:

```
 sudo apt-get update
```or press "Reload" on Synaptic.

In Synaptic, search for "wine" to confirm you have wine available, or type

```
apt-cache search wine | grep wine

```The output should be something like this (only universe repository, winehq repository disabled in "Software Sources"):

```
user@desktop$ apt-cache search wine | grep wine
libwine - Microsoft Windows Compatibility Layer (Dummy Package)
libwine-dev - Microsoft Windows Compatibility Layer (Dummy Package)
wine - Microsoft Windows Compatibility Layer (Binary Emulator and Library)
wine-dev - Microsoft Windows Compatibility Layer (Development files)
winefish - LaTeX Editor based on Bluefish
```Hope this helps you somehow.

---

