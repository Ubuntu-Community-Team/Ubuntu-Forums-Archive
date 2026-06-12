---
title: "Software Updater Problem"
date: 2018-06-16
forum: General Help
---

### Post by shane_faulkinbury2 on 2018-06-16
I'm using Ubunti 18.04 LTS and I'm having a problem with the software updater.  It has been working fine since I installed 18.04 LTS, however last night and today I get the attached screen shot error.  Can anyone help?

---

### Post by deadflowr on 2018-06-16
What does running
```
sudo apt update
```
from a terminal show?

---

### Post by shane_faulkinbury2 on 2018-06-16
deadflowr, that works fine!  What I'm trying to get going is the Software Updater pictured on the middle, right.

---

### Post by deadflowr on 2018-06-16
I asked what the terminal output showed.
I understand the issue of the software updater.
What is unclear is what the package manager is doing.
The sudo apt update command can help.
It uses the same utilities as the software updater.

---

### Post by shane_faulkinbury2 on 2018-06-17
Sorry!

```
~$ sudo apt update
[sudo] password for none: 
Get:1 http://security.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]
Hit:2 http://repository.spotify.com stable InRelease                           
Hit:3 http://us.archive.ubuntu.com/ubuntu bionic InRelease                     
Hit:4 http://ppa.launchpad.net/daniruiz/flat-remix/ubuntu bionic InRelease     
Hit:5 https://repo.skype.com/deb stable InRelease                              
Get:6 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [83.2 kB]   
Hit:7 https://deb.opera.com/opera-stable stable InRelease                      
Hit:8 http://ppa.launchpad.net/gezakovacs/ppa/ubuntu bionic InRelease          
Get:9 http://security.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [204 B]
Hit:10 http://ppa.launchpad.net/unit193/encryption/ubuntu bionic InRelease     
Hit:11 http://repo.sinew.in stable InRelease                                   
Get:12 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [2,452 B]
Hit:13 http://download.virtualbox.org/virtualbox/debian bionic InRelease       
Get:14 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
Ign:16 http://download.opensuse.org/repositories/home:/stevenpusser/xUbuntu_18.04  InRelease
Get:17 http://download.opensuse.org/repositories/home:/stevenpusser/xUbuntu_18.04  Release [1,027 B]
Get:18 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [105 kB]
Get:19 http://download.opensuse.org/repositories/home:/stevenpusser/xUbuntu_18.04  Release.gpg [481 B]
Ign:19 http://download.opensuse.org/repositories/home:/stevenpusser/xUbuntu_18.04  Release.gpg
Get:20 http://us.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 48x48 Icons [18.0 kB]
Get:21 http://us.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64 Icons [34.2 kB]
Get:22 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [120 kB]
Get:23 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 48x48 Icons [123 kB]
Get:24 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 64x64 Icons [194 kB]
Get:25 http://us.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [5,096 B]
Hit:15 https://packagecloud.io/AtomEditor/atom/any any InRelease               
Reading package lists... Done                                                  
W: GPG error: http://download.opensuse.org/repositories/home:/stevenpusser/xUbuntu_18.04  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0FAD31CA8719FCE4
E: The repository 'http://download.opensuse.org/repositories/home:/stevenpusser/xUbuntu_18.04  Release' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

---

### Post by deadflowr on 2018-06-17
It seems like there is an issue with a repos keys
Try fixing the stevenpusser repo key issue with
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0FAD31CA8719FCE4
sudo apt update
```

See if that helps clear things up.

Do you remember trying to add that repository?
Or what directions were needed to add it?
Or has this been fine for a while and only now has gone belly up?

---

### Post by shane_faulkinbury2 on 2018-06-17
That did the trick deadflowr!  Thanks a ton!!!  :smile:

---

### Post by shane_faulkinbury2 on 2018-08-05
Deadflowr, it's doing it again and this is what I get now!

```
:~$ sudo apt updateHit:1 http://download.virtualbox.org/virtualbox/debian bionic InRelease
Hit:2 http://security.ubuntu.com/ubuntu bionic-security InRelease              
Hit:3 http://us.archive.ubuntu.com/ubuntu bionic InRelease                     
Hit:4 http://ppa.launchpad.net/unit193/encryption/ubuntu bionic InRelease      
Get:5 http://repository.spotify.com stable InRelease [3,302 B]                 
Hit:6 https://deb.opera.com/opera-stable stable InRelease                      
Hit:7 https://repo.skype.com/deb stable InRelease                              
Get:8 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]   
Ign:9 http://download.opensuse.org/repositories/home:/emby/xUbuntu_Next  InRelease
Hit:10 http://repo.sinew.in stable InRelease                                   
Hit:11 http://download.opensuse.org/repositories/home:/emby/xUbuntu_Next  Release
Err:5 http://repository.spotify.com stable InRelease                           
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A87FF9DF48BF1C90
Get:12 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
Reading package lists... Done                                   
W: GPG error: http://repository.spotify.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A87FF9DF48BF1C90
E: The repository 'http://repository.spotify.com stable InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.



```

---

### Post by oldos2er on 2018-08-05
Run the command in post #6 again, using the pubkey shown in the error.

---

### Post by shane_faulkinbury2 on 2018-08-05
I did and what I posted is what I got after!

---

### Post by oldos2er on 2018-08-05
I ran ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A87FF9DF48BF1C90
``` the result was ```
Executing: /tmp/apt-key-gpghome.fKGUiws3Jf/gpg.1.sh --keyserver keyserver.ubuntu.com --recv-keys A87FF9DF48BF1C90
gpg: key A87FF9DF48BF1C90: public key "Spotify Public Repository Signing Key <tux@spotify.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1
``` Is that the output for you too?

---

### Post by shane_faulkinbury2 on 2018-08-07
Here's todays!

```
:~$ sudo apt updateHit:1 http://us.archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 http://security.ubuntu.com/ubuntu bionic-security InRelease
Get:3 http://repository.spotify.com stable InRelease [3,302 B]                 
Hit:4 http://ppa.launchpad.net/unit193/encryption/ubuntu bionic InRelease      
Ign:5 http://download.opensuse.org/repositories/home:/emby/xUbuntu_Next  InRelease
Hit:6 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease             
Hit:7 https://deb.opera.com/opera-stable stable InRelease                      
Hit:8 http://download.virtualbox.org/virtualbox/debian bionic InRelease        
Hit:9 http://repo.sinew.in stable InRelease                                    
Err:3 http://repository.spotify.com stable InRelease                           
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A87FF9DF48BF1C90
Hit:10 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease          
Hit:11 http://download.opensuse.org/repositories/home:/emby/xUbuntu_Next  Release
Hit:12 https://repo.skype.com/deb stable InRelease                             
Reading package lists... Done                       
W: GPG error: http://repository.spotify.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A87FF9DF48BF1C90
E: The repository 'http://repository.spotify.com stable InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.



```

---

### Post by shane_faulkinbury2 on 2018-08-07
```
:[COLOR=#729FCF]**~**[/COLOR]$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A87FF9DF48BF1C90[sudo] password for none: 
Executing: /tmp/apt-key-gpghome.SAoIAQ44nN/gpg.1.sh --keyserver keyserver.ubuntu.com --recv-keys A87FF9DF48BF1C90
gpg: key A87FF9DF48BF1C90: public key "Spotify Public Repository Signing Key <tux@spotify.com>" imported
gpg: Total number processed: 1 gpg:               imported: 1
```

---

### Post by shane_faulkinbury2 on 2018-08-07
Well, I don't know what happened the first time, but it's working now!  Thanks  :p

---

