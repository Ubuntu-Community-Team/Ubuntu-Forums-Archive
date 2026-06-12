---
title: "Cannot update software"
date: 2012-10-27
forum: General Help
---

### Post by AndyForum on 2012-10-27
Hi,

I am using Ubuntu 12.04 and cannot run software update. 

The error message I got was : 

> W:Failed to fetch bzip2:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch [http://mirror.as29550.net/archive.ubuntu.com/dists/precise-security/restricted/source/Sources](http://mirror.as29550.net/archive.ubuntu.com/dists/precise-security/restricted/source/Sources)  404  Not Found
, W:Failed to fetch [http://mirror.as29550.net/archive.ubuntu.com/dists/precise-security/universe/source/Sources](http://mirror.as29550.net/archive.ubuntu.com/dists/precise-security/universe/source/Sources)  404  Not Found
, W:Failed to fetch [http://mirror.as29550.net/archive.ubuntu.com/dists/precise-security/multiverse/source/Sources](http://mirror.as29550.net/archive.ubuntu.com/dists/precise-security/multiverse/source/Sources)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Please help me as I have tried searching for answers on Google and tried many different commands including the ones found here :  [http://askubuntu.com/questions/131601/how-to-overcome-signature-verification-error](http://askubuntu.com/questions/131601/how-to-overcome-signature-verification-error)

But still found it unsuccessful.

Thank you.

---

### Post by jerrrys on 2012-10-27
Hi Andy, welcome to the forums  :)

My first question would be; do you really need source code?  If not, just uncheck it.

[http://en.wikipedia.org/wiki/Source_code](http://en.wikipedia.org/wiki/Source_code)

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

---

### Post by AndyForum on 2012-10-27
> **jerrrys said:**
> Hi Andy, welcome to the forums  :)

My first question would be; do you really need source code?  If not, just uncheck it.

[http://en.wikipedia.org/wiki/Source_code](http://en.wikipedia.org/wiki/Source_code)

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

Thanks Jerrys. I don't need source code and I will uncheck it. I'm new to ubuntu and appreciate it help very much.

After unchecking Source Code on software update, I have a new set of error messages as shown below :

> W:GPG error: [http://mirror.as29550.net](http://mirror.as29550.net) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>, E:Could not open file /var/lib/apt/lists/mirror.as29550.net_archive.ubuntu.com_dists_precise_restricted_binary-i386_Packages.IndexDiff - open (2: No such file or directory), E:Could not open file /var/lib/apt/lists/mirror.as29550.net_archive.ubuntu.com_dists_precise_universe_binary-i386_Packages.IndexDiff - open (2: No such file or directory)

Could anyone please help with these ? I had actually followed the steps given out here :

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)[/QUOTE]

but it didn't solve the problem.

---

### Post by jerrrys on 2012-10-27
OK, one down  :)

Error BADSIG can be fixed by:

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GPG+error+BADSIG&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GPG+error+BADSIG&as_qdr=all&sa=Google+Search&lang=en)

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

Also in terminal run:

sudo rm /var/lib/apt/lists/* -vf

sudo apt-get update

---

### Post by AndyForum on 2012-10-27
Hi,

Thanks for you help so far. I checked the links you provided and tried out some of the command executions. Still there are errors being generated.

> W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Index](http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_precise_main_i18n_Index
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-security_multiverse_binary-i386_Packages  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I have also changed the software update servers a few times to the Main Site. Still errors appear and cannot check for updates.

---

### Post by jerrrys on 2012-10-27
Try changing download server

[https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server](https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server)

Then in terminal

sudo rm -R /var/lib/apt/lists/partial/*

sudo apt-get update

---

