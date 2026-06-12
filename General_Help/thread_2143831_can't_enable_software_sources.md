---
title: "can't enable software sources"
date: 2013-05-10
forum: General Help
---

### Post by jjjjswait on 2013-05-10
hello,
today I made a persistent usb installation of xubuntu 12.04.  after successfully installing a few applications my internet connection died mid-download (installing wine).  now I am not able to install anything.  synaptic only shows my installed packages, software center displays all available packages but gives no option to install and terminal apt-get displays ' Unable to locate package '.
I assumed that the software sources options had somehow been changed, so I went into the 'software sources' menu, and all options were un-selected.  I selected those that I wanted, clicked 'close', and still no sources.  upon opening 'software sources' again, all options have reverted to unselected.  the same thing happens each time I try.
any ideas?  I'd hate to have to re-make this usb drive (no access to windows machine and bad luck with 'startup disk creator').  ps: I've had to make quite a few persistent usb drives and some variation of the not-able-to-install-applications-anymore problem has been endemic in every distribution I've used (except puppy).
thanks in advance -- any insight into this problem would be appreciated.

---

### Post by 25tom on 2013-05-10
Here are a few ideas:

1) Has your USB drive run out of space? If it's smaller than about 8GB, I'd expect it to run out of space rather quickly.
2) Since the problem seems unrelated to the actual distro you're using, it may be a problem with the USB drive.
3) Did you check the .iso file you put on the USB for corruptions? See here for instructions on that: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

It looks to me, unfortunately, that, unless someone else knows of a solution, or one of the above mentioned issues is present and solvable, that you'll need to reinstall with something to get any further...

Good luck finding a solution :)

---

