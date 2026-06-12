---
title: "Ubuntu no longer automatically prompts for updates"
date: 2014-10-22
forum: General Help
---

### Post by childintime on 2014-10-22
[SIZE=3][COLOR=#333333][FONT=UbuntuRegular]I am using 14.04 LTS and up until few months ago, Ubuntu would prompt me with updates daily. I recently manually updated whole system with:[/FONT][/COLOR][/SIZE]
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
[SIZE=3][COLOR=#333333][FONT=UbuntuRegular]And apparently system was horribly out of date because it took like an hour to update everything. In [options]("http://i.imgur.com/tQbSOS3.png?1") automatic updates are enabled.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]So how do I again enable automatic update prompt?[/FONT][/COLOR][/SIZE]

---

### Post by grahammechanical on 2014-10-22
Using dist-upgrade will bring in packages that are being held back. These packages are held back for a reason. It may be that the repository maintainer is waiting for other packages that also need upgrading are ready to be put in the repository so that the updating is not out of balance in some way. The apt-get dist-upgrade command will solve conflicts by removing packages. Sometimes that can break things. I have had dist-update break things.

So, it is not necessarily true that the system was horribly out of date because dist-update will always bring in a lot more stuff than update. But there is another factor to consider and that is the Phased Update process that Ubuntu now uses. An updated package may bring in regression bugs. If every user gets that package then every user gets the bug. But release updated packages to a percentage of the users and if there are no reports of problems, then release the update to another percentage of users and so on until 100% of uses get the package then the number of happy uses remains high. This could be the reason that it seems that a lot of packages were held back.

[https://wiki.ubuntu.com/ErrorTracker/PhasedUpdates](https://wiki.ubuntu.com/ErrorTracker/PhasedUpdates)

I have been using the Ubuntu 14.10 development version since the first week of it development cycle. I update every day and here we are just a few days from the official release of 14.10 and my system does not yet have the new wallpapers. Software Updater shows that they are there in the list of stuff to be downloaded. A new install will have those new 14.10 wallpapers and dist-update will bring them in for me. But it might also break something. There is a lot of other stuff being held back including a Linux kernel revision and an updated LibreOffice. This is the situation with phased updates.

Go to System Settings>Software and Updates>Updates tab and see what your settings are. Remember, checking for an update daily does not necessarily mean that there will be an update daily. This is especially true of an LTS release more than six months after its release. Great care is taken not to introduce instability in an LTS.  It is high impact bug fixes only with the LTS. So, expect boring stability with an LTS.

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

Regards.

---

### Post by childintime on 2014-10-22
> **grahammechanical said:**
> Using dist-upgrade will bring in packages that are being held back. These packages are held back for a reason. It may be that the repository maintainer is waiting for other packages that also need upgrading are ready to be put in the repository so that the updating is not out of balance in some way. The apt-get dist-upgrade command will solve conflicts by removing packages. Sometimes that can break things. I have had dist-update break things.

So, it is not necessarily true that the system was horribly out of date because dist-update will always bring in a lot more stuff than update. But there is another factor to consider and that is the Phased Update process that Ubuntu now uses. An updated package may bring in regression bugs. If every user gets that package then every user gets the bug. But release updated packages to a percentage of the users and if there are no reports of problems, then release the update to another percentage of users and so on until 100% of uses get the package then the number of happy uses remains high. This could be the reason that it seems that a lot of packages were held back.

[https://wiki.ubuntu.com/ErrorTracker/PhasedUpdates](https://wiki.ubuntu.com/ErrorTracker/PhasedUpdates)

I have been using the Ubuntu 14.10 development version since the first week of it development cycle. I update every day and here we are just a few days from the official release of 14.10 and my system does not yet have the new wallpapers. Software Updater shows that they are there in the list of stuff to be downloaded. A new install will have those new 14.10 wallpapers and dist-update will bring them in for me. But it might also break something. There is a lot of other stuff being held back including a Linux kernel revision and an updated LibreOffice. This is the situation with phased updates.

Go to System Settings>Software and Updates>Updates tab and see what your settings are. Remember, checking for an update daily does not necessarily mean that there will be an update daily. This is especially true of an LTS release more than six months after its release. Great care is taken not to introduce instability in an LTS.  It is high impact bug fixes only with the LTS. So, expect boring stability with an LTS.

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

Regards.

Thanks for this info. But since I installed 14.04 LTS, I had update prompt come almost daily asking if I want to install updates. Now in the last couple of months, I didn't have it come a single time. It never comes for some reason, and if I do 'apt-get upgrade' I can see that new updates were indeed available. And regarding Update tab in settings, as I showed in the image, they are all available: [options]("http://i.imgur.com/tQbSOS3.png?1")

Also I can launch software updater manually (just tried) and it indeed shows new updates available: [http://i.imgur.com/CjSSySk.png](http://i.imgur.com/CjSSySk.png) But I want this prompt to appear automatically like it was before.

---

