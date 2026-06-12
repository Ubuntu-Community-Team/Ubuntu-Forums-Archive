---
title: "Update Reports 'Misspelling&quot; in Sources.List for VirtualBox !?!"
date: 2019-12-09
forum: General Help
---

### Post by Rick St. George on 2019-12-09
Tried to find an answer to this, someone must have run into this ...? Attempting "update" in terminal we get;

Skipping acquire of configured file 'contrib/source/Sources' as repository 'http://download.virtualbox.org/virtualbox/debian bionic InRelease' does not seem to provide it (sources.list entry misspelt?)

According to several websites, it is not misspelt!  Any suggestions? I use VirtualBox to Run WinXP to run Trading Software which can only run in Windows. Thanks!

I also get this ... 

> 
sudo aptitude update
W: Target Packages (contrib/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list.d/virtualbox.org.list:1
W: Target Packages (contrib/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list.d/virtualbox.org.list:1
W: Target DEP-11 (contrib/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list.d/virtualbox.org.list:1
W: Target DEP-11 (contrib/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list.d/virtualbox.org.list:1
W: Target DEP-11-icons-small (contrib/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list.d/virtualbox.org.list:1
W: Target DEP-11-icons (contrib/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list.d/virtualbox.org.list:1
W: Target CNF (contrib/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list.d/virtualbox.org.list:1
W: Target CNF (contrib/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list.d/virtualbox.org.list:1
W: You may want to update the package lists to correct these missing files
Hit [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) bionic InRelease
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-security InRelease               
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease                
Hit [http://ppa.launchpad.net/kdenlive/kdenlive-stable/ubuntu](http://ppa.launchpad.net/kdenlive/kdenlive-stable/ubuntu) bionic InRelease   
Hit [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic InRelease                  
Hit [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease                        
Hit [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security InRelease                  
Hit [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) bionic InRelease
Hit [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates InRelease
Hit [http://ppa.launchpad.net/ubuntustudio-ppa/backports/ubuntu](http://ppa.launchpad.net/ubuntustudio-ppa/backports/ubuntu) bionic InRelease
Hit [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) bionic InRelease
W: Target Packages (contrib/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list.d/virtualbox.org.list:1
W: Target Packages (contrib/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list.d/virtualbox.org.list:1
W: Target DEP-11 (contrib/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list.d/virtualbox.org.list:1
W: Target DEP-11 (contrib/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list.d/virtualbox.org.list:1
W: Target DEP-11-icons-small (contrib/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list.d/virtualbox.org.list:1
W: Target DEP-11-icons (contrib/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list.d/virtualbox.org.list:1
W: Target CNF (contrib/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list.d/virtualbox.org.list:1
W: Target CNF (contrib/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list.d/virtualbox.org.list:1
W: Skipping acquire of configured file 'contrib/source/Sources' as repository 'http://download.virtualbox.org/virtualbox/debian bionic InRelease' does not seem to provide it (sources.list entry misspelt?)
W: Target Packages (contrib/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list.d/virtualbox.org.list:1
W: Target Packages (contrib/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list.d/virtualbox.org.list:1
W: Target DEP-11 (contrib/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list.d/virtualbox.org.list:1
W: Target DEP-11 (contrib/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list.d/virtualbox.org.list:1
W: Target DEP-11-icons-small (contrib/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list.d/virtualbox.org.list:1
W: Target DEP-11-icons (contrib/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list.d/virtualbox.org.list:1
W: Target CNF (contrib/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list.d/virtualbox.org.list:1
W: Target CNF (contrib/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:13 and /etc/apt/sources.list.d/virtualbox.org.list:1
          


How do I clean all this up ???  Thanks!

):P

---

### Post by deadflowr on 2019-12-09
First decide which source you want.
You have two.
Either remove the entry for virtualbox from the main sources.list file or remove the virtualbox list file from the sources.list.d directory.

From there you should see what and why it's trying to skip anything.

---

### Post by Rick St. George on 2019-12-09
1. Deleted all files in sources.list.d directory

```

sudo rm -f /etc/apt/sources.list.d/*.*

```

2. Deleted Backup and Save file

```

sudo rm -f  /etc/apt/sources.list.save
sudo rm -f /etc/apt/sources.backup
sudo rm -f /etc/apt/sources.list.distUpgrade

```

3. Deleted all but essential in sources.list

```

###### Ubuntu Main Repos
deb [arch=amd64] http://us.archive.ubuntu.com/ubuntu bionic main restricted

###### Ubuntu Security Repos
deb [arch=amd64] http://security.ubuntu.com/ubuntu bionic-security main restricted
# deb-src [arch=amd64] http://security.ubuntu.com/ubuntu bionic-security main restricted
deb [arch=amd64] http://security.ubuntu.com/ubuntu bionic-security universe
# deb-src [arch=amd64] http://security.ubuntu.com/ubuntu bionic-security universe
deb [arch=amd64] http://security.ubuntu.com/ubuntu bionic-security multiverse
# deb-src [arch=amd64] http://security.ubuntu.com/ubuntu bionic-security multiverse
## Major bug fix updates after the final release
deb [arch=amd64] http://archive.ubuntu.com/ubuntu/ bionic-updates main restricted
# deb-src [arch=amd64] http://archive.ubuntu.com/ubuntu/ bionic-updates main restricted

###### VirtualBox Repo
deb [arch=amd64] http://download.virtualbox.org/virtualbox/debian bionic contrib
# deb-src [arch=amd64] http://download.virtualbox.org/virtualbox/debian bionic contrib

```

4. Update now shows;

> 
Hit [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) bionic InRelease
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease                                       
Get: 1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]
Get: 2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [88.7 kB]      
Fetched 177 kB in 1s (147 kB/s)           


Done!  Hope this helps someone else!
OS: UbuntuStudio v18.04; kernel 4.15.0.72

---

