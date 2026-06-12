---
title: "Making a clone of ubuntu 18.04 system to run it on other hardware environment"
date: 2018-07-06
forum: General Help
---

### Post by jmnb on 2018-07-06
The purpose is to have two different (desktop) computers that have exactly the same ubuntu 18.04 and exactly the same applications installed. The most important applications are MediaWiki and KaLite. One desktop is connected to internet and the second one is not connected to internet. 

I followed the procedure described in [https://ubuntuforums.org/showthread.php?t=525660](https://ubuntuforums.org/showthread.php?t=525660).

First I did a standard installation on the first desktop of ubuntu 18.04, php, mysql and mediawiki. I checked if mediawiki could start and run correctly.

Using the tar command I made a tgz-file of the sub directories:[COLOR=#000000][FONT=&quot]/etc /home /opt /tmp /usr /var[/FONT][/COLOR] and excluded the tgz-file it self. I copied the tgz-file to a USB-flash.

Next I did a minimal installation of ubuntu 18.04 on the second desktop without internet connection, copied the tgz-file from a USB-flash to the home-directory. Using the tar command I extracted the files and they were copied according to the original directory structure.

After rebooting the second desktop two error messages were displayed:
"Failed to start remount root and kernel file system"
"Failed to activate swap/swapfile"

Can anybody help me to tell me what I did wrong or how I can solve this?

I made sure that both desktops have the same name, usernames and passwords, and no other operating systems are running.
[SIZE=2][COLOR=#000000] [/COLOR][/SIZE]

---

### Post by oldfred on 2018-07-06
At the minimum a new install will have different UUIDs & if gpt different GUIDs.
So you just about have to reinstall grub and update /etc/fstab with correct UUIDs.

It would be a lot better if you could, at least temporarily, connect second computer to Internet. In the update & install on first computer, you probably also changed installed kernels and other software. Or they are not in sync in various, difficult to analyze ways.

---

### Post by deadflowr on 2018-07-06
*Thread moved to **General Help***
([Desktop Environment]("https://en.wikipedia.org/wiki/Desktop_environment") means something entirely different than Desktop machine)

---

### Post by jmnb on 2018-07-06
Thank you for the quick answer - we will connect the second desktop to internet tomorrow, reinstall this one and followed by the tar-extract

---

### Post by SeijiSensei on 2018-07-06
You can use the --set-selections and --get-selections switches to dpkg to create a list of installed packages that you can feed to a new machine.  See "man dpkg" for details.

---

### Post by monkeybrain20122 on 2018-07-07
use fsarchiver, it can be done very easily. It is in the repo [http://www.fsarchiver.org/quickstart/](http://www.fsarchiver.org/quickstart/)

I don't know, that thread was from 2007, I think it is ridiculous to use tar or dd to clone systems in 2018. Some advice are given by old school people who do things the hard way just because they can.

---

