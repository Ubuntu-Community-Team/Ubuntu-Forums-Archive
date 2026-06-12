---
title: "[SOLVED] Lost Thunderbird email"
date: 2007-09-20
forum: General Help
---

### Post by valley96 on 2007-09-20
Hi all,

I have a problem that hopefully someone can help with. My computer crashed while I had Thunderbird open. I restarted, the disk check went through and everything seemed fine. I logged in but when I restarted Thunderbird, all of my email accounts were gone! Does any one know of a way to recover these or will I have to re-setup everything (I have 4 accounts I monitor)? I did notice during the disk check that something about email came up, but I never really paid attention because it had never been a problem before. Any help will be appreciated.

Cheers

---

### Post by swisscow on 2007-09-20
The emails are kept in a hidden folder in your home directory - enable view hidden files, you will see a folder there. I believe, and I could be wrong you could import your email from these folders into say evolution or kmail as a temporary fix - they accept the same format I think. 

It might work, and at least you may have your emails back, until you sort out the settings in Thunderbird

---

### Post by fjgaude on 2007-09-20
Thunderbird accounts are stored in your home directory as a hidden file /home/yourname/.thunderbird or it could be .mozilla-thunderbird depending on the version you are using.

In this file folder you find profiles.ini and another file called xxyyzz.default. Look into the .ini file and see what it points to as a default.

See if things match up... if they don't then try to re-name to get them to sync.

Good luck,
frank
[http://yantrayoga.typepad.com/noname/](http://yantrayoga.typepad.com/noname/)

---

### Post by Maestro23 on 2007-09-20
On my system:

> ~/.mozilla-thunderbird

Accounts are in:

> ~/.mozilla-thunderbird/bdxndx5l.default/Mail

---

### Post by NT4usB on 2007-09-20
Open Thunderbird profile manager and see what profile is launching and where your profile is pointing. You can browse to and manually point your user at the folder that contains your good profile.

---

### Post by valley96 on 2007-09-20
Thanks all. I think I got them all back. I knew what to look for, just not where...I didn't think of the "hidden files" idea even though it is the same in windows

Cheers

---

