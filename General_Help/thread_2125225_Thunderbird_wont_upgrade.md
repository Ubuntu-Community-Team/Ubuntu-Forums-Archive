---
title: "Thunderbird wont upgrade"
date: 2013-03-13
forum: General Help
---

### Post by Kilarin on 2013-03-13
I use Xubuntu 4.8 under Ubuntu 12.04.2 
I was trying to do something with filters in Thunderbird this morning, and realized my thunderbird version was 3.1.  WAY behind.  
Under Thunderbird/Help I've got an "Apply Downloaded Update Now" option.   So I clicked it, it told me 3.1.5 was downloaded and ready to install, and gave me options to restart now or later.  I clicked restart now, and thunderbird restarted, but still as version 3.1, and still with the same "apply downloaded update now" option.  I've repeated that several times, same result.

Of course, the newest version 17, so I thought I would just install from the command line:
```
$ sudo apt-get update
$ sudo apt-get install thunderbird 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  thunderbird-globalmenu thunderbird-locale-en
Suggested packages:
  thunderbird-gnome-support latex-xft-fonts
The following packages will be upgraded:
  thunderbird thunderbird-globalmenu thunderbird-locale-en
3 upgraded, 0 newly installed, 0 to remove and 81 not upgraded.
Need to get 23.4 MB of archives.
After this operation, 21.5 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird-globalmenu i386 17.0.4+build1-0ubuntu0.12.04.1 [49.9 kB]
Get:2 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird-locale-en i386 1:17.0.4+build1-0ubuntu0.12.04.1 [340 kB]
Get:3 http://security.ubuntu.com/ubuntu/ precise-security/main thunderbird i386 17.0.4+build1-0ubuntu0.12.04.1 [23.0 MB]
Fetched 23.4 MB in 1min 47s (217 kB/s)                                                                                                         
(Reading database ... 580874 files and directories currently installed.)
Preparing to replace thunderbird-globalmenu 17.0.2+build1-0ubuntu0.12.04.1 (using .../thunderbird-globalmenu_17.0.4+build1-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement thunderbird-globalmenu ...
Preparing to replace thunderbird-locale-en 1:17.0.2+build1-0ubuntu0.12.04.1 (using .../thunderbird-locale-en_1%3a17.0.4+build1-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement thunderbird-locale-en ...
Preparing to replace thunderbird 17.0.2+build1-0ubuntu0.12.04.1 (using .../thunderbird_17.0.4+build1-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement thunderbird ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Setting up thunderbird (17.0.4+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-globalmenu (17.0.4+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-locale-en (1:17.0.4+build1-0ubuntu0.12.04.1) ...
$ 
```

There are no errors, everything looks good.  So I start thunderbird and it comes up as version 3.1, with the same "Apply Downloaded Update Now" option to got to 3.1.5

I must be missing something obvious here.  Can anybody tell me what I'm doing wrong?

Thanks in advance!

---

### Post by Kilarin on 2013-03-13
Ok, never mind.  I got it fixed.
I followed the instructions from here: [http://forums.mozillazine.org/viewtopic.php?f=39&t=2018075](http://forums.mozillazine.org/viewtopic.php?f=39&t=2018075)
and installed from the ubuntuzilla repository.  Now I'm on thunderbird 17!

---

