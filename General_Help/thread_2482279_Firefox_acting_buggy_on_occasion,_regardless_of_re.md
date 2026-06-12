---
title: "Firefox acting buggy on occasion, regardless of reinstallations..."
date: 2022-12-26
forum: General Help
---

### Post by jonfisher on 2022-12-26
Firefox acting buggy on occasion, regardless of reinstallations...

I've purged and completely uninstalled it several times, but it keeps acting buggy.   Mostly,  after some use, it will not respond to me clicking in the url window or won't switch tabs when I attempt to....

Anyone else experience Firefox acting buggy ?

---

### Post by ajgreeny on 2022-12-27
What hardware do you use and which version of firefox?
Is Firefox a snap version, the default in 22.04 or installed as a deb package as it was in previous versions?

---

### Post by jonfisher on 2022-12-30
The only 2 ways I generally install is the Unbuntu Software center and the Synaptic package installer...
From this screen shot, it does not appear that I installed it with Synaptic....
Quick question though - don't Ubuntu Software ctr. and Synaptic both install Snap versions/packages?

attached screenshot

Addendum:  From a previous post I made, asking about this, someone typed that "Software Centre can give you both the deb and snap version"   So I suppose that Synaptic always installs "snap packages" & Ubuntu Software center installs either a snap or debian version & it doesn't always make it apparent which you are getting when you do an install (?)

---

### Post by ajgreeny on 2022-12-30
You have installed, actually you probably already had the snap version of firefox, now the default in Ubuntu, which I don't use so can not help you with any problems that relate specifically to the snap itself.

Some users are very happy with snaps, including that for firefox, but on my older hardware it is just too slow, particularly the first start in a session, so I have removed all the snap infrastructure and use firefox directly from the .tar.gz archive downloaded directly from [https://www.mozilla.org/en-GB/firefox/new/](https://www.mozilla.org/en-GB/firefox/new/) which I extract to /opt, then run firefox by creating a launcher (firefox.deslktop file) for the executable firefox file in that archive.

If you prefer to keep the default snap version I will have to leave other users to help you further.

---

### Post by deadflowr on 2022-12-30
You can try moving or removing the firefox user configuration folder(s) at snap/firefox or .mozilla/firefox. Both folders are in your home folder, so no need to use sudo to remove or move them.
Purging packages never remove the configuration files and settings from user folders, so removing those folders will start it as clean as possible. 

The folder(s) will generate anew after you launch firefox. This means it'll be empty so any bookmarks or history or extensions et al you have will be gone.
Which is why you might try moving them first (ie, simply rename them to something like snap/firefox.old or .mozilla.firefox.old)
Moving allows you to restore them whereas removing deletes them and theys ain't never coming back unless you do due diligence and have functional backups.

> Quick question though - don't Ubuntu Software ctr. and Synaptic both install Snap versions/packages?

You already have the answer in your other thread: [https://ubuntuforums.org/showthread.php?t=2482153&p=14123923#post14123923]("https://ubuntuforums.org/showthread.php?t=2482153&p=14123923#post14123923")

---

