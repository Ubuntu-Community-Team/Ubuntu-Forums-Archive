---
title: "upgrading to Kubuntu from ubuntu"
date: 2005-10-16
forum: General Help
---

### Post by jrbishop79 on 2005-10-16
I read somewhere that an easy way to upgrade to a newer version of Debian was to edit your sources.list to the newer version's repositories and the do an 'apt-get dist-upgrade'. Can i do this and upgrade my ubuntu hoary hedgehog to Kubuntu Breezy?

---

### Post by sylvester_0 on 2005-10-16
Yes. do an apt-get update, dist-upgrade, then install kubunt-desktop. I started out with hoary a while ago on this machine and the acceleration was working fine. I then moved to breezy (while still alpha/beta) and the 3d broke. Now my machine is upgraded to the final release version and it's still broken. I've read all the guides on this site over and over and can't get it to work (and I'm no newbie). I plan on doing a reinstall, but other than that, everything is gravy.

---

### Post by mlomker on 2005-10-16
Unless you have a lot of time invested into customizing your machine then I'd recommend [backing up]("http://www.ubuntuforums.org/showpost.php?p=361622&postcount=4") your /home directory and doing a clean installation.

---

### Post by jrbishop79 on 2005-10-16
well my /home is on it's own partition anyway.. I did that a long time ago when I started distro hopping..

can you point me to the repositories? I want to throw caution to the wind and try it.....

---

### Post by mlomker on 2005-10-16
> well my /home is on it's own partition anyway

That makes life *so* much easier.  I'd recommend a backup copy of your /etc (I copied mine into /home).  If you want to get fancy you could [consider this.]("http://ubuntuforums.org/showthread.php?t=74211")

---

### Post by jrbishop79 on 2005-10-16
well I copy some of the more important individual files from /etc to my home directory, i.e. my spamassassin config, but that's usually about it.. most progs nowadays wind up with .whatever directories in the home directory anyways....

---

