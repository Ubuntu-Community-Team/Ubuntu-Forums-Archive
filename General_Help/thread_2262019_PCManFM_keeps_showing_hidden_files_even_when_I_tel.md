---
title: "PCManFM keeps showing hidden files even when I tell it to hide them"
date: 2015-01-22
forum: General Help
---

### Post by Brent_Santin on 2015-01-22
Hi,

Whenever I go to my '/home/<username>' folder with PCManFM my hidden files are showing.  I hit CTRL-H to hide them, then uncheck "VIEW/Show Hidden" and check "Preserve this Folder's Settings" and everything looks right.  But then I navigate to another directory or subdirectory and when I return to the '/home/<username>' folder all my hidden files are showing again and in the VIEW menu "Show Hiden" has a checkmark beside it again.

PCManFM won't remember that I want the hidden files in this directory to stay hidden.

This problem happened to me about eight months ago on another Lubuntu computer.  It went away eventually after an upgrade, but now it's back on a different Lubuntu computer.

Using Lubuntu 14.04.1 LTS.

This behaviour is annoying because this is one of the most commonly accessed folders on my system.

Any help or suggestions to remedy this problem are appreciated.

Thanks.

---

### Post by mörgæs on 2015-01-22
According to the [bug report]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=744123") it's fixed in 14.10.

---

### Post by Brent_Santin on 2015-01-22
Oh, darn. I hope it gets fixed for 14.04. I'd rather not abandon the stability of an LTS release just to get a bugfix. This is a rather "in your face" bug, so do you think it will trickle back to the 14.04 release?

---

### Post by mörgæs on 2015-01-22
Unlikely. Support means that security bugs are fixed, other bugs are mainly fixed in the latest release.
There might be a PPA but I don't know. 

You could also try Thunar.

On all hardware on which I have installed 14.10 it's even more stable than 14.04.

---

### Post by engineerarun on 2015-12-22
Here's a workaround for this:
[http://tuxdiary.com/2015/12/22/fix-pcmanfm-shows-hidden-files-trusty/](http://tuxdiary.com/2015/12/22/fix-pcmanfm-shows-hidden-files-trusty/)

---

### Post by Brent_Santin on 2015-12-22
> **engineerarun said:**
> Here's a workaround for this:
[http://tuxdiary.com/2015/12/22/fix-pcmanfm-shows-hidden-files-trusty/](http://tuxdiary.com/2015/12/22/fix-pcmanfm-shows-hidden-files-trusty/)

Thanks, but which version to install from that page?

Lubuntu 14.10 is called "Utopic Unicorn" but there is no PCMAN-FM release for "Utopic Unicorn".
The closest release of PC-MAN FM on that DEB package page is for Vivid Vervet (Lubuntu/Ubuntu 15.04).

---

