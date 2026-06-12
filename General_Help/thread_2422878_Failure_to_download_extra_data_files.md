---
title: "Failure to download extra data files"
date: 2019-07-14
forum: General Help
---

### Post by dannyk2 on 2019-07-14
I have installed Ubuntu 18.04.2 LTS without any problems except, i keep getting the following message popping up on my screen all the time and i don't have an idea how to resolve this problem.  The message is:   Failure to download extra data files    ttf-mscorefonts-installer  Could someone help me please.

---

### Post by &amp;KyT$0P# on 2019-07-14
Try connecting to the internet and running these commands in Terminal -
```
sudo apt-get update
sudo apt-get --reinstall install ttf-mscorefonts-installer
```

If you get errors, please post the output from those commands.

---

### Post by cruzer001 on 2019-07-14
And use the "Tab" key to accept terms.

---

### Post by rbmorse on 2019-07-14
You might have to hit the <enter> key after using the <tab> to highlight "OK" on the terms screen.

---

### Post by dannyk2 on 2019-07-15
I have run the two commands as sugested in the terminal   ```
 sudo apt-get update && sudo apt-get --reinstall install ttf-mscorefonts-installer 
```    The output of the second command is as follows:    Reading package lists... Done Building dependency tree        Reading state information... Done 0 to upgrade, 0 to newly install, 1 reinstalled, 0 to remove and 16 not to upgrade. Need to get 27.6 kB of archives. After this operation, 0 B of additional disk space will be used. Get:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/multiverse amd64 ttf-mscorefonts-installer all 3.6ubuntu2 [27.6 kB] Fetched 27.6 kB in 0s (413 kB/s)                    Preconfiguring packages ... (Reading database ... 172952 files and directories currently installed.) Preparing to unpack .../ttf-mscorefonts-installer_3.6ubuntu2_all.deb ... mscorefonts-eula license has already been accepted Unpacking ttf-mscorefonts-installer (3.6ubuntu2) over (3.6ubuntu2) ... Processing triggers for update-notifier-common (3.192.1.7) ... ttf-mscorefonts-installer: processing... ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe) Get:1 [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe) [198 kB] Fetched 198 kB in 1s (255 kB/s)                                                               ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/arial32.exe](http://downloads.sourceforge.net/corefonts/arial32.exe) Err:1 [http://downloads.sourceforge.net/corefonts/arial32.exe](http://downloads.sourceforge.net/corefonts/arial32.exe)   Redirection from https to 'http://downloads.sourceforge.net/mirrorproblem?failedmirror=netcologne.dl.sourceforge.net' is forbidden [IP: 78.35.24.46 443] E: Failed to fetch [https://netcologne.dl.sourceforge.net/project/corefonts/the](https://netcologne.dl.sourceforge.net/project/corefonts/the) fonts/final/arial32.exe  Redirection from https to 'http://downloads.sourceforge.net/mirrorproblem?failedmirror=netcologne.dl.sourceforge.net' is forbidden [IP: 78.35.24.46 443] E: Download Failed Setting up ttf-mscorefonts-installer (3.6ubuntu2) ... Processing triggers for fontconfig (2.12.6-0ubuntu2) ...

---

