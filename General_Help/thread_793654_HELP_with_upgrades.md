---
title: "HELP with upgrades"
date: 2008-05-14
forum: General Help
---

### Post by roc320 on 2008-05-14
Hello I been following the multimedia thread about getting different codecs, flash, java, etc to work on version 8.04. I've just received this error message when I tried to run Synaptic Package Manager: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I did the following command in the console 'sudo dpkg --configure -a' but there was not output at all. Any help to fix this and to get Synaptic back to normal would be great thanks. Roc

---

### Post by overdrank on 2008-05-14
> **roc320 said:**
> Hello I been following the multimedia thread about getting different codecs, flash, java, etc to work on version 8.04. I've just received this error message when I tried to run Synaptic Package Manager: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I did the following command in the console 'sudo dpkg --configure -a' but there was not output at all. Any help to fix this and to get Synaptic back to normal would be great thanks. Roc

Hi and could post any errors of these commands in the terminal
```
sudo apt-get install -f 
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by roc320 on 2008-05-14
Ok when I ran the command: sudo apt-get install -f, I got the following error: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the prob

When I ran the other 2 commands I got the same error. Any help would be great.

---

### Post by tamoneya on 2008-05-14
do just as it says just remember that you need root privileges. It would look like this:
```
sudo dpkg --configure -a
```

---

### Post by roc320 on 2008-05-17
Thanks guys I got situation under control.

---

