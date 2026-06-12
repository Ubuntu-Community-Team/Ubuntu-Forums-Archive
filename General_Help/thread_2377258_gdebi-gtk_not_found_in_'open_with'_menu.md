---
title: "gdebi-gtk not found in 'open with' menu"
date: 2017-11-11
forum: General Help
---

### Post by monkeybrain20122 on 2017-11-11
As the title says, there is no option to install .deb with gdebi from 'open with' menu in Nautilus.

---

### Post by ajgreeny on 2017-11-11
Same here in my VM of a wayland session in Ubuntu 18.04.

A right click of a .deb package file shows only "Software" to open it and on searching in the "Alternative applications" option it did not even show gdebi as installed.  A search further in the "search for other" applications offers to install gdebi.

Simply to see what happens I accepted this offer to install gdebi which gave no error about already having the most recent version, but continued to install it (again?) along with about 50 or more other kde and qt packages which I will list from the logs later when I am back on my main machine.

Gdebi, however, was still not offered as a way of installing a .deb package after this second installation, so there is obviously some glitch in either the package or the procedure of installing.

---

### Post by ajgreeny on 2017-11-11
I uninstalled all those 145 kde etc etc packages that were installed along with gdebi when using the search system mentioned in post #2 which were those shown below; for some strange reason gdebi-kde was installed even though that was not asked for in the application search system that I used and that has thast long list of dependencies.
```
2017-11-11 12:04:29 install gdebi-core:all <none> 0.9.5.7+nmu1ubuntu3
2017-11-11 12:04:30 install gnome-icon-theme:all <none> 3.12.0-2
2017-11-11 12:04:32 install gdebi:all <none> 0.9.5.7+nmu1ubuntu3
2017-11-11 12:08:22 install libmng2:amd64 <none> 2.0.2-0ubuntu3
2017-11-11 12:08:22 install libqt5script5:amd64 <none> 5.9.1+dfsg-2
2017-11-11 12:08:22 install docbook-xsl:all <none> 1.79.1+dfsg-2
2017-11-11 12:08:23 install fonts-dejavu-extra:all <none> 2.37-1
2017-11-11 12:08:23 install fonts-dejavu:all <none> 2.37-1
2017-11-11 12:08:23 install breeze-icon-theme:all <none> 4:5.38.0-0ubuntu1
2017-11-11 12:08:28 install kde-runtime-data:all <none> 4:17.04.3-0ubuntu1
2017-11-11 12:08:30 install libkf5config-data:all <none> 5.38.0-0ubuntu1
2017-11-11 12:08:30 install libkf5configcore5:amd64 <none> 5.38.0-0ubuntu1
2017-11-11 12:08:30 install libqt5xml5:amd64 <none> 5.9.1+dfsg-10ubuntu2
2017-11-11 12:08:30 install libkf5configgui5:amd64 <none> 5.38.0-0ubuntu1
2017-11-11 12:08:31 install libkf5configwidgets-data:all <none> 5.38.0-0ubuntu1
2017-11-11 12:08:31 install libkf5auth-data:all <none> 5.38.0-0ubuntu1
2017-11-11 12:08:31 install libkf5coreaddons-data:all <none> 5.38.0-0ubuntu1
2017-11-11 12:08:31 install libfam0:amd64 <none> 2.7.0-17.2
2017-11-11 12:08:31 install libkf5coreaddons5:amd64 <none> 5.38.0-0ubuntu1
2017-11-11 12:08:31 install libpolkit-qt5-1-1:amd64 <none> 0.112.0-5
2017-11-11 12:08:31 install libkf5auth5:amd64 <none> 5.38.0-0ubuntu1
2017-11-11 12:08:32 install libkf5codecs-data:all <none> 5.38.0-0ubuntu1
2017-11-11 12:08:32 install libkf5codecs5:amd64 <none> 5.38.0-0ubuntu1
2017-11-11 12:08:32 install libkf5guiaddons5:amd64 <none> 5.38.0-0ubuntu2
2017-11-11 12:08:32 install libkf5i18n-data:all <none> 5.38.0-0ubuntu1
2017-11-11 12:08:32 install libkf5i18n5:amd64 <none> 5.38.0-0ubuntu1
2017-11-11 12:08:32 install libkf5widgetsaddons-data:all <none> 5.38.0-0ubuntu1
2017-11-11 12:08:33 install libkf5widgetsaddons5:amd64 <none> 5.38.0-0ubuntu1
2017-11-11 12:08:33 install libkf5configwidgets5:amd64 <none> 5.38.0-0ubuntu1
2017-11-11 12:08:33 install libkf5iconthemes-data:all <none> 5.38.0-0ubuntu1
2017-11-11 12:08:33 install libkf5archive5:amd64 <none> 5.38.0-0ubuntu1
2017-11-11 12:08:33 install libkf5itemviews-data:all <none> 5.38.0-0ubuntu1
2017-11-11 12:08:33 install libkf5itemviews5:amd64 <none> 5.38.0-0ubuntu1
2017-11-11 12:08:33 install libkf5iconthemes5:amd64 <none> 5.38.0-0ubuntu1
2017-11-11 12:08:33 install libkf5style5:amd64 <none> 5.38.0-0ubuntu2
2017-11-11 12:08:33 install kwayland-data:all <none> 4:5.38.0-0ubuntu1
2017-11-11 12:08:34 install libkf5waylandclient5:amd64 <none> 4:5.38.0-0ubuntu1
2017-11-11 12:08:34 install libkf5windowsystem-data:all <none> 5.38.0-0ubuntu1
2017-11-11 12:08:34 install libkf5windowsystem5:amd64 <none> 5.38.0-0ubuntu1
2017-11-11 12:08:34 install libqt5qml5:amd64 <none> 5.9.1-4ubuntu1
2017-11-11 12:08:34 install libqt5quick5:amd64 <none> 5.9.1-4ubuntu1
2017-11-11 12:08:34 install kde-style-breeze:amd64 <none> 4:5.10.5-0ubuntu1
2017-11-11 12:08:34 install libdlrestrictions1:amd64 <none> 0.15.28ubuntu1
2017-11-11 12:08:34 install qtcore4-l10n:all <none> 4:4.8.7+dfsg-7ubuntu1
2017-11-11 12:08:35 install libqtcore4:amd64 <none> 4:4.8.7+dfsg-7ubuntu1
2017-11-11 12:08:35 install libqt4-xml:amd64 <none> 4:4.8.7+dfsg-7ubuntu1
2017-11-11 12:08:35 install libqtdbus4:amd64 <none> 4:4.8.7+dfsg-7ubuntu1
2017-11-11 12:08:35 install qtchooser:amd64 <none> 63-g13a3d08-1
2017-11-11 12:08:35 install qdbus:amd64 <none> 4:4.8.7+dfsg-7ubuntu1
2017-11-11 12:08:35 install libqt4-dbus:amd64 <none> 4:4.8.7+dfsg-7ubuntu1
2017-11-11 12:08:35 install libqt4-network:amd64 <none> 4:4.8.7+dfsg-7ubuntu1
2017-11-11 12:08:35 install libkdecore5:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:36 install libattica0.4:amd64 <none> 0.4.2-2
2017-11-11 12:08:36 install libqt4-script:amd64 <none> 4:4.8.7+dfsg-7ubuntu1
2017-11-11 12:08:36 install libqt4-sql:amd64 <none> 4:4.8.7+dfsg-7ubuntu1
2017-11-11 12:08:36 install libqt4-xmlpatterns:amd64 <none> 4:4.8.7+dfsg-7ubuntu1
2017-11-11 12:08:36 install libqt4-declarative:amd64 <none> 4:4.8.7+dfsg-7ubuntu1
2017-11-11 12:08:36 install libqtgui4:amd64 <none> 4:4.8.7+dfsg-7ubuntu1
2017-11-11 12:08:37 install libdbusmenu-qt2:amd64 <none> 0.9.3+16.04.20160218-0ubuntu1
2017-11-11 12:08:37 install libqt4-svg:amd64 <none> 4:4.8.7+dfsg-7ubuntu1
2017-11-11 12:08:37 install libkdeui5:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:37 install kde-style-breeze-qt4:amd64 <none> 4:5.10.5-0ubuntu1
2017-11-11 12:08:37 install kate-data:all <none> 4:4.14.3-4ubuntu2
2017-11-11 12:08:38 install libkcmutils4:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:38 install libsolid4:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:38 install libavformat57:amd64 <none> 7:3.3.4-2build3
2017-11-11 12:08:38 install libstreams0v5:amd64 <none> 0.7.8-2.2
2017-11-11 12:08:38 install libstreamanalyzer0v5:amd64 <none> 0.7.8-2.2
2017-11-11 12:08:38 install libkio5:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:39 install libknewstuff3-4:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:39 install libkparts4:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:39 install libktexteditor4:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:39 install libkatepartinterfaces4:amd64 <none> 4:4.14.3-4ubuntu2
2017-11-11 12:08:39 install katepart:amd64 <none> 4:4.14.3-4ubuntu2
2017-11-11 12:08:39 install libkjsapi4:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:39 install libkjsembed4:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:39 install libkrosscore4:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:39 install kdelibs-bin:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:39 install kdelibs5-data:all <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:40 install libxml2-utils:amd64 <none> 2.9.4+dfsg1-5ubuntu1
2017-11-11 12:08:40 install kdoctools:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:41 install libutempter0:amd64 <none> 1.1.6-3
2017-11-11 12:08:41 install libkpty4:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:41 install libqt4-designer:amd64 <none> 4:4.8.7+dfsg-7ubuntu1
2017-11-11 12:08:41 install libqt4-qt3support:amd64 <none> 4:4.8.7+dfsg-7ubuntu1
2017-11-11 12:08:42 install libkde3support4:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:42 install libqt4-opengl:amd64 <none> 4:4.8.7+dfsg-7ubuntu1
2017-11-11 12:08:42 install libqtwebkit4:amd64 <none> 2.3.2-0ubuntu13
2017-11-11 12:08:43 install libkdewebkit5:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:43 install libkemoticons4:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:43 install libkfile4:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:43 install libgif7:amd64 <none> 5.1.4-1
2017-11-11 12:08:43 install libphonon4:amd64 <none> 4:4.9.0-4
2017-11-11 12:08:43 install libkhtml5:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:44 install libkntlm4:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:44 install libpolkit-qt-1-1:amd64 <none> 0.112.0-5
2017-11-11 12:08:44 install kdelibs5-plugins:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:44 install oxygen-icon-theme:all <none> 5:5.38.0-0ubuntu1
2017-11-11 12:08:50 install libkdnssd4:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:50 install libqca2:amd64 <none> 2.1.3-1ubuntu1
2017-11-11 12:08:50 install libthreadweaver4:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:51 install libplasma3:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:51 install plasma-scriptengine-javascript:amd64 <none> 4:17.04.3-0ubuntu1
2017-11-11 12:08:51 install libgpgme++2v5:amd64 <none> 4:4.14.10-1ubuntu3
2017-11-11 12:08:51 install libkactivities6:amd64 <none> 4:4.13.3-0ubuntu7
2017-11-11 12:08:51 install libkdeclarative5:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:51 install libkdesu5:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:51 install libkmediaplayer4:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:51 install libknotifyconfig4:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:51 install libkxmlrpcclient4:amd64 <none> 4:4.14.10-1ubuntu3
2017-11-11 12:08:52 install libnl-route-3-200:amd64 <none> 3.2.29-0ubuntu3
2017-11-11 12:08:52 install ntrack-module-libnl-0:amd64 <none> 016-1.3
2017-11-11 12:08:52 install libntrack0:amd64 <none> 016-1.3
2017-11-11 12:08:52 install libntrack-qt4-1:amd64 <none> 016-1.3
2017-11-11 12:08:52 install phonon-backend-gstreamer-common:amd64 <none> 4:4.9.0-1
2017-11-11 12:08:52 install phonon-backend-gstreamer:amd64 <none> 4:4.9.0-1
2017-11-11 12:08:53 install phonon:amd64 <none> 4:4.9.0-4
2017-11-11 12:08:53 install kde-runtime:amd64 <none> 4:17.04.3-0ubuntu1
2017-11-11 12:08:53 install libkidletime4:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:53 install libknewstuff2-4:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:53 install libkprintutils4:amd64 <none> 4:4.14.34-0ubuntu2
2017-11-11 12:08:53 install libqt4-help:amd64 <none> 4:4.8.7+dfsg-7ubuntu1
2017-11-11 12:08:54 install libqt4-scripttools:amd64 <none> 4:4.8.7+dfsg-7ubuntu1
2017-11-11 12:08:54 install libqt4-test:amd64 <none> 4:4.8.7+dfsg-7ubuntu1
2017-11-11 12:08:54 install libqtassistantclient4:amd64 <none> 4.6.3-7
2017-11-11 12:08:55 install python3-sip:amd64 <none> 4.18.1+dfsg-2build1
2017-11-11 12:08:55 install python3-pyqt4:amd64 <none> 4.11.4+dfsg-2build2
2017-11-11 12:08:55 install python3-pykde4:amd64 <none> 4:4.14.2-0ubuntu8
2017-11-11 12:08:56 install gdebi-kde:all <none> 0.9.5.7+nmu1ubuntu3
2017-11-11 12:08:56 install icoutils:amd64 <none> 0.32.2-1
2017-11-11 12:08:56 install libqt5waylandclient5:amd64 <none> 5.9.1-2
2017-11-11 12:08:56 install libqt5waylandcompositor5:amd64 <none> 5.9.1-2
2017-11-11 12:08:56 install qtwayland5:amd64 <none> 5.9.1-2
2017-11-11 12:08:56 install libkf5idletime5:amd64 <none> 5.38.0-0ubuntu1
2017-11-11 12:08:56 install kwayland-integration:amd64 <none> 4:5.10.5-0ubuntu1
2017-11-11 12:08:56 install libkf5config-bin:amd64 <none> 5.38.0-0ubuntu1
2017-11-11 12:08:56 install libkf5iconthemes-bin:amd64 <none> 5.38.0-0ubuntu1
2017-11-11 12:08:57 install mysql-common:all <none> 5.8+1.0.2ubuntu1
2017-11-11 12:08:57 install libmysqlclient20:amd64 <none> 5.7.19-0ubuntu1
2017-11-11 12:08:57 install libqca2-plugins:amd64 <none> 2.1.3-1ubuntu1
2017-11-11 12:08:57 install libqt4-sql-mysql:amd64 <none> 4:4.8.7+dfsg-7ubuntu1
2017-11-11 12:08:57 install qt-at-spi:amd64 <none> 0.4.0-6
2017-11-11 16:57:55 install gdebi-core:all <none> 0.9.5.7+nmu1ubuntu3
2017-11-11 16:57:56 install gnome-icon-theme:all <none> 3.12.0-2
2017-11-11 16:57:59 install gdebi:all <none> 0.9.5.7+nmu1ubuntu3

```all of which I got from running ```
grep "install " /var/log.dpkg.log
```
Ithen reinstalled gdebi with **sudo apt install gdebi** which brought with it just gdebi-core, of course, and it can be used if I open gdebi first then use the File ->Open menu to the .deb file, which then works as expected.

Just like you, however, there is no way to add gdebi as the default way to open a .deb file.  I copies the gdebi.desktop file to .local/share/applications and tried editing it to the full pathway of the executable, /usr/bin/gdebi-gtk which works fine when I use the newly edited .desktop file to launch gdebi but there is no way to use it by double clicking or right clicking a .deb package file in the file manager.

---

### Post by acheronuk on 2017-11-11
> **monkeybrain20122 said:**
> As the title says, there is no option to install .deb with gdebi from 'open with' menu in Nautilus.

There is a bug for this issue: [https://bugs.launchpad.net/ubuntu/+source/gdebi/+bug/1719746](https://bugs.launchpad.net/ubuntu/+source/gdebi/+bug/1719746)

Please comment there if you can.

---

### Post by ajgreeny on 2017-11-11
Thanks for the bug link which I have visited and added a comment.

---

### Post by monkeybrain20122 on 2017-11-11
I added an "affects me too" to the bug report.

Meanwhile, the issue is caused by a missing "%U" in gdebi.desktop's Exec line, appending it solves the problem. Thanks to mc4man for the work around.

---

### Post by ajgreeny on 2017-11-13
Just found your solution but not yet tried it. I will do so when next booted into my bionic system and assuming it does work will update the bug mentioned above with the solution.

---

### Post by ajgreeny on 2017-11-13
OK, I have now tried that solution of adding **&U** to the **Exec=gdebi-gtk** line of the **/usr/share/applications gdebi.desktop** file and it works fine; interestingly in 16.04 the Exec= line uses %f, not %U and I am not totally aware of the difference between all these %x suffixes.

@ monkeybrain20122 
It would be good to have a link to where you found the mac4man solution or workaround so that I can add that to the bug.

---

### Post by jbicha on 2017-11-13
Since this issue also affects Ubuntu 17.10, maybe it should be moved to the General Help forum.

---

### Post by vasa1 on 2017-11-13
> **jbicha said:**
> Since this issue also affects Ubuntu 17.10, maybe it should be moved to the General Help forum.
And done.

---

### Post by monkeybrain20122 on 2017-11-13
> **ajgreeny said:**
> 
@ monkeybrain20122 
It would be good to have a link to where you found the mac4man solution or workaround so that I can add that to the bug.

He pmed  me.

---

### Post by ajgreeny on 2017-11-15
As you will see in [https://ubuntuforums.org/showthread.php?t=2377524&p=13711374#post13711374](https://ubuntuforums.org/showthread.php?t=2377524&p=13711374#post13711374) I thought this problem would also affect Xubuntu 18.04 which I installed yesterday, but in fact that is not a problem in Xubuntu.

Does this mean, as it appears to, that it is the gnome DE or file manager that is the problem, not gdebi itself.

---

### Post by mc4man on 2017-11-15
For the last 5+ years or so only .desktops that have an argument (%letter) on the Exec= line would show in Gnome/Nautilus's  context menu. This was well known & most apps adjusted..

Simon Quigley is suggesting that argument interferes with gdebi working correctly. Maybe it does in the latest/greatest gnome or maybe he was mistaken. 
In any event the missing argument does not solve anything in Ubuntu & obviously creates a new issue.

---

### Post by mc4man on 2017-11-15
> **mc4man said:**
> 

Simon Quigley is suggesting that argument interferes with gdebi working correctly. Maybe it does in the latest/greatest gnome or maybe he was mistaken. 

Or maybe he wasn't using gnome/nautilus at all in which case the %letter is not needed. The commit was not verbose, no bug report(s) mentioned,  so who knows..

Not sure what gdebi brings over apt so  it's basically dead anyway.. (at least as far as gnome.

---

### Post by ajgreeny on 2017-11-15
> **mc4man said:**
> 

Not sure what gdebi brings over apt so  it's basically dead anyway.. (at least as far as gnome.
That is a very good point, and one that I tend to forget about after so many years of apt-get which was not capable of doing the same job as apt or gdebi; so thanks for the reminder.

---

