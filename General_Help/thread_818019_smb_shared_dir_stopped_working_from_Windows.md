---
title: "smb shared dir stopped working from Windows"
date: 2008-06-04
forum: General Help
---

### Post by lordgreg on 2008-06-04
Hi..

i'm not sure, but after the upgrade to 8.04, my samba shared folder in ubuntu (/home/user/Share) stopped working when trying to access it from Windows XP. 

1. folder is set to 777, my username is owner of the Share directory.
2. i've tried to reinstall samba, nautilus (as i've found somewhere to be a problem after upgrading to 8.04
3. here is my smb.conf:
```
[Share]
        path = /home/gregor/Share
        read only = No
        public = Yes
        writeable = Yes
        browseable = Yes
        guest ok = Yes
        create mask = 0777
        directory mask = 0777
        force user = nobody
        force group = nogroup

```

Any ideas what is causing that? 

When accessing only the ip of ubuntu computer from WinXP, it shows me printers, Share directory, but upon clicking on Share dir, it gives me the standard "\x.x.x.x\Share is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions"


Please help me out here. No idea what else to do :(

Thank you and best regards,



Gregor

---

### Post by slasko on 2008-06-04
Hi 

I have the exact same problem :(

---

### Post by lordgreg on 2008-06-05
can anyone point us to working result then? i did searched for the same threads on this forum, but all i found was someone stating he found a temp workaround with reinstalling samba and nautilus. this, however, doesn't work for me. anyone?

---

### Post by lordgreg on 2008-06-06
*bump*-ing for a need of good reply/help!

---

### Post by iaculallad on 2008-06-06
Downgrade your [samba-common]("http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.3_i386.deb") and [smbfs]("http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbfs_3.0.26a-1ubuntu2.3_i386.deb") files.

Download the files linked above and downgrade the package on your terminal:

Files will either be downloaded on your Desktop so change directory before running the commands below:

> cd ~/Desktop

```
dpkg -i --force-downgrade smbfs_3.0.26a-1ubuntu2.3_i386.deb

dpkg -i --force-downgrade samba-common_3.0.26a-1ubuntu2.3_i386.deb

```

---

### Post by lordgreg on 2008-06-06
hi and thank you for your reply. i downgraded samba & commons for it, rebooted samba service, still, i have the same problem. should i restart whole computer for effect or something?

---

### Post by iaculallad on 2008-06-06
> **lordgreg said:**
> hi and thank you for your reply. i downgraded samba & commons for it, rebooted samba service, still, i have the same problem. should i restart whole computer for effect or something?

You could try restarting SAMBA on your terminal:

```

sudo /etc/init.d/samba restart
```

OR

Do a system reboot.

---

### Post by lordgreg on 2008-06-06
hi and thanks again.

i've restarted samba, which didn't helped. rebooted pc, didn't helped either. one thing that is appearing now in synaptic- it complains those 2 "downgrades" have broken dependencies. 

huh?

---

### Post by iaculallad on 2008-06-06
Try running this commands in your terminal if it will resolve your broken dependencies:

```
sudo dpkg --configure -a
sudo apt-get update && sudo apt-get upgrade
```

Then try restarting SAMBA:

```
sudo /etc/init.d/samba restart
```

---

### Post by lordgreg on 2008-06-06
now, we have a problem with that:

after doing update & upgrade, i get:

```
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  samba: Depends: samba-common (= 3.0.28a-1ubuntu4.1) but 3.0.26a-1ubuntu2.3 is installed
  smbclient: Depends: samba-common (= 3.0.28a-1ubuntu4.1) but 3.0.26a-1ubuntu2.3 is installed
E: Unmet dependencies. Try using -f.

```


then, when runing -f:

```
gregor@gpbox:~$ apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libotr2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  samba-common smbfs
The following packages will be upgraded:
  samba-common smbfs
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2932kB of archives.
After this operation, 877kB disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Segmentation fault
```

Segmentation fault? updater constantly nags me with 2 never versions of samba & samba-common, since i have now downgraded.

---

### Post by slasko on 2008-06-06
Hi, I have reinstalled samba a number of times and made modification to the smb.conf with no success. In short i have messed everything up :confused:

Now the smb.conf looks like this:

> [global]
workgroup = matrix
netbios name =server
encrypted password = yes
security = user
guest account = nobody
invalid users = root

#Share Definitions

[homes]
        comment = Home Directories
        browseable = yes
        writable = yes
        security mask = 0700
        create mask = 0700

[share]
comment = Public Folder
path = /home/server/share
public = yes
writable = yes

The samba share can be accessed from my windows xp machine now, but i seems to have missed a step to grant access to my Ubuntu desktop machine?
From my Ubuntu desktop I can see and browse the share, but not write to it.

---

