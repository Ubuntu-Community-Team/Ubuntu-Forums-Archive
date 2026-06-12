---
title: "&quot;Could not write bytes: broken pipe&quot; error on 12.04 LTS"
date: 2014-05-14
forum: General Help
---

### Post by littleboysmart on 2014-05-14
[TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: postcell"]                I have installed Kali Linux in VirtualBox on Ubuntu 12.04  LTS. Then I tried to create a common shared folder between the guest and  the host. I installed additional plugins for shared folder
sudo apt-get install virtualbox-ose-guest-utils

, it removed  some xserver package. At that time it worked properly and I shutdown it. When the next day I booted my Ubuntu it shows:

   Could not write bytes: broken pipe
  Then I tried the ways given for this problem nothing works. I tried to install xserver-xorg via

  sudo apt-get install  xserver-xorge-video-all
  It shows it could not locate xserver-xorg-all. I am able to login through terminal but I am unable to connect internet . If I have to install xserver package I have to download it from windows then I have to boot Ubuntu terminal then only I can install the package.The problem I face here if I install one package then it shows error and point other package must be installed I have tried many times the chain continues.
 For exampe if I install 

"xserver-xorg-video-evdev" it points to "xserver-xorg-org" Then it also insist me to try install with "sudo apt-install -f package name" rather "sudo apt-install  package name".
I have tried but it says the package must be installed


I want recover this problem is the installing Xserver is package only way. If I have to do that then is there any way to download as single packages including all files?

Help me to get rid of this problem?

      
[/TD]
[/TR]
[/TABLE]

---

