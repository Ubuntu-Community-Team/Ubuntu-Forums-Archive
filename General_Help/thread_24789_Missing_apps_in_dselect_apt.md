---
title: "Missing apps in dselect/ apt"
date: 2005-04-08
forum: General Help
---

### Post by chris_andrew on 2005-04-08
Hi, all.

I've just discovered Ubuntu, and have installed Warty.  Having been a long term user of Debian, I am used to a huge selection of packages.

I wanted to download Hoary (5.04), and prefer to download a torrent.  Unfortunately, I was unable to find my usual torrent software in the APT repository.

I looked at the /etc/apt/sources.list and realised that I could uncomment two lines, in order to get UNIVERSAL (I think) packages.  I did this, still no torrent software.

Can anybody tell me how I can find this kind of software.

Thanks, 

Chris.

BTW  Ubuntu looks really really promising.

---

### Post by p!=f on 2005-04-08
Just a little correction: it's universe :)
There's the gnome-btdownload package but I prefer Azureus (java based) which is not present in the repositories but quite easy to install. Java can be installed as described ie. here or look for HOWTO section and Wiki:
[http://ubuntuforums.org/showthread.php?t=18180](http://ubuntuforums.org/showthread.php?t=18180)

---

### Post by lao_V on 2005-04-08
If you can't find it UNIVERSE then add MULTIVERSE as well!

---

### Post by chris_andrew on 2005-04-08
Chaps,

I have added multiverse, too.  Done an update, and searched on the gnome-btdownload package, still no luck.  Apt/ dseleect is usually so straight forward.  Have I missed something?

Thanks,

Chris.

---

### Post by chris_andrew on 2005-04-08
Oops,

Just looked for the packages I originally wanted, and found them (bittorrent and gtk-gnutella).  Forgive my oversight.

Thanks,

Chris.

---

### Post by p!=f on 2005-04-08
```

[~] > wajig policy gnome-btdownload
gnome-btdownload:
  Installed: (none)
  Candidate: 0.0.18-1ubuntu4
  Version table:
     0.0.18-1ubuntu4 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages

```
As you can see gnome-btdownload is in the section main. If you install ubuntu-desktop, gnome-btdownload should be installed too.

---

