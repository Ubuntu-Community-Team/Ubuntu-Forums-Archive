---
title: "Update Fails 1404 LTS"
date: 2015-01-14
forum: General Help
---

### Post by PaulInBHC on 2015-01-14
Package Operation Failed
The installation or removal of a software package failed.

I have update set to daily. Last week I had an update, ran install and it failed with the above. There were a bunch of 7kb transitional packages listed. I kept running the update every day hoping these would be removed. Today there were more updates and still fail. I went into settings and unchecked things one by one under other software and then under the updates tab trying to get it to work. Even just the important security updates fail.

Stumped

---

### Post by QIII on 2015-01-14
Hello!

That's not much to go on.

Could you please run the following in the terminal and post the result back here between code tags?

```
 sudo apt-get update 
```

```
 sudo apt-get update 
```

---

### Post by PaulInBHC on 2015-01-14
```
paul@paul-A785GE:~$ sudo apt-get update
[sudo] password for paul: 
Ign http://us.archive.ubuntu.com trusty InRelease
Ign http://security.ubuntu.com trusty-security InRelease
Hit http://us.archive.ubuntu.com trusty Release.gpg
Hit http://us.archive.ubuntu.com trusty Release
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]
Get:2 http://security.ubuntu.com trusty-security Release [62.0 kB]
Hit http://us.archive.ubuntu.com trusty/main Sources   
Hit http://us.archive.ubuntu.com trusty/restricted Sources                  
Hit http://us.archive.ubuntu.com trusty/universe Sources                    
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                  
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                  
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages            
Get:3 http://security.ubuntu.com trusty-security/restricted i386 Packages [8,846 B]
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Get:4 http://security.ubuntu.com trusty-security/main i386 Packages [185 kB]
Hit http://us.archive.ubuntu.com trusty/main Translation-en               
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en          
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Get:5 http://security.ubuntu.com trusty-security/multiverse i386 Packages [1,412 B]
Get:6 http://security.ubuntu.com trusty-security/universe i386 Packages [84.2 kB]
Hit http://us.archive.ubuntu.com trusty/universe Translation-en            
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US      
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Fetched 342 kB in 6s (50.2 kB/s)                                               
Reading package lists... Done
paul@paul-A785GE:~$ paul@paul-A785GE:~$ sudo apt-get update
[sudo] password for paul: 
Ign http://us.archive.ubuntu.com trusty InRelease
Ign http://security.ubuntu.com trusty-security InRelease
Hit http://us.archive.ubuntu.com trusty Release.gpg
Hit http://us.archive.ubuntu.com trusty Release
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]
Get:2 http://security.ubuntu.com trusty-security Release [62.0 kB]
Hit http://us.archive.ubuntu.com trusty/main Sources   
Hit http://us.archive.ubuntu.com trusty/restricted Sources                  
Hit http://us.archive.ubuntu.com trusty/universe Sources                    
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                  
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                  
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages            
Get:3 http://security.ubuntu.com trusty-security/restricted i386 Packages [8,846 B]
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Get:4 http://security.ubuntu.com trusty-security/main i386 Packages [185 kB]
Hit http://us.archive.ubuntu.com trusty/main Translation-en               
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en          
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Get:5 http://security.ubuntu.com trusty-security/multiverse i386 Packages [1,412 B]
Get:6 http://security.ubuntu.com trusty-security/universe i386 Packages [84.2 kB]
Hit http://us.archive.ubuntu.com trusty/universe Translation-en            
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US      
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Fetched 342 kB in 6s (50.2 kB/s)                                               
Reading package lists... Done
paul@paul-A785GE:~$ 
```

```
paul@paul-A785GE:~$ sudo apt-get update
Ign http://security.ubuntu.com trusty-security InRelease
Ign http://us.archive.ubuntu.com trusty InRelease
Hit http://security.ubuntu.com trusty-security Release.gpg
Hit http://us.archive.ubuntu.com trusty Release.gpg
Hit http://security.ubuntu.com trusty-security Release
Hit http://us.archive.ubuntu.com trusty Release
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty/main Sources             
Hit http://security.ubuntu.com trusty-security/main i386 Packages  
Hit http://us.archive.ubuntu.com trusty/restricted Sources         
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty/universe Sources           
Hit http://security.ubuntu.com trusty-security/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse Sources          
Hit http://security.ubuntu.com trusty-security/main Translation-en  
Hit http://us.archive.ubuntu.com trusty/main i386 Packages        
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages  
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages    
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages  
Hit http://us.archive.ubuntu.com trusty/main Translation-en
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/universe Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Reading package lists... Done                                                  
paul@paul-A785GE:~$ 


```

---

### Post by QIII on 2015-01-14
Sorry.  The second command should have been

```
sudo apt-get upgrade
```

---

### Post by PaulInBHC on 2015-01-14
```
paul@paul-A785GE:~$ sudo apt-get upgrade
[sudo] password for paul: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-generic-pae linux-headers-generic
  linux-headers-generic-pae linux-image-generic linux-image-generic-pae
The following packages will be upgraded:
  coreutils cpio firefox firefox-globalmenu firefox-locale-en
  flashplugin-installer libcgmanager0 libnss3 libnss3-1d libnss3-nssdb
  libssl1.0.0 linux-libc-dev mime-support openssl unzip xul-ext-ubufox
16 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 0 B/44.3 MB of archives.
After this operation, 2,222 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
dpkg: error: parsing file '/var/lib/dpkg/status' near line 9321 package 'apt':
 value for 'Conffiles' field has malformatted line '/etc/kernel/postinst.d/ap'
E: Sub-process /usr/bin/dpkg returned an error code (2)
paul@paul-A785GE:~$ 


```

---

### Post by QIII on 2015-01-15
Using a text editor -- *DO NOT USE sudo or gksudo!* -- open /var/lib/dpkg/status

Search for the line "Package: apt".

A dozen or so lines below that should be "Conffiles:"  The next line should begin with "/etc/kernel/postinst.d/ap".

Copy the line starting with "Conffiles:" and the next three or four lines.  Post that back.

---

### Post by PaulInBHC on 2015-01-15
```
Conffiles:
 /etc/cron.daily/apt 38f629d906ca7e292db6e426cc403f98
 /etc/kernel/postinst.d/ap\00-auto-removal e076044579e46f022b217cf3cd98998f
 /etc/apt/apt.conf.d/20changelog 8baafd95750e9c31c45512ff7bde7043
 /etc/apt/apt.conf.d/01autoremove 5bf3e7bfa3bec23d634c9f3652da1787
 /etc/logrotate.d/apt 179f2ed4f85cbaca12fa3d69c2a4a1c3
```

The \00 in this line is highlighted in red
/etc/kernel/postinst.d/ap\00-auto-removal

---

### Post by QIII on 2015-01-15
very odd.

```
/etc/kernel/postinst.d/ap\00-auto-removal e076044579e46f022b217cf3cd98998f
```

should read

```
/etc/kernel/postinst.d/apt-auto-removal e076044579e46f022b217cf3cd98998f
```

I have to get off to bed.  Hopefully, with that clue someone will be able to help you along from here.

Basically you are going to need to make a backup of that file (in case something goes wrong) and make a change.  Then you will also need to be sure that the permissions are 644.

---

### Post by PaulInBHC on 2015-01-15
Is this file something that I can delete and the system will create a new one?

---

### Post by Bashing-om on 2015-01-15
PaulInBHC; Hey; NO !

Put this in your pipe, tattoo it on eyelids, put in your wallet .. 
> 
sudo rm /var/lib/dpkg/status 
Ignore them or your computer will explode! You can open it up, look at it and edit it but you must never, ever delete it. It contains all the data dpkg requires to update and uninstall packages. If you delete it you will not be able to properly remove or upgrade the packages installed prior to it being removed and you might have problems when you try to install new packages into your system.


as advised; make a backup, make the edit, save the file; and reboot ->

[INDENT][INDENT][INDENT]see what the effect is
[/INDENT][/INDENT][/INDENT]

---

### Post by PaulInBHC on 2015-01-15
OK thanks.

---

### Post by PaulInBHC on 2015-01-15
I tried editing with gedit but it says I don't have permission. I checked properties and it says I am not the owner and cannot change the read only status.

---

### Post by QIII on 2015-01-15
OK.  Since we know what we need to do now, let's make a backup copy in case things go south:  ```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.bak
```  Then, to make the edits, you need to elevate your privileges with gksudo (the graphical version of sudo) and use gedit:   ```
gksudo gedit /var/lib/dpkg/status
```  find the spot we talked about above and make it read as I said.  Make sure you change that line and only that line.  No fat fingers, no "ooops"!  Save the file and close gedit.  Then check to see that the permissions are correct, for safety.  In the terminal  ```
cd /var/lib/dpkg
``` to change to the directory where that file is.  Then do   ```
ls -l
```  to look at the file permissions.  You may have to scroll down a bit to find the file "status".  That should show it as:  ```
rw-r--r--
```  or it may have a leading dash  ```
-rw-r--r--
```  If it doesn't look like either one of those, let us know.  Otherwise, reboot and see if you can update.

---

### Post by Bashing-om on 2015-01-15
PaulInBHC; Well .. well ..

Now we do want to make an edit - carefully !
Got to have that elevated privileges to edit that file,
Now, 14.04 is pivotal as to the means to gain that authority.

gksudo or pkexec ???
Let's look and see what we have to work with:
```

dpkg -l gksu

```

If it comes back:
> 
ii  gksu           2.0.2-6ubunt amd64        graphical frontend to su
 we are golden to use 'gksudo' !
Then one can do:
```

gksudo gedit /var/lib/dpkg/status

```
as before .. make a backup, make the prescribed edit, save the file , reboot

see the effect ->
```

sudo apt-get update
sudo apt-get upgrade

```

[INDENT][INDENT]sweat condition 3 over with ?
[/INDENT][/INDENT]

---

### Post by QIII on 2015-01-15
I want to say 14.04 still uses gksudo ... I think.  But it may not be installed by default.

(I use Kubuntu, so we're still using good ol' kdesudo.)

---

### Post by PaulInBHC on 2015-01-15
Followed the Q instructions. Rebooted normal. Firefox now shows 35. As I type this, auto updater pops up. I'll hold off on that.

```
paul@paul-A785GE:~$ sudo apt-get update
[sudo] password for paul: 
Ign http://security.ubuntu.com trusty-security InRelease
Ign http://us.archive.ubuntu.com trusty InRelease
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]
Hit http://us.archive.ubuntu.com trusty Release.gpg
Get:2 http://security.ubuntu.com trusty-security Release [62.0 kB]
Hit http://us.archive.ubuntu.com trusty Release    
Hit http://us.archive.ubuntu.com trusty/main Sources      
Hit http://us.archive.ubuntu.com trusty/restricted Sources                  
Hit http://us.archive.ubuntu.com trusty/universe Sources              
Get:3 http://security.ubuntu.com trusty-security/restricted i386 Packages [8,846 B]
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Get:4 http://security.ubuntu.com trusty-security/main i386 Packages [187 kB]
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages           
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages             
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Get:5 http://security.ubuntu.com trusty-security/multiverse i386 Packages [1,412 B]
Get:6 http://security.ubuntu.com trusty-security/universe i386 Packages [84.2 kB]
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Get:7 http://security.ubuntu.com trusty-security/main Translation-en [99.0 kB] 
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Hit http://us.archive.ubuntu.com trusty/universe Translation-en   
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Fetched 443 kB in 6s (63.7 kB/s)                                               
Reading package lists... Done
paul@paul-A785GE:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-generic-pae linux-headers-generic
  linux-headers-generic-pae linux-image-generic linux-image-generic-pae
The following packages will be upgraded:
  coreutils cpio firefox firefox-globalmenu firefox-locale-en
  flashplugin-installer gir1.2-gtk-3.0 libcgmanager0 libcurl3 libcurl3-gnutls
  libcurl3-nss libgail-3-0 libgtk-3-0 libgtk-3-bin libgtk-3-common libnss3
  libnss3-1d libnss3-nssdb libssl1.0.0 linux-libc-dev mime-support openssl
  unzip xul-ext-ubufox
24 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 2,821 kB/47.1 MB of archives.
After this operation, 2,222 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://security.ubuntu.com/ubuntu/ trusty-security/main libcurl3-gnutls i386 7.35.0-1ubuntu2.3 [166 kB]
Get:2 http://security.ubuntu.com/ubuntu/ trusty-security/main libcurl3 i386 7.35.0-1ubuntu2.3 [174 kB]
Get:3 http://security.ubuntu.com/ubuntu/ trusty-security/main libcurl3-nss i386 7.35.0-1ubuntu2.3 [177 kB]
Get:4 http://security.ubuntu.com/ubuntu/ trusty-security/main libgtk-3-common all 3.10.8-0ubuntu1.4 [167 kB]
Get:5 http://security.ubuntu.com/ubuntu/ trusty-security/main libgail-3-0 i386 3.10.8-0ubuntu1.4 [20.0 kB]
Get:6 http://security.ubuntu.com/ubuntu/ trusty-security/main libgtk-3-0 i386 3.10.8-0ubuntu1.4 [1,924 kB]
Get:7 http://security.ubuntu.com/ubuntu/ trusty-security/main gir1.2-gtk-3.0 i386 3.10.8-0ubuntu1.4 [174 kB]
Get:8 http://security.ubuntu.com/ubuntu/ trusty-security/main libgtk-3-bin i386 3.10.8-0ubuntu1.4 [18.1 kB]
Fetched 2,821 kB in 6s (440 kB/s)                                              
Preconfiguring packages ...
(Reading database ... 268099 files and directories currently installed.)
Preparing to unpack .../coreutils_8.21-1ubuntu5.1_i386.deb ...
Unpacking coreutils (8.21-1ubuntu5.1) over (8.21-1ubuntu5) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for install-info (5.2.0.dfsg.1-2) ...
Setting up coreutils (8.21-1ubuntu5.1) ...
(Reading database ... 268099 files and directories currently installed.)
Preparing to unpack .../libssl1.0.0_1.0.1f-1ubuntu2.8_i386.deb ...
Unpacking libssl1.0.0:i386 (1.0.1f-1ubuntu2.8) over (1.0.1f-1ubuntu2.7) ...
Preparing to unpack .../libcurl3-gnutls_7.35.0-1ubuntu2.3_i386.deb ...
Unpacking libcurl3-gnutls:i386 (7.35.0-1ubuntu2.3) over (7.35.0-1ubuntu2.2) ...
Preparing to unpack .../libcurl3_7.35.0-1ubuntu2.3_i386.deb ...
Unpacking libcurl3:i386 (7.35.0-1ubuntu2.3) over (7.35.0-1ubuntu2.2) ...
Preparing to unpack .../libnss3-1d_2%3a3.17.1-0ubuntu0.14.04.2_i386.deb ...
Unpacking libnss3-1d:i386 (2:3.17.1-0ubuntu0.14.04.2) over (2:3.17.1-0ubuntu0.14.04.1) ...
Preparing to unpack .../libnss3-nssdb_2%3a3.17.1-0ubuntu0.14.04.2_all.deb ...
Unpacking libnss3-nssdb (2:3.17.1-0ubuntu0.14.04.2) over (2:3.17.1-0ubuntu0.14.04.1) ...
Preparing to unpack .../libnss3_2%3a3.17.1-0ubuntu0.14.04.2_i386.deb ...
Unpacking libnss3:i386 (2:3.17.1-0ubuntu0.14.04.2) over (2:3.17.1-0ubuntu0.14.04.1) ...
Preparing to unpack .../libcurl3-nss_7.35.0-1ubuntu2.3_i386.deb ...
Unpacking libcurl3-nss:i386 (7.35.0-1ubuntu2.3) over (7.35.0-1ubuntu2.2) ...
Preparing to unpack .../libgtk-3-common_3.10.8-0ubuntu1.4_all.deb ...
Unpacking libgtk-3-common (3.10.8-0ubuntu1.4) over (3.10.8-0ubuntu1.3) ...
Preparing to unpack .../libgail-3-0_3.10.8-0ubuntu1.4_i386.deb ...
Unpacking libgail-3-0:i386 (3.10.8-0ubuntu1.4) over (3.10.8-0ubuntu1.3) ...
Preparing to unpack .../libgtk-3-0_3.10.8-0ubuntu1.4_i386.deb ...
Unpacking libgtk-3-0:i386 (3.10.8-0ubuntu1.4) over (3.10.8-0ubuntu1.3) ...
Preparing to unpack .../mime-support_3.54ubuntu1.1_all.deb ...
Unpacking mime-support (3.54ubuntu1.1) over (3.54ubuntu1) ...
Preparing to unpack .../cpio_2.11+dfsg-1ubuntu1.1_i386.deb ...
Unpacking cpio (2.11+dfsg-1ubuntu1.1) over (2.11+dfsg-1ubuntu1) ...
Preparing to unpack .../libcgmanager0_0.24-0ubuntu7.1_i386.deb ...
Unpacking libcgmanager0:i386 (0.24-0ubuntu7.1) over (0.24-0ubuntu7) ...
Preparing to unpack .../openssl_1.0.1f-1ubuntu2.8_i386.deb ...
Unpacking openssl (1.0.1f-1ubuntu2.8) over (1.0.1f-1ubuntu2.7) ...
Preparing to unpack .../firefox_35.0+build3-0ubuntu0.14.04.2_i386.deb ...
Unpacking firefox (35.0+build3-0ubuntu0.14.04.2) over (34.0+build2-0ubuntu0.14.04.1) ...
Preparing to unpack .../firefox-globalmenu_35.0+build3-0ubuntu0.14.04.2_i386.deb ...
Unpacking firefox-globalmenu (35.0+build3-0ubuntu0.14.04.2) over (34.0+build2-0ubuntu0.14.04.1) ...
Preparing to unpack .../firefox-locale-en_35.0+build3-0ubuntu0.14.04.2_i386.deb ...
Unpacking firefox-locale-en (35.0+build3-0ubuntu0.14.04.2) over (34.0+build2-0ubuntu0.14.04.1) ...
Preparing to unpack .../flashplugin-installer_11.2.202.429ubuntu0.14.04.1_i386.deb ...
Unpacking flashplugin-installer (11.2.202.429ubuntu0.14.04.1) over (11.2.202.425ubuntu0.14.04.1) ...
Preparing to unpack .../gir1.2-gtk-3.0_3.10.8-0ubuntu1.4_i386.deb ...
Unpacking gir1.2-gtk-3.0 (3.10.8-0ubuntu1.4) over (3.10.8-0ubuntu1.3) ...
Preparing to unpack .../libgtk-3-bin_3.10.8-0ubuntu1.4_i386.deb ...
Leaving 'diversion of /usr/sbin/update-icon-caches to /usr/sbin/update-icon-caches.gtk2 by libgtk-3-bin'
Leaving 'diversion of /usr/share/man/man8/update-icon-caches.8.gz to /usr/share/man/man8/update-icon-caches.gtk2.8.gz by libgtk-3-bin'
Unpacking libgtk-3-bin (3.10.8-0ubuntu1.4) over (3.10.8-0ubuntu1.3) ...
Preparing to unpack .../linux-libc-dev_3.13.0-44.73_i386.deb ...
Unpacking linux-libc-dev:i386 (3.13.0-44.73) over (3.13.0-43.72) ...
Preparing to unpack .../unzip_6.0-9ubuntu1.1_i386.deb ...
Unpacking unzip (6.0-9ubuntu1.1) over (6.0-9ubuntu1) ...
Preparing to unpack .../xul-ext-ubufox_3.0-0ubuntu0.14.04.1_all.deb ...
Unpacking xul-ext-ubufox (3.0-0ubuntu0.14.04.1) over (2.9-0ubuntu0.14.04.1) ...
Processing triggers for libglib2.0-0:i386 (2.40.2-0ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for update-notifier-common (0.154.1ubuntu1) ...
flashplugin-installer: downloading http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.429.orig.tar.gz
Installing from local file /tmp/tmp_4wOip.gz
Flash Plugin installed.
Setting up libssl1.0.0:i386 (1.0.1f-1ubuntu2.8) ...
Setting up libcurl3-gnutls:i386 (7.35.0-1ubuntu2.3) ...
Setting up libcurl3:i386 (7.35.0-1ubuntu2.3) ...
Setting up libgtk-3-common (3.10.8-0ubuntu1.4) ...
Setting up libgtk-3-0:i386 (3.10.8-0ubuntu1.4) ...
Setting up libgail-3-0:i386 (3.10.8-0ubuntu1.4) ...
Setting up mime-support (3.54ubuntu1.1) ...
Setting up cpio (2.11+dfsg-1ubuntu1.1) ...
Setting up libcgmanager0:i386 (0.24-0ubuntu7.1) ...
Setting up openssl (1.0.1f-1ubuntu2.8) ...
Setting up firefox (35.0+build3-0ubuntu0.14.04.2) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-globalmenu (35.0+build3-0ubuntu0.14.04.2) ...
Setting up firefox-locale-en (35.0+build3-0ubuntu0.14.04.2) ...
Setting up gir1.2-gtk-3.0 (3.10.8-0ubuntu1.4) ...
Setting up libgtk-3-bin (3.10.8-0ubuntu1.4) ...
Setting up linux-libc-dev:i386 (3.13.0-44.73) ...
Setting up unzip (6.0-9ubuntu1.1) ...
Setting up xul-ext-ubufox (3.0-0ubuntu0.14.04.1) ...
Setting up libnss3-nssdb (2:3.17.1-0ubuntu0.14.04.2) ...
Setting up libnss3:i386 (2:3.17.1-0ubuntu0.14.04.2) ...
Setting up libnss3-1d:i386 (2:3.17.1-0ubuntu0.14.04.2) ...
Setting up libcurl3-nss:i386 (7.35.0-1ubuntu2.3) ...
Setting up flashplugin-installer (11.2.202.429ubuntu0.14.04.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.4) ...
paul@paul-A785GE:~$ 


```

---

### Post by QIII on 2015-01-15
Looks like you're cookin' with gas again!

The updater is likely popping up because of the held kernel packages, which you should eventually install.

---

### Post by PaulInBHC on 2015-01-15
OK Thanks for all the help. I did do a forum search and google search before posting for help but neither of those came up with anything close to the help here.

---

