---
title: "flashplugin-nonfree error[Solved]"
date: 2007-12-07
forum: General Help
---

### Post by Jungle-Cat on 2007-12-07
Hey all,
When I try and install flashplugin-nonfree from the repos using apt-get, I get the following error:
```
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.
```
Does this simply mean the repos are out of date for the versions of flash players that adobe have up?

Thanks

---

### Post by Sef on 2007-12-07
1) How are you installing flash?  Through Add/Remove, Synaptic, the terminal, or other?

2) Which Ubuntu are you using?

---

### Post by Jungle-Cat on 2007-12-07
1) Terminal:
sudo apt-get install flashplugin-nonfree

2) Ubuntu 7.10 Gutsy Gibbon

---

### Post by subSkipper on 2007-12-07
I have this exact same problem and get the same error message. I've tried
[LIST=1]
[*]Installing flash through Firefox
[*]Installing flash through Synaptic
[*]Installing through the Terminal
[/LIST]

All of the above generate the below error message:

```
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.
```

---

### Post by PmDematagoda on 2007-12-07
Flash is installed by downloading it from the Adobe website, it could be a problem on their end, may be if you waited for sometime the problem may be automatically fixed.

As the issue is the MD5 sum, this is the most likely problem.

---

### Post by daradib on 2007-12-08
This is a very recent bug, caused by Adobe's update of Flash 9.0 update 3 (9.0.115.0) codename "Moviestar" on December 4th.

[http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html](http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html)

This causes Ubuntu to not install the flash plugin, detecting a change in the flash plugin installer file (via MD5 checksums). See [bug 173890]("http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890"). This bug has been fixed in the next release of Ubuntu (Hardy 8.04) and it should soon come as an update to Ubuntu 7.10.

If you want an immediate fix, do the following.

Using Synaptic Package Manager, remove the package flashplugin-nonfree.

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): sudo apt-get remove flashplugin-nonfree

Then just download this package (32-bit only) and install it (it is identical to the current package in the next release of Ubuntu, Hardy 8.04): [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

If you have 64-bit Ubuntu, you currently need to build a binary package from this source package: [http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)

---

### Post by Jungle-Cat on 2007-12-08
Thanks mate; worked great.

---

### Post by daradib on 2007-12-09
> **Jungle-Cat said:**
> Thanks mate; worked great.

Cheers. That's what I call Ubuntu.

---

### Post by daradib on 2007-12-10
For more information on this bug, see [http://ubuntuforums.org/showthread.php?p=3929669](http://ubuntuforums.org/showthread.php?p=3929669)

---

