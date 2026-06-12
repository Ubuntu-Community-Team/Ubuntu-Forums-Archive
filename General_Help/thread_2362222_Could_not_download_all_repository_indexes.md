---
title: "Could not download all repository indexes"
date: 2017-05-25
forum: General Help
---

### Post by makem2 on 2017-05-25
Recently updating repository index in synaptic has started giving error which seem to be increasing. The error is very long and appears complex so I am loath to try editing without some guidance.

Error message:


Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1Target Translations (main/i18n/Translation-en_GB) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google.list:1Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'http://dl.google.com/linux/chrome/deb stable InRelease' doesn't support architecture 'i386'The repository 'http://cz.archive.ubuntu.com/ubuntu xenial Release' does not have a Release file.Data from such a repository can't be authenticated and is therefore potentially dangerous to use.See apt-secure(8) manpage for repository creation and user configuration details.Failed to fetch [http://cz.archive.ubuntu.com/ubuntu/dists/xenial/main/binary-amd64/Packages](http://cz.archive.ubuntu.com/ubuntu/dists/xenial/main/binary-amd64/Packages)  Cannot initiate the connection to cz.archive.ubuntu.com:80 (2001:1488:ffff::63). - connect (101: Network is unreachable) [IP: 2001:1488:ffff::63 80]Some index files failed to download. They have been ignored, or old ones used instead.

```

makem@ssdTOSH:/etc/apt/sources.list.d$ ls -la
total 92
drwxr-xr-x 2 root root 4096 Apr 19 00:33 .
drwxr-xr-x 6 root root 4096 Sep 14  2016 ..
-rw-r--r-- 1 root root   66 May 25 20:11 cinelerra-ppa-ubuntu-ppa-xenial.list
-rw-r--r-- 1 root root   66 May 25 20:11 cinelerra-ppa-ubuntu-ppa-xenial.list.save
-rw-r--r-- 1 root root   82 May 25 20:11 danielrichter2007-ubuntu-grub-customizer-xenial.list
-rw-r--r-- 1 root root   82 May 25 20:11 danielrichter2007-ubuntu-grub-customizer-xenial.list.save
-rw-r--r-- 1 root root  189 May 25 20:11 google-chrome.list
-rw-r--r-- 1 root root  189 May 25 20:11 google-chrome.list.save
-rw-r--r-- 1 root root  175 May 25 20:11 google-earth.list
-rw-r--r-- 1 root root  175 Sep 14  2016 google-earth.list.distUpgrade
-rw-r--r-- 1 root root  175 May 25 20:11 google-earth.list.save
-rw-r--r-- 1 root root   55 May 25 20:11 google.list
-rw-r--r-- 1 root root   55 May 25 20:11 google.list.save
-rw-r--r-- 1 root root   72 May 25 20:11 inameiname-stable-trusty.list
-rw-r--r-- 1 root root  138 Sep 14  2016 inameiname-stable-trusty.list.distUpgrade
-rw-r--r-- 1 root root   72 May 25 20:11 inameiname-stable-trusty.list.save
-rw-r--r-- 1 root root   72 May 25 20:11 openshot_developers-ubuntu-ppa-xenial.list
-rw-r--r-- 1 root root   72 May 25 20:11 openshot_developers-ubuntu-ppa-xenial.list.save
-rw-r--r-- 1 root root   84 May 25 20:11 qbittorrent-team-ubuntu-qbittorrent-stable-xenial.list
-rw-r--r-- 1 root root   84 May 25 20:11 qbittorrent-team-ubuntu-qbittorrent-stable-xenial.list.save
-rw-r--r-- 1 root root    0 May 25 20:10 qbittorrent-team-ubuntu-qbittorrent-unstable-xenial.list
-rw-r--r-- 1 root root    0 May 25 20:10 qbittorrent-team-ubuntu-qbittorrent-unstable-xenial.list.save
-rw-r--r-- 1 root root   81 May 25 20:11 xenial-partner.list
-rw-r--r-- 1 root root   81 May 25 20:11 xenial-partner.list.save
-rw-r--r-- 1 root root    0 May 25 20:11 xubuntu-dev-xfce-4_12-trusty.list
-rw-r--r-- 1 root root   76 Sep 14  2016 xubuntu-dev-xfce-4_12-trusty.list.distUpgrade
-rw-r--r-- 1 root root    0 May 25 20:11 xubuntu-dev-xfce-4_12-trusty.list.save
makem@ssdTOSH:/etc/apt/sources.list.d$
makem@ssdTOSH:/etc/apt/sources.list.d$ cat /etc/issue
Ubuntu 16.04.2 LTS \n \l

```

---

### Post by QIII on 2017-05-25
Hello!

Code tags would have left the wall of text in your post in a formatted state and it would have been easier to read.  Unfortunately, adding code tags now does not seem to help.

---

### Post by deadflowr on 2017-05-25
Look at both google-chrome.list and google.list and compare if they have the same entries, which is what it's basically telling you.
And if they do have the same entries, remove one of them, perhaps the google.list file, since it's non-default anyway. 
(google-chrome.list is the normal file name)


The second problem is that the system is trying to connect to the regular Ubuntu repos using ipv6, which from time to time does what it has to you. (rare but I've seen it here and there)
Usually all you need to do is try again.
Worse case, try forcing ipv4
```
apt-get -o Acquire::ForceIPv4=true update
apt-get -o Acquire::ForceIPv4=true upgrade
```
From here: [https://askubuntu.com/questions/759524/problem-with-ipv6-sudo-apt-get-update-upgrade]("https://askubuntu.com/questions/759524/problem-with-ipv6-sudo-apt-get-update-upgrade")
But like I stated, a re-run should fix it, if only after a while.

I think once you get that connection issue fixed, it should fix the  Release file issue the repo is showing.

Edit:
To add: the google-chrome.list file needs the entry to read like this
```
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
```
as it needs the [arch=amd64] entry so that apt doesn't look for the i386 packages, since chrome does not have any i386 packages anymore.
And because it has no such packages, it borks without the added part. 
Hope it helps

---

### Post by makem2 on 2017-05-26
Thank you for your interest. I have made the deletion with respect to google as you suggest.

```

makem@ssdTOSH:~$ sudo apt-get -o Acquire::ForceIPv4=true update
[sudo] password for makem: 
Ign:1 http://archive.canonical.com/ubuntu trusty InRelease
Hit:2 http://gb.archive.ubuntu.com/ubuntu xenial InRelease          
Get:3 http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu xenial InRelease [17.5 kB]                                  
Ign:4 http://dl.google.com/linux/chrome/deb stable InRelease                                                                   
Hit:5 http://archive.canonical.com/ubuntu xenial InRelease                                                                     
Get:6 http://gb.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]                               
Hit:7 http://archive.canonical.com/ubuntu trusty Release                                                                                  
Ign:8 http://dl.google.com/linux/earth/deb stable InRelease                                              
Hit:9 http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu xenial InRelease                 
Hit:10 http://dl.google.com/linux/chrome/deb stable Release                        
Hit:11 http://ppa.launchpad.net/openshot.developers/ppa/ubuntu xenial InRelease                          
Hit:12 http://dl.google.com/linux/earth/deb stable Release               
Get:13 http://gb.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]
Hit:14 http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu xenial InRelease
Get:15 http://gb.archive.ubuntu.com/ubuntu xenial-security InRelease [102 kB]       
Get:16 http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu xenial/main amd64 Packages [1,848 B]
Fetched 326 kB in 0s (403 kB/s)                                 
Reading package lists... Done
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target Translations (universe/i18n/Translation-en_GB) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target Translations (universe/i18n/Translation-en_GB) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53

makem@ssdTOSH:~$ sudo apt-get -o Acquire::ForceIPv4=true upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libbonobo2-0 libbonobo2-common libgles1-mesa libgnome-2-0 libgnome2-common libopenshot-audio3 liborbit-2-0 linux-headers-4.4.0-71
  linux-headers-4.4.0-71-generic linux-headers-4.4.0-72 linux-headers-4.4.0-72-generic linux-headers-4.4.0-75 linux-headers-4.4.0-75-generic
  linux-image-4.4.0-71-generic linux-image-4.4.0-72-generic linux-image-4.4.0-75-generic linux-image-extra-4.4.0-71-generic
  linux-image-extra-4.4.0-72-generic linux-image-extra-4.4.0-75-generic linux-signed-image-4.4.0-71-generic linux-signed-image-4.4.0-72-generic
  linux-signed-image-4.4.0-75-generic snap-confine
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  cinelerra-cv libguicast1-cv libmpeg3cine-cv libquicktimecine-cv libquicktimecine-cv-dev
5 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 8,498 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu xenial/main amd64 cinelerra-cv amd64 1:2.3.git.20170526-0~ppa1~xenial1 [5,414 kB]
Get:2 http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu xenial/main amd64 libguicast1-cv amd64 1:2.3.git.20170526-0~ppa1~xenial1 [467 kB]
Get:3 http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu xenial/main amd64 libmpeg3cine-cv amd64 1:2.3.git.20170526-0~ppa1~xenial1 [2,231 kB]
Get:4 http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu xenial/main amd64 libquicktimecine-cv-dev amd64 1:2.3.git.20170526-0~ppa1~xenial1 [29.4 kB]
Get:5 http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu xenial/main amd64 libquicktimecine-cv amd64 1:2.3.git.20170526-0~ppa1~xenial1 [356 kB]
Fetched 8,498 kB in 1s (4,374 kB/s)          
(Reading database ... 360861 files and directories currently installed.)
Preparing to unpack .../cinelerra-cv_1%3a2.3.git.20170526-0~ppa1~xenial1_amd64.deb ...
Unpacking cinelerra-cv (1:2.3.git.20170526-0~ppa1~xenial1) over (1:2.3.git.20170523-0~ppa1~xenial1) ...
Preparing to unpack .../libguicast1-cv_1%3a2.3.git.20170526-0~ppa1~xenial1_amd64.deb ...
Unpacking libguicast1-cv (1:2.3.git.20170526-0~ppa1~xenial1) over (1:2.3.git.20170523-0~ppa1~xenial1) ...
Preparing to unpack .../libmpeg3cine-cv_1%3a2.3.git.20170526-0~ppa1~xenial1_amd64.deb ...
Unpacking libmpeg3cine-cv (1:2.3.git.20170526-0~ppa1~xenial1) over (1:2.3.git.20170523-0~ppa1~xenial1) ...
Preparing to unpack .../libquicktimecine-cv-dev_1%3a2.3.git.20170526-0~ppa1~xenial1_amd64.deb ...
Unpacking libquicktimecine-cv-dev (1:2.3.git.20170526-0~ppa1~xenial1) over (1:2.3.git.20170523-0~ppa1~xenial1) ...
Preparing to unpack .../libquicktimecine-cv_1%3a2.3.git.20170526-0~ppa1~xenial1_amd64.deb ...
Unpacking libquicktimecine-cv (1:2.3.git.20170526-0~ppa1~xenial1) over (1:2.3.git.20170523-0~ppa1~xenial1) ...
Processing triggers for menu (2.1.47ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu7) ...
/sbin/ldconfig.real: /usr/lib/nvidia-375/libEGL.so.1 is not a symbolic link


/sbin/ldconfig.real: /usr/lib32/nvidia-375/libEGL.so.1 is not a symbolic link


Setting up libguicast1-cv (1:2.3.git.20170526-0~ppa1~xenial1) ...
Setting up libmpeg3cine-cv (1:2.3.git.20170526-0~ppa1~xenial1) ...
Setting up libquicktimecine-cv (1:2.3.git.20170526-0~ppa1~xenial1) ...
Setting up cinelerra-cv (1:2.3.git.20170526-0~ppa1~xenial1) ...
kernel.shmmax = 0x7fffffff
Setting up libquicktimecine-cv-dev (1:2.3.git.20170526-0~ppa1~xenial1) ...
Processing triggers for libc-bin (2.23-0ubuntu7) ...
/sbin/ldconfig.real: /usr/lib/nvidia-375/libEGL.so.1 is not a symbolic link


/sbin/ldconfig.real: /usr/lib32/nvidia-375/libEGL.so.1 is not a symbolic link


Processing triggers for menu (2.1.47ubuntu1) ...

makem@ssdTOSH:~$ sudo apt-get -o Acquire::ForceIPv4=true update
Hit:1 http://gb.archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu xenial InRelease                                            
Ign:3 http://dl.google.com/linux/chrome/deb stable InRelease                                                        
Ign:4 http://archive.canonical.com/ubuntu trusty InRelease                                    
Get:5 http://gb.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]                   
Hit:6 http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu xenial InRelease                                      
Hit:7 http://archive.canonical.com/ubuntu xenial InRelease                                                                     
Ign:8 http://dl.google.com/linux/earth/deb stable InRelease                                                                    
Hit:9 http://ppa.launchpad.net/openshot.developers/ppa/ubuntu xenial InRelease                           
Hit:10 http://archive.canonical.com/ubuntu trusty Release                                                
Hit:11 http://dl.google.com/linux/chrome/deb stable Release                                               
Hit:12 http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu xenial InRelease               
Hit:13 http://dl.google.com/linux/earth/deb stable Release                         
Get:14 http://gb.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]
Get:15 http://gb.archive.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Fetched 306 kB in 0s (366 kB/s)                               
Reading package lists... Done
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target Translations (universe/i18n/Translation-en_GB) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target Translations (universe/i18n/Translation-en_GB) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target DEP-11-ico



```

I am unable to find /etc/apt/sources.list:16 and /etc/apt/sources.list:53 anywhere in the file system so am unable to remove duplicates.

```

makem@ssdTOSH:/etc/apt$ ls -la
total 88
drwxr-xr-x   6 root root  4096 May 26 15:17 .
drwxr-xr-x 156 root root 12288 May 26 15:22 ..
drwxr-xr-x   2 root root  4096 May 26 14:52 apt.conf.d
drwxr-xr-x   2 root root  4096 Apr 10  2014 preferences.d
-rw-r--r--   1 root root  3047 May 25 20:40 sources.list
drwxr-xr-x   2 root root  4096 May 26 15:09 sources.list.d
-rw-r--r--   1 root root  3353 Sep 14  2016 sources.list.distUpgrade
-rw-r--r--   1 root root  3033 May 25 20:40 sources.list.save
-rw-------   1 root root    40 Feb 17  2016 trustdb.gpg
-rw-r--r--   1 root root 16514 Sep 14  2016 trusted.gpg
-rw-r--r--   1 root root 17105 Jun 25  2016 trusted.gpg~
drwxr-xr-x   2 root root  4096 Apr 19 00:27 trusted.gpg.d

```

The error is repeating on every update.

The suggestion below does not correct the error.

```

sudo [COLOR=#111111][FONT=Consolas]echo 'Acquire::ForceIPv4 "true";' | tee /etc/apt/apt.conf.d/99force-ipv4
[/FONT][/COLOR]tee: /etc/apt/apt.conf.d/99force-ipv4: Permission denied[sudo] password for makem:
Acquire::ForceIPv4 "true";
makem@ssdTOSH:~$


```

---

### Post by makem2 on 2017-05-26
> **QIII said:**
> Hello!

Code tags would have left the wall of text in your post in a formatted state and it would have been easier to read.  Unfortunately, adding code tags now does not seem to help.

I obtained the error from Synaptic as text and when put in codes it truncated it drastically, hence the way I posted. However, I find using the command line produces the same error and can be formatted as you suggest.

---

### Post by #&amp;thj^% on 2017-05-26
Those are just Warnings...You have multiple entries as pointed out.
```
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target Translations (universe/i18n/Translation-en_GB) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target Translations (universe/i18n/Translation-en_GB) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:53
W: Target DEP-11-ico
```
Just remove one of each of the above.
EDIT: If this is not clear....you could just try to follow this: [https://askubuntu.com/questions/124017/how-do-i-restore-the-default-repositories/192388#192388](https://askubuntu.com/questions/124017/how-do-i-restore-the-default-repositories/192388#192388)

---

### Post by deadflowr on 2017-05-26
> I am unable to find /etc/apt/sources.list:16 and /etc/apt/sources.list:53 anywhere in the file system so am unable to remove duplicates.
They're in the file /etc/apt/source.list
lines 16 and 53 are the same.
This problem is new (to us) , and not part of what you originally posted.

What i suggested worked as expected.
You no longer get this error anymore:
```
The repository 'http://cz.archive.ubuntu.com/ubuntu xenial Release' does not have a Release file.
Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
See apt-secure(8) manpage for repository creation and user configuration details.
Failed to fetch http://cz.archive.ubuntu.com/ubuntu/...amd64/Packages Cannot initiate the connection to 
cz.archive.ubuntu.com:80 (2001:1488:ffff::63). - connect (101: Network is unreachable) [IP: 2001:1488:ffff::63 80]
```
though, you also do not seem to have any affiliation with the cz.archives...

Anyhoo, your system is up-to-date, fwiw.

---

### Post by makem2 on 2017-05-26
I failed to realise that [COLOR=#000000]*/etc/apt/sources.list*[/COLOR][COLOR=#ff0000]*:16*[/COLOR]* and *[COLOR=#000000]*/etc/apt/sources.list*[/COLOR][COLOR=#ff0000]*:53 *[/COLOR]*referred to line numbers (which were not evident in the file) and failed to spot the duplication when I looked in that file previously.*

[I]Errors are no longer received and I thank you both.

Later I found:

[/I][https://askubuntu.com/questions/120621/how-to-fix-w-duplicate-sources-list-entry/184446#184446](https://askubuntu.com/questions/120621/how-to-fix-w-duplicate-sources-list-entry/184446#184446)

This gives a very full explanation.

---

