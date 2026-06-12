---
title: "ubuntu msg"
date: 2018-02-03
forum: General Help
---

### Post by an3as on 2018-02-03
Hello,
I have just see this msg on my screen. what is it? 

[https://ibb.co/eU6kOm](https://ibb.co/eU6kOm)

---

### Post by coffeecat on 2018-02-03
Support, not chat. Good grief, how many more people are going to post technical help requests in a forum clearly marked not for technical support? Rhetorical question. Sigh.

*Thread moved to **General Help**.*

@an3as, did you read what the error message said? Hint - run apt-get in a terminal.

Post the output of this command:

```
sudo apt-get update
```

Please post the output between BBCode code tags - there is a link in my sig telling you how.

Oh, and by the way. When you post a URL, the forum software automatically converts it to a hyperlink, but somehow you have managed to circumvent that.

---

### Post by an3as on 2018-02-03
```
sudo apt-get update
[sudo] password for an3as: 
Hit:1 http://archive.canonical.com/ubuntu xenial InRelease
Hit:2 http://archive.ubuntu.com/ubuntu xenial InRelease            
Hit:3 http://archive.ubuntu.com/ubuntu xenial-updates InRelease                
Get:4 http://archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]     
Ign:5 http://dell.archive.canonical.com/updates xenial-dell-gamora-kbl InRelease
Ign:6 http://dell.archive.canonical.com/updates xenial-dell InRelease
Hit:7 http://dell.archive.canonical.com/updates xenial-dell-gamora-kbl Release
Hit:8 http://dell.archive.canonical.com/updates xenial-dell Release            
Get:11 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Ign:12 http://dl.google.com/linux/chrome/deb stable InRelease                  
Hit:13 http://linux.teamviewer.com/deb stable InRelease                        
Hit:14 http://ppa.launchpad.net/atareao/atareao/ubuntu xenial InRelease        
Ign:15 http://linux.dropbox.com/ubuntu wily InRelease                          
Hit:16 http://linux.teamviewer.com/deb preview InRelease                       
Get:17 http://linux.dropbox.com/ubuntu wily Release [6596 B]                   
Get:18 http://download.virtualbox.org/virtualbox/debian xenial InRelease [7883 B]
Ign:18 http://download.virtualbox.org/virtualbox/debian xenial InRelease       
Hit:20 http://dl.google.com/linux/chrome/deb stable Release
Fetched 219 kB in 1s (119 kB/s)
Reading package lists... Done
W: GPG error: http://download.virtualbox.org/virtualbox/debian xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2F683C52980AECF
W: The repository 'http://download.virtualbox.org/virtualbox/debian xenial InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

---

### Post by QIII on 2018-02-03
@an3as:

Is this related to your post about your problems installing VirtualBox?

---

### Post by an3as on 2018-02-03
probably yes

---

### Post by coffeecat on 2018-02-03
> **an3as said:**
> probably yes

Then I suggest you resolve your VirtualBox problem first. Leave this thread be until you have. Once your VirtualBox problem is solved, run "sudo apt-get update" again and see if any errors occur. The only error in your posted output is to do with VirtualBox so, hopefully, once you've re-installed VirtualBox correctly, the problem you describe in your first post here will be resolved as well.

---

### Post by an3as on 2018-02-03
now it's everything ok. thank you a lot

---

