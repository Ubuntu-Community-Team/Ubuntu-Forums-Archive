---
title: "Plugin installs but NO flash"
date: 2007-12-08
forum: General Help
---

### Post by leegold on 2007-12-08
Xbuntu 7.10

Tried Adobe Flash and Gnash plugings loaded via Synaptic Manager on both FF and Opera. The plugin installs but NO flash.

Usually the browser "sees" the plugin and everythings OK - the plugin is installed but the browser does not "see" it.

Help appreciated. Thnaks, leegold

---

### Post by ajgreeny on 2007-12-08
In the address bar of FF type **about:plugins** and see if the flash plugin is listed.  If not come back and we'll try to help.

---

### Post by Joeb454 on 2007-12-08
I had this problem as well. Open a terminal and run ```
sudo apt-get remove flashplugin-nonfree
```

Then:
1) Open Firefox / Opera whichever you want to install it in.
2) Go to [youtube]("http://www.youtube.com")
3) Try to play any video, and then click the link that says "get flash player"
4) This takes you to the adobe site, which gives instructions on how to install from the tar.bz2 file

---

### Post by daradib on 2007-12-08
The above instructions will not help you in *ubuntu 7.10.

This is a very recent bug, caused by Adobe's update of Flash 9.0 update 3 (9.0.115.0) codename "Moviestar" on December 4th.

[http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html](http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html)

This causes Ubuntu to not install the flash plugin, detecting a change in the flash plugin installer file (via MD5 checksums). See [bug 173890]("http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890"). This bug has been fixed in the next release of Ubuntu (Hardy 8.04) and it should soon come as an update to Ubuntu 7.10.

If you want an immediate fix, do the following.

Using Synaptic Package Manager, remove the package flashplugin-nonfree. For more information on how to do this, see the Ubuntu documentation here: [https://help.ubuntu.com/7.10/add-applications/C/advanced.html#synaptic](https://help.ubuntu.com/7.10/add-applications/C/advanced.html#synaptic)

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): sudo apt-get remove flashplugin-nonfree

Then just download this package (32-bit only) and install it (it is identical to the current package in the next release of Ubuntu, Hardy 8.04): [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

If you have 64-bit Ubuntu, you currently need to build a binary package from this source package: [http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)

---

### Post by daradib on 2007-12-10
For more information on this bug, see [http://ubuntuforums.org/showthread.php?p=3929669](http://ubuntuforums.org/showthread.php?p=3929669)

---

### Post by imaca on 2007-12-15
If you want an immediate fix, do the following.

Using Synaptic Package Manager, remove the package flashplugin-nonfree. For more information on how to do this, see the Ubuntu documentation here: [https://help.ubuntu.com/7.10/add-applications/C/advanced.html#synaptic](https://help.ubuntu.com/7.10/add-applications/C/advanced.html#synaptic)

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): sudo apt-get remove flashplugin-nonfree

Then just download this package (32-bit only) and install it (it is identical to the current package in the next release of Ubuntu, Hardy 8.04): [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)
]

This does not fix the problem for me, and I have seen other comments to the same effect

---

### Post by daradib on 2007-12-15
> **imaca said:**
> If you want an immediate fix, do the following.

Using Synaptic Package Manager, remove the package flashplugin-nonfree. For more information on how to do this, see the Ubuntu documentation here: [https://help.ubuntu.com/7.10/add-applications/C/advanced.html#synaptic](https://help.ubuntu.com/7.10/add-applications/C/advanced.html#synaptic)

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): sudo apt-get remove flashplugin-nonfree

Then just download this package (32-bit only) and install it (it is identical to the current package in the next release of Ubuntu, Hardy 8.04): [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)
]

This does not fix the problem for me, and I have seen other comments to the same effect

Could you please read the thread again. (I updated the thread 2 days ago). If you still have problems with the package in the proposed repository (after removing the current package you have installed), please add a comment on [Launchpad Bug# 173890]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890").

---

