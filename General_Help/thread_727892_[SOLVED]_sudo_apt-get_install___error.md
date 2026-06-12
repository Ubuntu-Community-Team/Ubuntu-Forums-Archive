---
title: "[SOLVED] sudo apt-get install   error"
date: 2008-03-18
forum: General Help
---

### Post by bigbrovar on 2008-03-18
i was tring to install second live .. appearently it need to download additional package for the installation to complete .. while doing this.. my system swiitched off due to power cut ... not when i try to install anything i get these error** E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.**


i have tried doing  sudo dpkg --configure -a   and   sudo apt-get install -f but still the same ... although i can still install using **sudo aptitude install** the porblem is that i cant open synaptics it gives me this error E: Internal error opening cache (1). Please report. what can i do ..... can anyway pls help me with this


when i do sudo aptitude remove secondlife-install i get these error  **  E: Sub-process /usr/bin/dpkg returned an error code (1)**

---

### Post by Ub1476 on 2008-03-18
Have you tried to reinstall as it asks?

```
sudo apt-get install *packagename* --reinstall
```

Or maybe clearing unnecessary packages:

```
sudo apt-get autoremove
```

Hopefully then wont tun into an error message:???:

---

### Post by bigbrovar on 2008-03-18
> Have you tried to reinstall as it asks?

Code:
sudo apt-get install *packagename* --reinstall
Or maybe clearing unnecessary packages:

Code:
sudo apt-get autoremove
Hopefully then wont tun into an error message

thanks for ur help bro .. but when i tried it retured the same error  [B]E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.
[/B]  i searched google and i saw this solution  >  For some reason you may have damaged an archive and/or lock file. You may try to remove the file /var/cache/apt/pkgcache.bin and recreate it with
Code:

sudo rm -r /var/cache/apt/pkgcache.bin
sudo apt-get keep-all

You may also look at the /var/lib/dpkg directory, that may be compromised as well.

NOTE!! I never tried this, so it's really on your own risk. As an alternative I suggest re-installing Ubuntu.
   
and 

> 

Try with "sudo rm /var/lib/dpkg/lock"
Also make sure you don't have another package manager running, like running a dpkg command with synaptics open.

hope this solution can be applied to ubuntu .... further more it seems most pple that have this problem ended reinstalling thier system and i dont want that for my system .. pls help

---

### Post by Ub1476 on 2008-03-18
I'm not very familiar with the roots of the apt-get system, so I won't tell you to remove anything. Maybe you can cd into /var/lib or /usr/bin/, and see if you can find any clues there? Possible you can download SL from [Ubuntu Repos]("http://packages.ubuntu.com/") and try to install it manually.

---

### Post by bigbrovar on 2008-03-18
manual installation too doesnt work ... i will try installing it with aptitude cus that is the only thing working for me

---

### Post by Ub1476 on 2008-03-18
Have you checked out [this thread]("http://ubuntuforums.org/showthread.php?t=696741")?

```
sudo gedit /var/lib/dpkg/status
```
Delete the section for libavahi-core5. #I suppose this is something else in your case
```
sudo mv /var/lib/dpkg/info /var/lib/dpkg/info_old
sudo mkdir /var/lib/dpkg/info
sudo apt-get update
sudo apt-get -f install 
```

---

### Post by bigbrovar on 2008-03-18
thanks bro ... i have solved it now .. i went to  sudo gedit /var/lib/dpkg/status and i removed secondlife from the list .. Beng .. that was it everything went back to normal..... God do i love ubuntu sooooooooooooooooooooo much . :guitar: .. even when it has a problem .. bcus its opensource .. its easy to solve the problem bcus pple know how things run .. and with just a line of code everything is fixed .. cant imagine if it was windoze .... i would be cleaning my recovery disk for a reinstall .....thank u every much u have made my day today ..   :lolflag:     Ub1476

---

