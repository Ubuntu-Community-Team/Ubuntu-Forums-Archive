---
title: "Package broken, apt screwed!"
date: 2007-10-19
forum: General Help
---

### Post by alwbsok on 2007-10-19
I tried installing the cdemu 1.00 package on my 7.04 distribution (from a series of .deb files), but after installing cdemu-daemon, it failed. I would post the exact text, but I can't get it to reproduce it. Now, whenever I open any package manager (including dpkg), I get some variation of the following error:

"E:The package cdemu-daemon needs to be reinstalled, but I can't find an archive for it"

When I try to reinstall cdemu-daemon with the graphical package installer, I got a message saying I didn't have the permissions, or that the file was corrupted, both of which are absurd, since I got the gksu dialogue box, and the same package was (sort of) working before.

My approach so far has been to create a local repository that could hopefully allow apt to at least try to reinstall the package. I've created a packages.gz file, and I've put them both in a folder called "binary", which is in its own folder. I've also tried to add it to /etc/apt/sources.list. The truth is that I don't know much about repositories, let alone making and adding local repositories.

Is my approach valid? Do I need to do anything different to make the repository work? How do you add a local repository to /etc/apt/sources.list? Or is there a better method to fixing apt? Thank you so much in advance!

---

### Post by por100pre1 on 2007-10-19
```
sudo dpkg --remove --force-remove-reinstreq cdemu-daemon
```

---

### Post by alwbsok on 2007-10-19
Thanks a lot for replying.

I tried your suggestion and got the following:

```
Password:
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 217391 files and directories currently installed.)
Removing cdemu-daemon ...
 * Stopping CDEmu daemon                                                         * Killing daemon...                                                     [ OK ] 
 * Removing kernel module...                                             [fail] 
                                                                         [fail]
invoke-rc.d: initscript cdemu-daemon, action "stop" failed.
dpkg: error processing cdemu-daemon (--remove):
 subprocess pre-removal script returned error exit status 1
 * Starting CDEmu daemon                                                         * Inserting kernel module...                                            [fail] 
                                                                         [fail]
invoke-rc.d: initscript cdemu-daemon, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cdemu-daemon
```
Did it remove? Is this as bad as it sounds?

Edit: It didn't uninstall; I'm getting the same errors. Thanks for trying though.

---

