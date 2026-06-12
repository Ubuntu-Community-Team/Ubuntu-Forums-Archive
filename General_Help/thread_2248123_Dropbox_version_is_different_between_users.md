---
title: "Dropbox version is different between users"
date: 2014-10-12
forum: General Help
---

### Post by CaptainMark on 2014-10-12
I have two users on my system, myself and my girl. When I log in, everything is A-ok, but when she logs in, she gets an error about dropbox not being up to date. I checked the preferences dialog and the version number that is being reported by her dropbox is different from the dropbox version being reported when I log in. I really cant even begin to understand this or how to diagnose the problem. She doesn't have root so cant have installed any debs, and I installed dropbox just by running the .deb from dropbox website. 

Any ideas?

---

### Post by nerdtron on 2014-10-12
> She doesn't have root so cant have installed any debs, and I installed dropbox just by running the .deb from dropbox website.

Your account dropbox is installed from .deb from Dropbox website and how is her account Dropbox installed if she doesn't have root privileges?

Anyway, why not temporary give here account sudo privileges so she can update/install newer version.

---

### Post by vasa1 on 2014-10-12
I did this: [http://ubuntuforums.org/showthread.php?t=2240094&p=13101776#post13101776](http://ubuntuforums.org/showthread.php?t=2240094&p=13101776#post13101776)

I have Dropbox 2.10.30 which updates automatically.

---

### Post by CaptainMark on 2014-10-14
@nerdtron Well I am root, so I have installed a .deb, of course it will install system-wide and the same version is run for all users who call dropbox, at least thats the plan, Dropbox is not installed in userspace,

---

### Post by CaptainMark on 2014-10-14
AAH, okay Dropbox works completely stupidly, it DOES install into userspace automatically for some reason. The files /usr/bin/dropbox is just a script that installs the binaries into ~/dropbox and ~/.dropbox-dist so I quit Dropbox daemon removed these directories and ran Dropbox from the dash, it reinstalled the Dropbox daemon and now everything is hunky dory. It strikes me as bizarre that the files in /usr/bin/dropbox do not seem able to correctly update the daemon but oh well, thats life. The binaries should really contain the daemon which uses only config files from userspace.

---

