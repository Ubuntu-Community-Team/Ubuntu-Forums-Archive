---
title: "Does Thunar have an option to navigate right pane as a tree"
date: 2015-05-31
forum: General Help
---

### Post by Ralph L on 2015-05-31
I am working on switching from ubuntu 12.04 to xubuntu 14.04.  I have found that default Thunar doesn't allow tree file expansion in the right (main) pane like Nautilus does.  Is there some option in some configuration file somewhere that enables this??  Nautilus has its "Navigate folders in a tree" option to enable this.  I really like that feature.  If Thunar does not have this option, is there another file manager that you would recommend that is similar to Nautilus and Thunar, but does have this option.  Maybe PCmanFM or XFE????

Edit:  I tried to install PCmanFM from the tarball, because so many bugs were fixed in the latest version.  However, during ./configure I got the following errors:```
checking for GIO... no
configure: error: Package requirements (gio-unix-2.0 >= 2.26.0 glib-2.0 >= 2.26.0 gthread-2.0 gobject-2.0) were not met:

No package 'gio-unix-2.0' found
No package 'glib-2.0' found
No package 'gthread-2.0' found
No package 'gobject-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GIO_CFLAGS
and GIO_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
ralph@lat1:~/Documents/Downloads/libfm-1.2.3$ 

```  I couldn't find these missing dependencies in the repository using synaptic.  Does anybody know how to satisfy these dependencies so I can install and try PCmanFM??

---

### Post by Dennis N on 2015-05-31
In Thunar, you can indeed navigate through folders as a tree, but navigation is in the side pane. You need to change the mode of the side pane. From the menus: 
**View > Side Pane** and select Tree. A keyboard shortcut for Tree mode is **Ctrl+E**, and then **Ctrl+B** to return to Shortcuts (Places, Devices, Network).

PCManFM works the same way as Thunar, so you gain nothing by using it.

---

### Post by nerdtron on 2015-05-31
Xubuntu 14.04, Thunar allows the left pane to be navigated in tree mode just like Dennis N posted.

---

### Post by Dennis N on 2015-05-31
There is one file manager not mentioned which allows folder navigation in the RIGHT (main) pane,  and that is Caja from Ubuntu MATE. I don't know how well Caja might work installed in Xubuntu. It would have to come from a PPA to be used in 14.04.

---

### Post by Ralph L on 2015-06-01
Thanks to everybody for responding.  You gave me some ideas that I will pursue in the future.  Regarding my missing dependencies when I tried to install pcmanfm, I found those.  This web site gave me needed info:  [http://wiki.lxde.org/en/LXDE:PCManFM_build_and_setup_guide](http://wiki.lxde.org/en/LXDE:PCManFM_build_and_setup_guide).  However, after the installation of the downloaded tarball (libfm-1.2.3), I still could not get pcmanfm to launch.  I tried typing "pcmanfm" into Terminal, but it didn't find anything.  I don't know whether there is another tarball that needs to be installed for pcmanfm, or I just didn't know the right command to launch it.  However, based on the info provided in this thread, I may not pursue it further.  Also, I see that the authors have gone on to a more advanced file manager call SpaceFM.  I may give that a try. 
My problem with thunar not allowing folder expansion in the right pane stems from the fact that I use a small screen laptop computer and try to keep my file managers at 1/4 or 1/6 screen size. (I use Python Windows Manager to resize and manipulate windows.)  With thunar I have to keep the left pane large enough to hold the file structure, which reduces the right pane size, and hence I must scroll to see date modified, permissions, etc.  With nautilus I could keep the left screen small and the right pane big.  However, the new nautilus has been un-developed badly taking out the Computer item under Go, so the safe removal external disk shutdown is gone, as is the multi-right pane option (it does have tabs, as does thunar, that help some).  Also, the stepper arrows no longer step 1 file name, and clicking on the slide doesn't advance a screenload.  So I may install the old nautilus from ubuntu 12.04.
Thanks again.

---

### Post by mansonfan78 on 2015-06-01
PcManfm is available in the repos, you should be able to install it using Synaptic or Software Manager, any necessary dependencies would be automatically pulled in.  As far as Nautilus is concerned, just use Nemo (from Linux Mint) instead - it is based on what Nautilus used to be like (and may also be in the repos at this point).

---

### Post by Ralph L on 2015-06-02
mansonfan78:  Thank you.  I will try Nemo as soon as I get a chance.

---

### Post by dragonfly41 on 2015-06-02
Can I suggest that you also try Krusader as your twin pane file manager?
It is in Ubuntu Software Centre.

---

### Post by Bucky Ball on 2015-06-02
Hmm. PCmanFM is probably the lightest of the lot (I use it with xfce4 on a minimal install and have used it for about five years as it seems a little snappier than Thunar) and doesn't call for third-party PPAs or a heap of dependencies getting dragged in (Krusader will pull in plenty, as will anything KDE). The standard Nautilus, Thunar, PCmanFM triumvirate are all pretty similar in most ways.

Midnight Commander's another lightweight possibility, although not sure if it will do the tree. Also a double pane file manager. It is in the repos (Synaptics in Xubuntu). Throw it on and have an experiment. Easy enough to get rid of if it doesn't do the trick.

Hope you're enjoying Xubuntu. ;)

FYI: Do a search for 'mc' for Midnight Commander in Synaptics. That's the one you want to install. Whatever it needs, which isn't a lot, will be dragged in with it. Good luck.

---

### Post by Ralph L on 2015-06-04
Thanks to everybody for all the responses.  I can see that I will have to do a little more study on file browsers. I also thought of another question about file managers (Access Control Lists and Extended Attributes) that I posted here: [http://ubuntuforums.org/showthread.php?t=2281049&p=13297866#post13297866](http://ubuntuforums.org/showthread.php?t=2281049&p=13297866#post13297866) .

---

