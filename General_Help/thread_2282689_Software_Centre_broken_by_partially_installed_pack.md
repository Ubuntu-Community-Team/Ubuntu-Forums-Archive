---
title: "Software Centre broken by partially installed package"
date: 2015-06-16
forum: General Help
---

### Post by Smeerkat on 2015-06-16
Hi,

I tried to install a .deb package (xmind mind mapping software) using the Software Centre but the install failed to complete. I tried to reinstall the package but now the Software Centre will not run and reports an error. When I run apt-get to remove the partly installed package I get the following:

david@david-Dell-DV051:~$ sudo apt-get remove xmind
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package xmind needs to be reinstalled, but I can't find an archive for it.

The .deb file I downloaded still exists. Is this the archive referred to above?
If I use apt-cache to see the package status I get the following:

david@david-Dell-DV051:/usr/bin$ sudo apt-cache show xmind
Package: xmind
Status: install reinstreq half-installed
Priority: optional
Section: non-free/editors
Installed-Size: 116924
Maintainer: XMind Ltd. <dev@xmind.net>
Architecture: i386
Version: 3.5.2
Depends: default-jre (>= 1:1.5-0) | java5-runtime | java6-runtime | java7-runtime, libgtk2.0-0 (>= 2.8.0), libwebkitgtk-1.0-0, lame, libc6 (>= 2.7), libglib2.0-0 (>= 2.12.0)
Conffiles:
 /etc/XMind.ini e30b5e04b4db3b8042e189b77724fa8e

How can I get rid of the partial install and hence get the Software Centre working again? I have decided not to attempt to install this package again as there must be some dependency issues which have caused the problem in the first place, I just want to remove it and any references to it. I will then look for an alternative application!

Thanks and grateful for any advice! I am running Ubuntu 12.04.

David

---

### Post by v3.xx on 2015-06-16
> Status: install reinstreq half-installed
Have you tried:
```
sudo dpkg --configure -a
```

You could also try dpkg to remove it:
```
sudo dpkg -r xmind  #see post #3 below
```
and a cleaning after
```
sudo apt-get autoremove
```

---

### Post by slickymaster on 2015-06-16
> **Smeerkat said:**
> 
david@david-Dell-DV051:/usr/bin$ sudo apt-cache show xmind
Package: xmind
Status: install reinstreq half-installed
Priority: optional
Section: non-free/editors
Installed-Size: 116924
Maintainer: XMind Ltd. <dev@xmind.net>
Architecture: i386
Version: 3.5.2
Depends: default-jre (>= 1:1.5-0) | java5-runtime | java6-runtime | java7-runtime, libgtk2.0-0 (>= 2.8.0), libwebkitgtk-1.0-0, lame, libc6 (>= 2.7), libglib2.0-0 (>= 2.12.0)
Conffiles:
 /etc/XMind.ini e30b5e04b4db3b8042e189b77724fa8e

From man dpkg> [B]Package flags
       reinst-required
              [/B]A package marked **reinst-required** is broken and requires reinstallation. These  packages  cannot  be  removed,  unless  forced  with  option
              **--force-remove-reinstreq**.So try```
sudo dpkg --force-remove-reinstreq --remove xmind
```Use **--purge** instead of **--remove** if you want to remove the configuration files as well, since **--remove** won't remove them.

---

### Post by dino99 on 2015-06-16
the other way to get rid of the broken xmind installation is to search about it with the file manager, and then erase each found file(s)

---

### Post by Bucky Ball on 2015-06-16
Off-topic, but just a word from a mind-mapping enthusiast. XMind is good, but unless you pay, not that useful as you can't export anything. Try Freeplane. It's in the repositories. It's a derivative of Freemind. One big happy family, really! :)

Hope you get your XMind issue fixed so you can get on with mind mapping in Ubuntu.  

(PS: View Your Mind (VYM) is basic but also good, particularly for quick 'on the fly' mapping, and also in the repos. The others have a steeper learning curve and will take a bit of time to get across.)

Just thought I'd throw that in. Carry on, as you were ... :)

---

### Post by Smeerkat on 2015-06-16
Thanks for that suggestion. Definitely going to ditch XMind and will give Freeplane a try. First time I have used mind mapping software but have looked at Freemind and thought it was good.

Regards,

David

---

### Post by bapoumba on 2015-06-16
+1 to Freeplane, been using it for a while now.

Side not from post #4, I'd not do that. Always better to use a package manager or dpkg to add/remove packages.

---

### Post by Smeerkat on 2015-06-16
Thanks for your suggestions. I gave them a try but it seems that the broken, partly installed package is in too much of a mess to remove without re-installing.

david@david-Dell-DV051:~$ sudo dpkg -r xmind
dpkg: error processing xmind (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 xmind

---

### Post by Smeerkat on 2015-06-16
Thanks Slickymaster.

Tried forcing a remove of the re-install request, as you suggested. Seems that xmind is well and truly messed up and refusing to budge. I have a seeming catch 22 situation: can't remove unless I re-install, can't reinstall as I don't have a working software centre!

david@david-Dell-DV051:~$ sudo dpkg --force-remove-reinstreq --remove xmind
[sudo] password for david: 
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 881292 files and directories currently installed.)
Removing xmind ...
dpkg (subprocess): unable to execute installed post-removal script (/var/lib/dpkg/info/xmind.postrm): No such file or directory
dpkg: error processing xmind (--remove):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for shared-mime-info ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 xmind

---

### Post by bapoumba on 2015-06-16
Please try with --remove before the reinstreq :
```
sudo dpkg --remove --force-remove-reinstreq xmind
```

If it does not work, please see here, post #6 :
[http://ubuntuforums.org/showthread.php?t=1608698](http://ubuntuforums.org/showthread.php?t=1608698)

---

### Post by slickymaster on 2015-06-17
> **bapoumba said:**
> Please try with --remove before the reinstreq :
```
sudo dpkg --remove --force-remove-reinstreq xmind
```

If it does not work, please see here, post #6 :
[http://ubuntuforums.org/showthread.php?t=1608698](http://ubuntuforums.org/showthread.php?t=1608698)
+1

---

### Post by Smeerkat on 2015-06-17
> **bapoumba said:**
> Please try with --remove before the reinstreq :
```
sudo dpkg --remove --force-remove-reinstreq xmind
```

If it does not work, please see here, post #6 :
[http://ubuntuforums.org/showthread.php?t=1608698](http://ubuntuforums.org/showthread.php?t=1608698)

Tried this, with the following result:

david@david-Dell-DV051:~$ sudo dpkg --remove --force-remove-reinstreq xmind
[sudo] password for david: 
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 878529 files and directories currently installed.)
Removing xmind ...
dpkg (subprocess): unable to execute installed post-removal script (/var/lib/dpkg/info/xmind.postrm): No such file or directory
dpkg: error processing xmind (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 xmind

When I look at the xmind.postrm file, there does not seem to be much in it:

david@david-Dell-DV051:~$ cat /var/lib/dpkg/info/xmind.postrm
#!/bin/sh

# Ensures that the script's execution is aborted when any subcommand fails.
# [http://www.debian.org/doc/debian-policy/ch-files.html#s-scripts](http://www.debian.org/doc/debian-policy/ch-files.html#s-scripts)
set -e

# Update application mime database
update-mime-database /usr/share/mime/

I will try the manual removal technique suggested in the link posted above - thanks for this and for all the other help and suggestions everyone has sent. I am certainly learning a lot about how complicated package management is :)

David

---

### Post by Smeerkat on 2015-06-17
At the risk of prolonging this thread, I have now tried a manual removal of the offending package. Deleted the postrm file from /var/dpkg/info, then:

david@david-Dell-DV051:/var/lib/dpkg/info$ sudo apt-get remove --purge xmind
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package xmind needs to be reinstalled, but I can't find an archive for it.
david@david-Dell-DV051:/var/lib/dpkg/info$

I'm thinking now that my only method left is to search through the system for all files referring in any way to xmind and delete them. The main problem I have is that the Software Centre application that I rely on for keeping my system up to date does not work and seems unlikely to as long as it thinks the xmind package is still stuck in a partial install. Does anyone know where this information is kept and if so, how I can get in and remove it?

Thanks for your patience!

David

---

### Post by v3.xx on 2015-06-17
```
I'm thinking now that my only method left is to search through the  system for all files referring in any way to xmind and delete them.
```
You can go ahead and manually remove the files, nothing else is working att.  Just not a recommended way to go.

I would open up your file manager with gksudo, then go to your file system and do a search for xmind. And remove.

But others may want to try something else.

---

### Post by Smeerkat on 2015-06-17
> **v3.xx said:**
> ```
I'm thinking now that my only method left is to search through the  system for all files referring in any way to xmind and delete them.
```
You can go ahead and manually remove the files, nothing else is working att.  Just not a recommended way to go.

I would open up your file manager with gksudo, then go to your file system and do a search for xmind. And remove.

But others may want to try something else.

I think I've done it!!

After removing the postrm file from /var/dpkg/info, I tried once more to force the removal again with dpkg:

sudo dpkg --remove --force-remove-reinstreq xmind

and this time it seems to have succeeded. Ran apt-get update and lo and behold, the update manager started up of its own accord and downloaded 13 system updates :)

XMind is now showing as un-installed:

david@david-Dell-DV051:~$ sudo apt-cache show xmind
[sudo] password for david: 
Package: xmind
Status: deinstall ok config-files
Priority: optional
Section: non-free/editors
Installed-Size: 116924
Maintainer: XMind Ltd. <dev@xmind.net>
Architecture: i386
Version: 3.5.2
Depends: default-jre (>= 1:1.5-0) | java5-runtime | java6-runtime | java7-runtime, libgtk2.0-0 (>= 2.8.0), libwebkitgtk-1.0-0, lame, libc6 (>= 2.7), libglib2.0-0 (>= 2.12.0)
Conffiles:
 /etc/XMind.ini e30b5e04b4db3b8042e189b77724fa8e

Hopefully now everything should work OK. Will install Freeplane from the repository and try some mind mapping!

Big thanks to everyone for your help with this problem.

David

---

### Post by Bucky Ball on 2015-06-17
Well done and fantastic news! :) Once you're satisfied you've solved this issue, please see the second link in my thread. Thanks.

Be sure to post a new thread if you have any issues with Freeplane, which hopefully you won't. The only issue might be getting your head around it, but that's not too hard.

---

### Post by bapoumba on 2015-06-20
Glad to see you got it to work :)

---

