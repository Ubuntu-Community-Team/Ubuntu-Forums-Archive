---
title: "Where to see Softwar-Updater install log?"
date: 2024-02-13
forum: General Help
---

### Post by ishmael3 on 2024-02-13
I have my Software Updater set to check weekly for updates. At which time it finds various updates to download and install.  
 
 When it installs, it opens a terminal window and shows the unpacking and installing of each update. As part of that process it sometimes shows comments and warnings that I might like to learn more about; but it all goes by too quickly for me to note or remember everything, and, when done installing, the window simply closes.  
 
Linux must keep a log of this process. Could someone kindly instruct me where to look? (Ubuntu 22.04)

 Thank you.

---

### Post by deadflowr on 2024-02-13
look in /var/log/apt/
should be two files history.log and term.log.
Also look at the log file /var/log/dpkg.log

If auto-updates are enabled look in /var/log/unattended-upgrades.

---

### Post by ishmael3 on 2024-02-13
Thank you.
 
 The *term.log* file in *var/log/apt**/  *was just what I needed.

---

