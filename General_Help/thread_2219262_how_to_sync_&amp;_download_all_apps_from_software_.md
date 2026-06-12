---
title: "how to sync &amp; download all apps from software center after upgrading"
date: 2014-04-23
forum: General Help
---

### Post by AbhimanyuAryan on 2014-04-23
I am currently using ubuntu 14.04 final beta 32-bit.I want to re-installing ubuntu 14.04 final ISO 64-bit 

Is their a way so my software center automatically download all the apps(sync) once i do a fresh installation?

I have installed too many apps in this OS(currently). However, I don't wish to re-download all the apps manually again

Also, if this thing is not their could someone consider this as an idea in upcoming versions of ubuntu(this might help lot people):D

Loosing everything might be one of the reason people don't wanna upgrade & try newer stuff :o

---

### Post by oldfred on 2014-04-23
You have 32 bit apps and have to install the 64 bit versions.

You can export a list of installed apps to make it easy to reinstall.
Back up all of /home. If you have manually reconfigured any system settings back those up from /etc.

       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

If you have added ppas you have to separately readd those.

---

### Post by AbhimanyuAryan on 2014-04-23
I noticed the command has listed all the apps. Including the one which were installed by default. Can i grab the list of only those apps which i installed manually. Also how to backup ppa's? 

These are for x86(32 bit). Would restoring install x64 version apps or 32-bit one's(CONFUSED)?](*,)

---

### Post by oldfred on 2014-04-23
If you look at the text file output it is just a list. Then the reinstall installs the correct versions for your install even if an upgrade to a newer version. In some cases a newer version may not offer that app. And you may want to houseclean list like remove old kernels or apps you do not want.

It only reinstalls apps that are missing so having all the others does not really matter.

There may not be correct versions of your ppa, so you should manually add them. Often the biggest issue of upgrades are missing ppas and then the errors that creates on an upgrade.

 But do not just import all sources as that can lead to issues of versions:
[http://askubuntu.com/questions/2038/backup-software-sources](http://askubuntu.com/questions/2038/backup-software-sources)
sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, the tip will only reinstall Ubuntu files,

---

### Post by trag on 2014-04-26
This is the solution to your problem just click the link   [http://ubuntuhandbook.org/?s=aptik](http://ubuntuhandbook.org/?s=aptik)
good luck
trag

---

