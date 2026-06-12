---
title: "No option to upgrade to 13.04"
date: 2013-04-30
forum: General Help
---

### Post by typos1 on 2013-04-30
Update manager does not show any option to upgrade to 13.04 on my system, I ve been trying for 4 days now. Can anyone help. There is an outstanding update "Userspace interface to DRM services - runtime" that will not install and hasnt for the last month. I have submitted error reports for it, but it still wont install. Could this be why ? Cant wait to upgrade as 12.10 is the most buggy, slow and unstable release yet.

I get this if I try to install:

installArchives() failed: (Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 265059 files and directories currently installed.) 
Preparing to replace libdrm2:amd64 2.4.39-0ubuntu1 (using .../libdrm2_2.4.39-0ubuntu1_amd64.deb) ... 
Unpacking replacement libdrm2:amd64 ... 
dpkg: error processing /var/cache/apt/archives/libdrm2_2.4.39-0ubuntu1_amd64.deb (--unpack): 
 trying to overwrite shared '/usr/share/doc/libdrm2/changelog.Debian.gz', which is different from other instances of package libdrm2:amd64 
Errors were encountered while processing: 
 /var/cache/apt/archives/libdrm2_2.4.39-0ubuntu1_amd64.deb 
Error in function:  



Thanks

---

### Post by David D. on 2013-04-30
You may have upgrade to LTS versions only selected in settings.  Open the software updater, select settings, and go to the Updates tab.  At the bottom where it states "Notify me of new Ubuntu version" ensure that "for any new version" is selected.

---

### Post by dino99 on 2013-04-30
[http://askubuntu.com/questions/136148/upgrade-from-11-10-to-12-04-no-upgrade-option-available-in-update-manager](http://askubuntu.com/questions/136148/upgrade-from-11-10-to-12-04-no-upgrade-option-available-in-update-manager)

---

### Post by typos1 on 2013-04-30
> **David D. said:**
> You may have upgrade to LTS versions only selected in settings.  Open the software updater, select settings, and go to the Updates tab.  At the bottom where it states "Notify me of new Ubuntu version" ensure that "for any new version" is selected.

Yeah, already checked that.

---

### Post by ibjsb4 on 2013-04-30
```
sudo apt-get update && sudo apt-get dist-upgrade
```

Does that go smoothly?

---

### Post by typos1 on 2013-04-30
Yeah, ta, I got that from the second reply, I ll backup and try it :-)

---

### Post by typos1 on 2013-04-30
Tried it the command line way, but it stops at ttf-mscorefonts-installer, I press enter as promted but nothing happens . . . :-/

So now in mid upgrade and dont know how to abort it in the command line

---

### Post by ibjsb4 on 2013-04-30
Its **Tab **+ Enter

---

### Post by typos1 on 2013-04-30
Lol, yeah I googled it expecting to find nothing, but found out it was the tab button ! thanks though, just panicked a bit mid upgrade

---

### Post by typos1 on 2013-05-01
After upgrade unity doesnt work properly - when I click on an icon thats open on another desktop it doesnt take me there

---

