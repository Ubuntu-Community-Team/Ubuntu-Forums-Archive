---
title: "i cant install anything"
date: 2008-01-31
forum: General Help
---

### Post by gard195 on 2008-01-31
for a while i was able to install stuff then all of a sudden it wont let me this is what i get.

/home/allen/Desktop/Screenshot-synaptic.png

---

### Post by reckless2k2 on 2008-01-31
can you try to run the following at the terminal and then post the error or results:

```
sudo apt-get update
```

---

### Post by ~LoKe on 2008-01-31
You'll need to upload that screenshot somewhere.  Click "Manage Attachments" at the end of the reply box and add your image.

---

### Post by jan quark on 2008-01-31
just guessing can't wait to see the actual error screenshot

but try this code
```
sudo apt-get -f install
```

should fix all broken packages

---

### Post by gard195 on 2008-02-02
here is the screenshot.

---

### Post by kellemes on 2008-02-02
Please post /etc/apt/sources.list
There probably is a typo going on..

---

### Post by gard195 on 2008-02-02
> **kellemes said:**
> Please post /etc/apt/sources.list
There probably is a typo going on..


i dont know what that is.

---

### Post by kellemes on 2008-02-02
> **gard195 said:**
> i dont know what that is.


It's a file called sources.list, it's location is : /etc/apt
Browse to this location.. open this file with an editor and copy/paste the text in this thread.

---

### Post by gard195 on 2008-02-02
this is what it came up with. i dont know all the terms yet.

---

### Post by Dylock on 2008-02-02
You should be able to open in a text editor, use whatever came installed with you're system and open that file.

Edit: this can usually be accomplished by doing a right click like in windows.

or from the terminal you can output the contents of a file using the cat command
ie: cat /etc/apt/sources.list

---

### Post by kellemes on 2008-02-02
> **gard195 said:**
> this is what it came up with. i dont know all the terms yet.


No, we need to see the contents of the file itself.. since there is a typo in it.

- Open a terminal window, from the menu's Applications>>Accessories>>Terminal
- type "gksudo gedit /etc/apt/sources.list
- select all the text (Ctrl-A) -> copy the text (Ctrl-C).
- start a new post in this thread and paste the text (Ctrl-V)

preferably within [code]-tags

---

### Post by gard195 on 2008-02-03
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
“deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main”

---

### Post by aysiu on 2008-02-03
That's your problem right there: ```
&#8220;deb http://packages.dfreer.org feisty main&#8221;
``` Delete that line.
Save.
Close Gedit.
Then paste back in the terminal the command ```
sudo apt-get update
```

---

### Post by gard195 on 2008-02-03
i did that so thats it?

---

### Post by gard195 on 2008-02-03
that didnt do anything i still get the same error messages.

---

### Post by ~LoKe on 2008-02-03
> **gard195 said:**
> i did that so thats it?

Yes.  You had quotation marks in your sources.list.  The line has to start with "deb" or "deb-src" only, otherwise it must be prefixed by # (comment).

---

### Post by ~LoKe on 2008-02-03
Alright, let's try again:
```
gksu gedit /etc/apt/sources.list
```
Remove **everything** and paste this in:
> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
Save it, then...
```
sudo apt-get update
```

---

### Post by gard195 on 2008-02-03
i still get the same message.

---

### Post by aysiu on 2008-02-03
> **gard195 said:**
> i still get the same message.
Okay. Post the exact output of these two commands.

Copy and paste this command in: ```
cat /etc/apt/sources.list
``` Then copy and paste the output back here. Then copy and paste this command in ```
sudo apt-get update
``` Then copy and paste the exact output back here again.

---

### Post by gard195 on 2008-02-03
allen@allen-desktop:~$ cat /etc/apt/sources.list
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse 
allen@allen-desktop:~$

---

### Post by gard195 on 2008-02-03
allen@allen-desktop:~$ cat /etc/apt/sources.list
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse 
allen@allen-desktop:~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Sources
Fetched 4B in 1s (3B/s)  
Reading package lists... Done
allen@allen-desktop:~$

---

### Post by ~LoKe on 2008-02-03
It worked.  That's what's supposed to happen.  Now you can upgrade like usual:
```
sudo apt-get upgrade
```

---

### Post by gard195 on 2008-02-03
allen@allen-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
allen@allen-desktop:~$

---

### Post by gard195 on 2008-02-03
this is getting rediculous. why cant ubuntu just work?

---

### Post by ~LoKe on 2008-02-03
> **gard195 said:**
> this is getting rediculous. why cant ubuntu just work?

It does work.  But apparently you followed a guide and improperly added a repository.  That's a user error, my friend.  Add this line to the end of /etc/apt/sources.list
> deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) feisty non-free
Then save it, and
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by gard195 on 2008-02-03
allen@allen-desktop:~$ sudo apt-get update && sudo apt-get upgrade
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US                 
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Get:4 [http://www.virtualbox.org](http://www.virtualbox.org) feisty Release.gpg [189B]           
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release.gpg [191B]  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Translation-en_US
Ign [http://www.virtualbox.org](http://www.virtualbox.org) feisty/non-free Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Get:6 [http://www.virtualbox.org](http://www.virtualbox.org) feisty Release [701B]                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release                      
Ign [http://www.virtualbox.org](http://www.virtualbox.org) feisty Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources    
Get:7 [http://www.virtualbox.org](http://www.virtualbox.org) feisty/non-free Packages [811B]      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Sources
Fetched 1705B in 1s (1277B/s)
Reading package lists... Done
W: GPG error: [http://www.virtualbox.org](http://www.virtualbox.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 390EC3FF927CCC73
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  gnupg hal mencoder mplayer rhythmbox
The following packages will be upgraded:
  gnome-btdownload gpgv hal-device-manager lftp libhal-storage1 libhal1
  libpulse0 libwine virtualbox wine
10 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 28.8MB of archives.
After unpacking 38.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  virtualbox
Install these packages without verification [y/N]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main gpgv 1.4.6-2ubuntu3~feisty1 [146kB]
Get:2 [http://www.virtualbox.org](http://www.virtualbox.org) feisty/non-free virtualbox 1.5.4-27034_Ubuntu_feisty [16.6MB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main gnome-btdownload 0.0.28-1~feisty1 [35.8kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main hal-device-manager 0.5.9-1ubuntu2~feisty1 [403kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main lftp 3.5.11-1~feisty1 [535kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main libhal1 0.5.9-1ubuntu2~feisty1 [362kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main libhal-storage1 0.5.9-1ubuntu2~feisty1 [360kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main libpulse0 0.9.6-1ubuntu2~feisty1 [104kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe wine 0.9.41-0ubuntu2~feisty1 [10.3MB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe libwine 0.9.41-0ubuntu2~feisty1 [854B]
Fetched 28.8MB in 42s (677kB/s)                                                
Preconfiguring packages ...
(Reading database ... 
dpkg: serious warning: files list file for package `virtualbox' missing, assuming package has no files currently installed.
119951 files and directories currently installed.)
Preparing to replace virtualbox 1.5.4-27034_Ubuntu_feisty (using .../virtualbox_1.5.4-27034%5fUbuntu%5ffeisty_i386.deb) ...
Unpacking replacement virtualbox ...
Preparing to replace gpgv 1.4.6-1ubuntu2 (using .../gpgv_1.4.6-2ubuntu3~feisty1_i386.deb) ...
Unpacking replacement gpgv ...
Preparing to replace gnome-btdownload 0.0.25-1ubuntu1 (using .../gnome-btdownload_0.0.28-1~feisty1_all.deb) ...
Unpacking replacement gnome-btdownload ...
Preparing to replace hal-device-manager 0.5.8.1-4ubuntu12 (using .../hal-device-manager_0.5.9-1ubuntu2~feisty1_all.deb) ...
Unpacking replacement hal-device-manager ...
Preparing to replace lftp 3.5.6-1build1 (using .../lftp_3.5.11-1~feisty1_i386.deb) ...
Unpacking replacement lftp ...
Preparing to replace libhal1 0.5.8.1-4ubuntu12 (using .../libhal1_0.5.9-1ubuntu2~feisty1_i386.deb) ...
Unpacking replacement libhal1 ...
Preparing to replace libhal-storage1 0.5.8.1-4ubuntu12 (using .../libhal-storage1_0.5.9-1ubuntu2~feisty1_i386.deb) ...
Unpacking replacement libhal-storage1 ...
Preparing to replace libpulse0 0.9.5-5ubuntu4.2 (using .../libpulse0_0.9.6-1ubuntu2~feisty1_i386.deb) ...
Unpacking replacement libpulse0 ...
Preparing to replace wine 0.9.33-0ubuntu1 (using .../wine_0.9.41-0ubuntu2~feisty1_i386.deb) ...
Unpacking replacement wine ...
Preparing to replace libwine 0.9.33-0ubuntu1 (using .../libwine_0.9.41-0ubuntu2~feisty1_all.deb) ...
Unpacking replacement libwine ...
Setting up virtualbox (1.5.4-27034_Ubuntu_feisty) ...
 * Starting VirtualBox kernel module vboxdrv                             [ OK ] 
Starting VirtualBox host networking...done.

Setting up gpgv (1.4.6-2ubuntu3~feisty1) ...
Setting up gnome-btdownload (0.0.28-1~feisty1) ...

Setting up hal-device-manager (0.5.9-1ubuntu2~feisty1) ...

Setting up lftp (3.5.11-1~feisty1) ...

Setting up libhal1 (0.5.9-1ubuntu2~feisty1) ...

Setting up libhal-storage1 (0.5.9-1ubuntu2~feisty1) ...

Setting up libpulse0 (0.9.6-1ubuntu2~feisty1) ...

Setting up wine (0.9.41-0ubuntu2~feisty1) ...

Setting up libwine (0.9.41-0ubuntu2~feisty1) ...
allen@allen-desktop:~$

---

### Post by gard195 on 2008-02-03
so where can i find the virtualbox i just installed?

---

### Post by ~LoKe on 2008-02-03
> **gard195 said:**
> so where can i find the virtualbox i just installed?

It should be in your menu somewhere, or you should be able to type "virtualbox" from the terminal.

---

### Post by gard195 on 2008-02-03
i did a program search and it cant find virtualbox

---

