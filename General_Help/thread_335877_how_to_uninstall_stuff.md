---
title: "how to uninstall stuff"
date: 2007-01-10
forum: General Help
---

### Post by Mateo on 2007-01-10
one big criticism of linux for me is that there are too many ways to uninstall stuff.  and none of them are easy, to be honest.

If you install stuff via synaptic it's pretty much straight forward.

If you install from source, you either have to keep the source on your computer (waste of space) or redownload and config/make later (waste of time, and can often be hard to find them, especially if the project dies).

-----------

And I need help with another way.  I installed a mplayer frontend from a SH script (link below), and don't know how to uninstall it.

[http://www.xm1math.net/qxmp/download.html](http://www.xm1math.net/qxmp/download.html)

worst case scenario in windows is you can just delete the folder that contains the files.  Maybe 1 or 2 files gets put somewhere else.  But in linux they spread the files around to many different places.  so you can't just manually delete it, unless you know where all the files are.

---

### Post by rioghal on 2007-01-10
MPlayer is in the repos and would have been an easy install using either aptitude, apt-get or synaptic. Why did you install it from a script?

My advice is to always use aptitude to install things, and never install anything outside of the repos, if you're on Dapper. Aptitude keeps track of the apps you install as well as the dependencies for the apps. Example:

sudo aptitude install appname - this will install the app AND its deps.
sudo aptitude purge appname - this will uninstall the app AND its deps.

In Dapper, sudo apt-get install will install the app and its deps, but sudo apt-get remove will only uninstall the app, not its deps.. which leaves packages behind that waste space.

On Edgy, the version of apt-get that comes with Edgy has a new option for uninstalling, it's --auto-remove if I remember correctly. sudo apt-get remove --auto-remove will uninstall the app AND its deps, leaving no packages behind.

I feel it's always best to avoid installing anything outside of the repos because installing that way can make a mess of the system.
If you absolutely must have the latest and greatest, then it's up to you to manage things you install from binaries or scripts.

---

### Post by Mateo on 2007-01-10
That wasn't mplayer.  that was an mplayer frontend.  That isn't in the repos.  Not everything is in the repos.

How do you uninstall it.

---

### Post by rioghal on 2007-01-10
> **Mateo said:**
> That wasn't mplayer.  that was an mplayer frontend.  That isn't in the repos.  Not everything is in the repos.

How do you uninstall it.
If you installed is from a script, the best advice I have is open the script in a text editor and see where the script copied all the nedded files, then go to those locations and delete the files.. or see if make uninstall will work, sometimes devs will add a "make uninstall" option to the ir scripts to help uninstall apps.

---

### Post by Mateo on 2007-01-10
ok thanks

---

### Post by rioghal on 2007-01-11
By the way, if you install MPlayer from the repos, it comes with a frontend - gmplayer - and there are lots of skins for it (sudo aptitude install mplayer-skins).

---

### Post by bodhi.zazen on 2007-01-11
Take a look at checkinstall:

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

[http://www.howtoforge.com/howto_linux_debian_deb_checkinstall](http://www.howtoforge.com/howto_linux_debian_deb_checkinstall)

Checkinstall does not always work, but if it does life is good 8)

---

### Post by Mateo on 2007-01-11
> **rioghal said:**
> By the way, if you install MPlayer from the repos, it comes with a frontend - gmplayer - and there are lots of skins for it (sudo aptitude install mplayer-skins).

I hate the gmplayer frontend because A) it crashes on me all the time and B) I hate programs that take up more than 1 window.

---

